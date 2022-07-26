<template>
  <div class="hello">
    <div class="choose">
      <button @click="getTxt">选择文件</button>
      <div>{{data}}</div>
    </div>
  </div>
</template>
<script>
import { ref} from 'vue';

export default {
  name: 'HelloWorld',
  // props: {
  //   msg: String
  // }
  setup(){
    const data = ref("");
    const getTxt = async ()=>{
      await window.electronAPI.openFile()
      window.electronAPI.getData((event,value)=>{
        console.log(event,value)
        data.value = value
      })
    }

    return{
      data,
      getTxt,
    }
  }
}
</script>
<style scoped>

</style>
