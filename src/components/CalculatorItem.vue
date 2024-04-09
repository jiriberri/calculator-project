<template>
  <div class="calculator">
   <span>hello</span>
   <span>hello</span>
   <span>hello</span>
   <span>hello</span>
   <span>hello</span>
   <span>hello</span>
   <span>hello</span>
  </div>
</template>

<script>

export default {
  
}
</script>

<style lang="scss" scoped>
  .calculator {
    grid-template-columns: repeat(4, 1fr);
    grid-auto-rows: minmax(50px, auto);
  }
</style>