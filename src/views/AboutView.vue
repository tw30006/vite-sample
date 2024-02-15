<template>
  <div class="about">
    <h1>This is an about page</h1>
    <LoadingOverlay :active="isLoading"/>
  </div>
</template>

// 加入js
<script>
export default {
  data(){
    return{
      isLoading: true,
    }
  },
  mounted(){
    const api = 'https://ec-course-api.hexschool.io/'
    this.$http.get(`${api}v2/api/sponge/products/all`)
    .then((res)=>{
      console.log(res);
      this.isLoading = false
    })
    // 5秒後關閉loading
    // setTimeout(()=>{
    //   this.isLoading = false
    // },1000);
  },
}
</script>
<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
