  <template>
  <div class="container">
    <transition-group name="fade" tag="div">
      <div v-for="currentValue in [currentIndex]" v-bind:key="currentValue" class="img-container">
        <!-- NOTE: you can either use style property and bind the background image or put a div inside the image and bind the image source -->
        <img class="myImg" v-bind:src="currentImg" />
      </div>
    </transition-group>
  </div>
</template>

<script>
export default {
  name: "Slider",
  data() {
    return {
      timer: null,
      currentIndex: 0,
      images: [
        require("../assets/images/artem-bali-682651-unsplash.jpg"),
        require("../assets/images/brooke-lark-261793-unsplash.jpg"),
        require("../assets/images/erik-dungan-1079095-unsplash.jpg"),
        require("../assets/images/ivan-timov-663072-unsplash.jpg")
      ]
    };
  },
  methods: {
    next() {
      this.currentIndex += 1;
      console.log(
        this.currentIndex,
        Math.abs(this.currentIndex) % this.images.length
      );
    },
    prev() {
      this.currentIndex -= 1;
    },
    startSlide() {
      this.timer = setInterval(this.next, 4000);
    }
  },
  computed: {
    currentImg: function() {
      // Makes more sense if you run this in the console
      /**
       * Basically there are 4 images.
       * currentIndex always goes up by one, even though there are only 4      images
       * To keep the index values of the images array between 0 and 4, we take the remainders of currentIndex with the length of the array. Here is an example...
       * if currentIndex = 10, we take 10/4, which is 2 with a REMAINDER of 2. ie, 10%4 = 2, so the index value of images array when currentIndex = 10, will be 2 and the appropriate image will be rendered.
       */
      return this.images[Math.abs(this.currentIndex) % this.images.length];
    }
  },
  mounted() {
    this.startSlide();
  }
};
</script>

<style>
.container {
  width: 100%;
  height: 100%;
}
.fade-enter-active,
.fade-leave-active {
  transition: all 2s ease-in;
  overflow: hidden;
  visibility: visible;
  position: absolute;
  width: 100%;
  opacity: 1;
}
.fade-enter,
.fade-leave-to {
  visibility: hidden;
  width: 100%;
  opacity: 0;
}
.img-container {
  width: 100%;
  height: 100vh;
  background-size: cover;
  background-position: center;
}
.myImg {
  width: 100%;
  height: 100%;
}
</style>