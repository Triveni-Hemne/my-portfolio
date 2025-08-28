<template>
  <div
    class="cube-scene relative w-32 h-32 perspective-500 hover:cursor-grab"
    @mousedown="startDrag" 
    @mousemove="onDrag" 
    @mouseup="stopDrag"
    @mouseleave="endDrag"
    @touchstart="startDrag"
    @touchmove="onDrag"
    @touchend="endDrag"
  >
    <div
      class="cube relative w-full h-full transform-style-preserve-3d"
      :style="{ transform: `rotateX(${rotationX}deg) rotateY(${rotationY}deg)` }"
    >
      <!-- 6 Faces -->
      <div class="cube-face cube-front absolute w-full h-full bg-lime-50 flex items-center justify-center">
        <img :src="skill.icon" :alt="skill.name" :key="side" class="w-14 h-12 object-contain rounded-full" draggable="false" />
      </div>
      <div class="cube-face cube-back absolute w-full h-full bg-lime-50 flex items-center justify-center">
        <img :src="skill.icon" :alt="skill.name" :key="side" class="w-14 h-12 object-contain rounded-full" draggable="false"/>
      </div>
      <div class="cube-face cube-right absolute w-full h-full bg-lime-50 flex items-center justify-center">
        <img :src="skill.icon" :alt="skill.name" :key="side" class="w-14 h-12 object-contain rounded-full" draggable="false"/>
      </div>
      <div class="cube-face cube-left absolute w-full h-full bg-lime-50 flex items-center justify-center">
        <img :src="skill.icon" :alt="skill.name" :key="side" class="w-14 h-12 object-contain rounded-full" draggable="false"/>
      </div>
      <div class="cube-face cube-top absolute w-full h-full bg-lime-50 flex items-center justify-center">
        <img :src="skill.icon" :alt="skill.name" :key="side" class="w-14 h-12 object-contain rounded-full" draggable="false"/>
      </div>
      <div class="cube-face cube-bottom absolute w-full h-full bg-lime-50 flex items-center justify-center">
        <img :src="skill.icon" :alt="skill.name" :key="side" class="w-14 h-12 object-contain rounded-full" draggable="false"/>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Cube",
  props: {
    skill: Object
  },
  data() {
    return {
      rotationX: -20,
      rotationY: 20,
      velocityX: 0,
      velocityY: 0,
      isDragging: false,
      lastX: 0,
      lastY: 0,
      inertiaTimer: null,
      sides: ["front", "back", "right", "left", "top", "bottom"],
    };
  },
  methods: {
    startDrag(e) {
      this.isDragging = true;
      const point = e.touches ? e.touches[0] : e;
      this.lastX = point.clientX;
      this.lastY = point.clientY;
      clearInterval(this.inertiaTimer);
    },
    onDrag(e) {
      if (!this.isDragging) return;
      const point = e.touches ? e.touches[0] : e;
      const deltaX = point.clientX - this.lastX;
      const deltaY = point.clientY - this.lastY;
      this.velocityX = deltaX; // store last movement speed
      this.velocityY = deltaY;
      this.rotationY += deltaX * 0.5;
      this.rotationX -= deltaY * 0.5;
      this.lastX = point.clientX;
      this.lastY = point.clientY;
    },
    stopDrag() {
      if (!this.isDragging) return;
      this.isDragging = false;

      // Apply inertia effect
      this.inertiaTimer = setInterval(() => {
        this.rotationY += this.velocityX * 0.5;
        this.rotationX -= this.velocityY * 0.5;

        // Slow down gradually
        this.velocityX *= 0.95;
        this.velocityY *= 0.95;

        if (Math.abs(this.velocityX) < 0.1 && Math.abs(this.velocityY) < 0.1) {
          clearInterval(this.inertiaTimer);
        }
      }, 16); // ~60fps
    },
  }
};
</script>

<style scoped>
.cube-scene {
  perspective: 800px;
}
.cube {
  transform-style: preserve-3d;
  transition: transform 0.1s linear;
}
.cube-face {
  backface-visibility: hidden;
}
.cube-front  { transform: rotateY(0deg) translateZ(64px); }
.cube-back   { transform: rotateY(180deg) translateZ(64px); }
.cube-right  { transform: rotateY(90deg) translateZ(64px); }
.cube-left   { transform: rotateY(-90deg) translateZ(64px); }
.cube-top    { transform: rotateX(90deg) translateZ(64px); }
.cube-bottom { transform: rotateX(-90deg) translateZ(64px); }
.cube-scene, .cube-scene * {
  user-select: none;
  -webkit-user-drag: none;
}
</style>
