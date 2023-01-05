<template>
  <div class="view">
    <NavBar />
    <MisTareas />
  </div>
</template>

<script>
import NavBar from './components/NavBar';
import MisTareas from './components/MisTareas';

export default {
  name: 'App',
  components: {
    NavBar,
    MisTareas
  }
}
</script>

<style>
 .view {
   background-color: pink ;
   /* background-image: url(""); */
   height: 100vh;

}

</style>
