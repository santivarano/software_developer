<template>
    <div>
        <transition-group name="fade" tag="div">
            <div v-for="i in [currentIndex]" :key="i">
                <img class="slider" :src="currentImg" />
            </div>
        </transition-group>
        <a class="prev" @click="prev" href="#">&#10094; Previous</a>
        <a class="next" @click="next" href="#">&#10095; Next</a>
    </div>
</template>
<script>
export default {
  name: "Slider",
  data() {
    return {
      images: [
        "/images/android.jpg",
        "/images/drone1.jpg",
        "/images/drone2.jpg",
        "/images/ios.jpg",
      ],
      timer: null,
      currentIndex: 0
    };
  },

    mounted: function() {
        this.startSlide();
    },

    methods: {
        startSlide: function() {
            this.timer = setInterval(this.next, 5000);
        },

        next: function() {
            this.currentIndex += 1;
        },
        prev: function() {
            this.currentIndex -= 1;
        }
    },

    computed: {
        
        currentImg: function() {
            //alert(Math.abs(this.currentIndex) % this.images.length)
            return this.images[Math.abs(this.currentIndex) % this.images.length];
        }
    }
};
</script>