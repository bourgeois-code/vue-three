<template>
  <div></div>
</template>

<script>
import * as THREE from 'three';

export default {
  name: 'HelloWorld',
  data() {
    return {
      renderer: null,
      scene: null,
      camera: null,
      cube: null
    }
  },
  mounted() {
    this.scene = new THREE.Scene();
    this.camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000 );
    this.renderer = new THREE.WebGLRenderer();
    this.renderer.setSize(window.innerWidth / 3, window.innerHeight / 3);
    document.body.appendChild(this.renderer.domElement);

    var geometry = new THREE.BoxGeometry( 2, 2, 2 );
    var material = new THREE.MeshBasicMaterial({ color: 0x0000ff });
    this.cube = new THREE.Mesh(geometry, material);
    this.scene.add( this.cube );
    this.camera.position.z = 5;

    this.animate();
  },
  methods: {
    animate() {
      requestAnimationFrame(this.animate);
      this.cube.rotation.x += 0.03; 
      this.cube.rotation.y += 0.03;
      this.renderer.render(this.scene, this.camera);
    }
  }
}
</script>

<style scoped lang="less">

</style>
