<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <h2>ค้นหาศูนย์</h2>
    <!-- <h2>{{lastMember}}</h2> -->

    <p>ชื่อของคุณ: {{msgHome}}</p>
    <Input v-model="msgHome" style="width: 200px" placeholder="ชื่อจริง" />
    <HelloWorld :msg="msgHome" />
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'Home',
  components: {
    HelloWorld
  },
  data() {
    return {
      msgHome:"",
      lastMember:""
    }
  },
  // methods:{
  //   received(val) {
  //     this.lastMember = val 
  //   }
  // }
}
</script>
