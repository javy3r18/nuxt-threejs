<template>
  <div>
    <canvas class="webgl"></canvas>
  </div>
</template>

<script>
export default {
  data(){
    return{
      
    }
  },

  mounted(){
    this.initObject()
  },

  methods: {
    initObject(){
      const scene = new this.$THREE.Scene()
      const geometry = new this.$THREE.BoxGeometry(1, 1, 1)
      const material = new this.$THREE.MeshBasicMaterial({color: 'green'})
      const mesh = new this.$THREE.Mesh(geometry, material)
      scene.add(mesh)

      const sizes = {
        width: 800,
        height: 600
      };

      const camera = new this.$THREE.PerspectiveCamera(75, sizes.width / sizes.height )
      camera.position.z = 3
      camera.position.y = 1 
      scene.add(camera)

      const canvas = document.querySelector('.webgl')
      const renderer = new this.$THREE.WebGLRenderer({
        canvas: canvas
      })
      renderer.setSize(sizes.width, sizes.height)
      renderer.render(scene, camera)
    }
  }
}
</script>
