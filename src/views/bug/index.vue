<template>
  <div class="canvas-container" ref="container">
  </div>
</template>

<script>
import testImg from '../../assets/1.png';
import * as THREE from 'three';

export default {
  name: "bug",
  components: {},
  data() {
    return {
      testImg,
      scene: null,
      camera: null,
      renderer: null,
    }
  },
  methods: {
    prepare() {
      this.scene = new THREE.Scene();
      this.camera = new THREE.PerspectiveCamera( 100, window.innerWidth / window.innerHeight, 0.1, 1000 );
      const container = this.$refs.container;
      this.renderer = new THREE.WebGLRenderer();
      this.renderer.setSize( container.clientWidth, container.clientHeight );
      this.$refs.container.appendChild( this.renderer.domElement );
      const geometry = new THREE.PlaneGeometry( 1, 1 );
      const material1 = new THREE.MeshBasicMaterial( {color: 0xffff00, side: THREE.DoubleSide} );
      const mesh = new THREE.Mesh( geometry, material1 );
      this.scene.add( mesh );
      console.log(this.scene);
      this.renderer.render(this.scene, this.camera);
    },
    drawImg() {
      const loader = new THREE.ImageLoader();
      loader.load(
          testImg,
          (image) => {
            console.log(image);
            // const texture = new THREE.CanvasTexture( image );
            // const material = new THREE.MeshBasicMaterial( { map: texture } );
            const shape = new THREE.Shape();
            const x = 0, y = 0;
            shape.moveTo( x + 5, y + 5 );
            shape.bezierCurveTo( x + 5, y + 5, x + 4, y, x, y );
            shape.bezierCurveTo( x - 6, y, x - 6, y + 7,x - 6, y + 7 );
            shape.bezierCurveTo( x - 6, y + 11, x - 3, y + 15.4, x + 5, y + 19 );
            shape.bezierCurveTo( x + 12, y + 15.4, x + 16, y + 11, x + 16, y + 7 );
            shape.bezierCurveTo( x + 16, y + 7, x + 16, y, x + 10, y );
            shape.bezierCurveTo( x + 7, y, x + 5, y + 5, x + 5, y + 5 );
            const geometry = new THREE.ShapeGeometry(shape);
            const material1 = new THREE.MeshBasicMaterial({color: 0xFF0000});
            const mesh = new THREE.Mesh( geometry, material1 );
            this.scene.add( mesh );
            this.renderer.render(this.scene, this.camera);
          }
      )
    }
  },
  mounted() {
    this.prepare();
    // this.drawImg();
  }
}
</script>

<style scoped lang="scss">

.canvas-container {
  width: 800px;
  height: 800px;
}

</style>
