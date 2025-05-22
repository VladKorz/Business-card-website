<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue';
import * as THREE from 'three';
import { OBJLoader } from 'three/examples/jsm/loaders/OBJLoader.js';
import { MTLLoader } from 'three/examples/jsm/loaders/MTLLoader.js';
import { OrbitControls } from 'three/examples/jsm/controls/OrbitControls.js';

const canvasRef = ref<HTMLCanvasElement | null>(null);
let scene: THREE.Scene;
let camera: THREE.PerspectiveCamera;
let renderer: THREE.WebGLRenderer;
let model: THREE.Group;
let controls: OrbitControls;
let frameId: number;

onMounted(() => {
  initThree();
  animate();
  window.addEventListener('resize', onWindowResize);
});

onUnmounted(() => {
  window.removeEventListener('resize', onWindowResize);
  cancelAnimationFrame(frameId);
  if (renderer) {
    renderer.dispose();
  }
});

function initThree() {
  if (!canvasRef.value) return;
  
  // Scene setup
  scene = new THREE.Scene();
  scene.background = new THREE.Color(0x0a0a0a);
  
  // Camera setup
  camera = new THREE.PerspectiveCamera(
    75,
    canvasRef.value.clientWidth / canvasRef.value.clientHeight,
    0.1,
    1000
  );
  camera.position.z = 5;
  
  // Renderer setup
  renderer = new THREE.WebGLRenderer({
    canvas: canvasRef.value,
    antialias: true,
    alpha: true
  });
  renderer.setSize(canvasRef.value.clientWidth, canvasRef.value.clientHeight);
  renderer.setPixelRatio(window.devicePixelRatio);
  
  // Add OrbitControls
  controls = new OrbitControls(camera, renderer.domElement);
  controls.enableDamping = true;
  controls.dampingFactor = 0.05;
  controls.autoRotate = true;
  controls.autoRotateSpeed = 1.0;
  
  // Lights
  const ambientLight = new THREE.AmbientLight(0xffffff, 0.5);
  scene.add(ambientLight);
  
  const directionalLight = new THREE.DirectionalLight(0xffffff, 1);
  directionalLight.position.set(5, 5, 5);
  scene.add(directionalLight);
  
  // Load 3D model
  const loader = new OBJLoader();
  const mtlLoader = new MTLLoader();

  mtlLoader.load(
    'models/3DModel_LowPoly/3DModel_LowPoly.mtl',
    (materials) => {
      materials.preload();
      loader.setMaterials(materials);
      loader.load(
        'models/3DModel_LowPoly/3DModel_LowPoly.obj',
        (object: THREE.Group) => {
          model = object;
          model.scale.set(15, 15, 15);
          model.rotation.y = 0;
          model.rotation.z = Math.PI / -2;
          model.rotation.x = 0;
          model.position.set(0, 0, 0);
          
          // Add material to the model (only if no material in .mtl)
          model.traverse((child) => {
            if (child instanceof THREE.Mesh && !child.material) {
              child.material = new THREE.MeshStandardMaterial({
                color: 0xff3c00,
                metalness: 0.3,
                roughness: 0.4,
                wireframe: true
              });
            }
          });
          
          scene.add(model);
          
          // Calculate camera position to fit the model
          const boundingBox = new THREE.Box3().setFromObject(model);
          const center = new THREE.Vector3();
          const size = new THREE.Vector3();
          boundingBox.getCenter(center);
          boundingBox.getSize(size);

          const maxDim = Math.max(size.x, size.y, size.z);
          const fov = camera.fov * (Math.PI / 180);
          let cameraZ = Math.abs(maxDim / 2 / Math.tan(fov / 2));
          
          // Add some padding
          cameraZ *= 1.2;
          
          camera.position.z = cameraZ;
          camera.position.copy(center);
          camera.position.z = cameraZ; // Reset Z after copying center
          
          // Update controls target
          controls.target.copy(center);
          controls.update();
        },
        (xhr: ProgressEvent) => {
          console.log((xhr.loaded / xhr.total * 100) + '% loaded');
        },
        (error: unknown) => {
          console.error('An error happened while loading the OBJ model:', error);
        }
      );
    },
    (xhr: ProgressEvent) => {
      console.log((xhr.loaded / xhr.total * 100) + '% loaded');
    },
    (error: unknown) => {
      console.error('An error happened while loading the MTL file:', error);
    }
  );
}

function animate() {
  frameId = requestAnimationFrame(animate);
  
  if (controls) {
    controls.update();
  }
  
  if (renderer && scene && camera) {
    renderer.render(scene, camera);
  }
}

function onWindowResize() {
  if (!canvasRef.value || !camera || !renderer) return;
  
  camera.aspect = canvasRef.value.clientWidth / canvasRef.value.clientHeight;
  camera.updateProjectionMatrix();
  renderer.setSize(canvasRef.value.clientWidth, canvasRef.value.clientHeight);
}
</script>

<template>
  <div class="three-container">
    <canvas ref="canvasRef" class="three-canvas"></canvas>
    <div class="model-info">
      <p>3D MODEL VIEWER</p>
      <p class="small">Rotate for different angles</p>
    </div>
  </div>
</template>

<style scoped>
.three-container {
  width: 100%;
  height: 100%;
  position: relative;
  overflow: hidden;
}

.three-canvas {
  width: 100%;
  height: 100%;
  display: block;
}

.model-info {
  position: absolute;
  bottom: 20px;
  right: 20px;
  background-color: rgba(10, 10, 10, 0.8);
  padding: 10px 15px;
  border-left: 3px solid var(--accent-color);
  font-size: 0.8rem;
  text-transform: uppercase;
}

.small {
  font-size: 0.7rem;
  opacity: 0.7;
  margin-top: 5px;
}
</style>