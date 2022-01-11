<template>
  <header class="header">
    <nav class="nav">
      <ul class="nav-links">
        <li class="link">
          <router-link to="/"><button class="btn btn-small btn-info btn-popup">Home</button></router-link>
        </li>
      </ul>
    </nav>
    <slot></slot>
  </header>
</template>

<script>
export default {};

</script>

<style scoped>
.header {
  width: 100%;
  height: 70px;
  background-color: #333333;
  box-sizing: border-box;
  padding: 0.5em;
  display: flex;
  justify-content: center;
  align-items: center;
}

.nav {
  width: 600px;
}
button {
  color: white;
  border: 1px solid #2D9CDB;
  border-radius: 3px;
  padding: 8px 30px;
  background-color: #2D9CDB;
  line-height: 1.15;
}
.nav-links {
  width: 100%;
  display: flex;
  justify-content: flex-start;
}

.link {
  list-style: none;
  padding: 0 2em;
}

.link a {
  color: #fff;
  text-decoration: none;
}
</style>
