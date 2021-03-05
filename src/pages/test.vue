<template>
  <div class="blocks">
    <div class="block">Block 1</div>
    <div class="block">Block 2</div>
    <div class="block">Block 3</div>
    <!-- <q-btn @click="onBtnClicked">click me</q-btn> -->
  </div>
</template>

<style>
.blocks{
  background-color: blue;
  display: flex;
  justify-content: center;
  align-items: flex-end;
}
.block{
  background-color: yellow;
  width: 30%;
  height: 100px;
  margin: 10px;
}

.block:nth-child(2) {
  order: -1;
}

.block:nth-child(1) {
  height: 200px;
}
</style>

<script>
export default {
  methods: {
    fnDrawTriange(n) {
        let starNo, spaceNo
        for (let rowIndex = 1; rowIndex <= n; rowIndex++) {
          starNo = rowIndex * 2 - 1
          spaceNo = rowIndex + n - starNo
          
          let result = []
          result = result.concat(Array(spaceNo).fill(' '), Array(starNo).fill('*'))
          console.log(result.join(''))
        }
    },
    // onBtnClicked() {
    //   var baz = this.counter()
    //   baz();
    // },
    counter() {
      var count = 0
      function countAndOutput() {
        count++
        console.log(count)
      }

      return countAndOutput
    }
  },
  mounted: function(){
    this.fnDrawTriange(3)
    var baz = this.counter()
    baz();
    baz();
    baz();
  }
}
</script>