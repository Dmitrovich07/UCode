<template>
  <div class="title">
    <h1>Blog</h1>
  </div>
  <div class="test-header" @click="openMenu">
    <h3>Header Text Test</h3>
  </div>
  <div class="menu" :class="{ open: isOpen }">
      <ul class="menu-list">
        <li class="menu-link">link #1</li>
        <li class="menu-link">link #2</li>
        <li class="menu-link">link #3</li>
      </ul>
    </div>
  <div class="test-content"></div>
</template>

<script>
export default {
  name: 'Blog',
  data() {
    return {
      isOpen: false,
    }
  },
   methods: {
    openMenu() {
      this.isOpen = !this.isOpen;
    }
  }
}
</script>

<style lang="scss" scoped>
.title {
  width: 100%;
  display: flex;
  justify-content: center;
  h1 {
    padding: 50px 0; 
    margin: 0 auto;
  }
}
.test-header {
  position: relative;
  z-index: 2;
  min-height: 80px;
  background-color: aqua;
  display: flex;
  align-items: center;
  justify-content: center;
  h3 {
    text-align: center;
  }
}
.menu {
  position: absolute;
  z-index: 1;
  // overflow: hidden;
  top: 0;
  left: 0;
  background-color: black;
  color: #fff;
  transition: top 0.5s ease;
  &.open {
    // z-index: 1;
    top: 80px;
  }
  .menu-list {
    padding: 0 20px;
    display: flex;
    gap: 15px;
    .menu-link {
      font-size: 18px;
    }
  }
}
.test-content {
  // position: relative;
  // z-index: -2;
  width: 100%;
  min-height: 150px;
  background-color: orange;
}
</style>