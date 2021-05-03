<template>
  <div class="container">
    <div class="content">
      <div class="slider-wrapper">
        To
        <div class="slider">
          <div class="slider-text1">Think💡</div>
          <div class="slider-text3">Do💻</div>
          <div class="slider-text2">Write📝</div>
          <div class="slider-text4">Think💡</div>
        </div>
      </div>
    </div>
    <div class="links">
      <b-button variant="dark">
        <NuxtLink to="/list" class="nuxtlink">Add new list</NuxtLink>
      </b-button>
    </div>
  </div>
</template>

<script>
export default {}
</script>
<style>
.container {
  margin: 0 auto;
  min-height: 25vh;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  text-align: center;
}

.nuxtlink {
  text-decoration: none;
  color: aliceblue;
}
.nuxtlink:hover {
  text-decoration: none;
  color: rgb(157, 163, 168);
}

.content {
  width: 100vw;
  height: 60vh;
  display: flex;
  align-items: center;
  justify-content: center;
}
.slider-wrapper {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;

  font-weight: 300;
  font-size: 80px;
  color: #080808;
  letter-spacing: 1px;
  display: flex;
  align-items: center;
  justify-content: center;
}
.slider {
  height: 110px;
  padding-left: 10px;
  overflow: hidden;
}
.slider div {
  color: #fff;
  height: 50px;
  margin-bottom: 50px;
  padding: 2px 15px;
  text-align: center;
  box-sizing: border-box;
}
.slider-text1 {
  animation: slide 6s linear infinite;
}
.slider .slider-text3 {
  padding-right: 100px;
}
@keyframes slide {
  0% {
    margin-top: -300px;
  }
  5% {
    margin-top: -200px;
  }
  33% {
    margin-top: -200px;
  }
  38% {
    margin-top: -100px;
  }
  66% {
    margin-top: -100px;
  }
  71% {
    margin-top: 0px;
  }
  100% {
    margin-top: 0px;
  }
}
</style>
