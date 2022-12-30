<template>
  <div class="hero">
    <img src="../assets/imgs/movieHero.jpg" alt="">
    <div class="text-container">
      <div class="text">
        <span class="mini-heading">Pre Netflix</span>
        <h1><span>Now</span> Streaming</h1>
        <a href="#movie-grid" class="button">View Movies</a>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'Hero'
  }
</script>

<style lang="scss" scoped>
  .hero {
    height: 350px;
    position: relative;

    &::after {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      height: 100%;
      width: 100%;
      background-color: rgba(0, 0, 0, 0.7);
    }

    img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }

    .text-container {
      z-index: 99;
      position: absolute;
      top: 0;
      margin: 0;
      width: 100%;
      height: 100%;
      display: flex;
      flex-direction: column;
      justify-content: center;

      .text {
        padding: 0 16px;
        width: 100%;
        max-width: 1400px;
        margin: 0 auto;
      }

      .mini-heading {
        font-weight: 600;
        font-size: 2rem;
        text-transform: uppercase;
        color: #c92502;
        margin-bottom: 8px;

        @media (min-width: 750px) {
          font-size: 4rem;
        }
      }

      h1 {
        color: #fff;
        font-size: 1rem;
        font-weight: 200;
        margin-bottom: 1rem;

        @media (min-width: 750px) {
          font-size: 2rem;
        }

        span {
          font-weight: 500;
        }
      }

      .button {
        font-size: 1rem;
        align-self: flex-start;
        padding: 8px 12px;

        @media (min-width: 750px) {
          padding: 10px 20px;
        }
      }
    
  }
}
</style>