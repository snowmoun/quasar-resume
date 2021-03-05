<template>
  <div>
    <div class="box1">box-sizing:border-box</div>
    <div class="box2">box-sizing: content-box;</div>
  </div>
</template>

<script>
export default {
  
}
</script>

<style scoped>
.box1 {
    border:20px solid #000;
    width:300px;
    height:150px;
    margin:20px;
    padding:10px;
    background-color:orange;
    text-align:center;

    box-sizing:border-box;
}

.box2 {
    border:20px solid #000;
    width:300px;
    height:150px;
    margin:20px;
    padding:10px;
    background-color: orange;
    text-align:center;
    
    box-sizing: content-box;
}
</style>