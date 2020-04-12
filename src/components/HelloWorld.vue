<template>
  <div class="hello">
    <!-- <h1>{{ msg }}</h1> -->
    <!-- work1 -->
      <!-- <h1>your name is:{{message}}</h1>
      <input v-model="message" placeholder="nick name">
      <button @click="submit">click</button>
      <button v-on:click="greet()">alert</button>
      <button v-on:click="reverseMessage">reverse</button>
      <h1 v-if="isShow">Hello {{message}}!</h1>
      <br>
      <hr> -->

    <!-- work2 -->
    <p>จังหวัด :{{selected}}</p>
    <AutoComplete
      v-model="selected"
      icon="ios-search"
      :data="provinces"
      placeholder="input here"
      style="width:200px"
    >
    </AutoComplete>
    <!-- <button @click="submit">submit</button> -->
    
    <!-- <button @click="$emit('lastMem', rederName('พระ',lastMem))">select</button> -->

    <br>
    <br>
    <Row v-if="isShow" style="padding:20px">
      <i-col v-for="(el, i) in selectedP" :key="i" span="8" style="padding:20px">
        <Card :bordered="false" style="text-align: left;">
          <p slot="title">{{i+1}}. {{el.addressName}}</p>
          <p>หัวหน้าศูนย์: {{rederName("พระ",el.holderName)}}</p>
          <p>Tel: {{el.telephone}}</p>
          <p>จังหวัด: {{el.addressLv2}}</p>
          <br>
          <Button ghost type="info" @click="clickedSendId(el.id)">เลือก</Button>
        </Card>
      </i-col>
    </Row>
  </div>
</template>

<script>
import Vue from 'vue'
import { AutoComplete } from 'view-design';
Vue.component('AutoComplete', AutoComplete);
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
   data() {
      return {
        isShow: true,
        selected: "",
      }
    },
    methods: {
      clickedSelected (selected) {
        let zeroSelected =  selected

        this.$store.dispatch('setLastMemBySelected', { input: this.msg,  selected: zeroSelected })
        this.$router.push('/result')
      },
      clickedSendId (id) {
        this.$router.push({ path: `/result/${id}`, query: { name: this.msg } })
      },
      // reverseMessage: function () {
        //   return  this.message = this.message.split('').reverse().join('')
        // },
        // greet: function () {
        //   return alert('Hello ' + this.message + '!')
        // },
      rederName(prefix,input){
        if(this.msg){
          return `${prefix}${this.msg} ${input.split(" ").slice(1).join(' ')}`
        }else{
          return input
        }
      },
      submit(){
        // this.isShow = !this.isShow 
        // this.$store.dispatch('setProvinceBySelected', this.selected)
        if(this.selected){
          // this.$store.dispatch('setLastMemBySelected', {input: this.msg,  selected: this.lastMem})
          this.$router.push("/result") // change localhost:8080 /(Home <--Helloworld) --> /result
        }else{
          alert("กรุณากรอกเลือกจังหวัด")
        }
      },
      filterMethod (value, option) {
        return option.toUpperCase().indexOf(value.toUpperCase()) !== -1;
      }
    },
    computed:{
      addresses(){
        return this.$store.getters.getAddress
      },
      provinces(){
        return this.$store.getters.getProvince
      },
      selectedP(){
        return this.addresses.filter(address => address.addressLv2 === this.selected)
      },
      lastMem () {
        return ''
      }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
