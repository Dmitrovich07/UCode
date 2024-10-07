<template>
<div class="title">
  <h1>Courses</h1>
  <div class="loading-blocks">
    <div class="loading-skeleton">
      <div class="loader" style="--b: 20px;--c:#000;width:80px;--n:15;--g:7deg"></div>
    </div>
    <div class="loading-skeleton">
      <div class="loader" style="--b: 20px;--c:#000;width:80px;--n:15;--g:7deg"></div>
    </div>
    <div class="loading-skeleton">
      <div class="loader" style="--b: 20px;--c:#000;width:80px;--n:15;--g:7deg"></div>
    </div>
    <div class="loading-skeleton">
      <div class="loader" style="--b: 20px;--c:#000;width:80px;--n:15;--g:7deg"></div>
    </div>
  </div>
</div>
</template>

<script>
export default {
  name: 'Courses',
  data() {
    return {

    }
  }
}
</script>

<style lang="scss" scoped>
.title {
  width: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  h1 {
    padding: 50px 0; 
    margin: 0 auto;
  }
  .loading-blocks {
    display: flex;
    justify-content: space-around;
    align-items: center;
    margin-bottom: 50px;
    .loading-skeleton {
      opacity: 0.7;
      width: 400px;
      height: 200px;
      background-color: #E4F5EB;
      border-radius: 10px;
      position: relative;
      overflow: hidden;
      border: 2px solid rgba(0, 0, 0, 0.3);
      display: flex;
      justify-content: center;
      align-items: center;
      .loader {
        --b: 10px;
        --n: 10;
        --g: 10deg;
        --c: red;
        
        width:100px;
        aspect-ratio: 1;
        border-radius: 50%;
        padding: 1px;
        background: conic-gradient(#0000,var(--c)) content-box;
        --_m:
          repeating-conic-gradient(#0000 0deg,
            #000 1deg calc(360deg/var(--n) - var(--g) - 1deg),
            #0000     calc(360deg/var(--n) - var(--g)) calc(360deg/var(--n))),
          radial-gradient(farthest-side,#0000 calc(98% - var(--b)),#000 calc(100% - var(--b)));
        -webkit-mask: var(--_m);
                mask: var(--_m);
        -webkit-mask-composite: destination-in;
                mask-composite: intersect;
        animation: load 0.4s infinite steps(var(--n));
      }
      &::before {
        content: '';
        position: absolute;
        top: 0;
        left: -150%;
        width: 150%;
        height: 100%;
        background: linear-gradient(90deg, rgba(255, 255, 255, 0) 0%, rgba(255, 255, 255, 0.7) 50%, rgba(255, 255, 255, 0) 100%);
        animation: shimmer 0.4s infinite;
      }
    }
  }
}

@keyframes shimmer {
  0% {
    left: -150%;
  }
  100% {
    left: 100%;
  }
}

@keyframes load {to{transform: rotate(1turn)}}
</style>