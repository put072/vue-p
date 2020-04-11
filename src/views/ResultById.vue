<template>
    <div class="Result">
        <div class="row">
            <img alt="proflie" src="https://i.picsum.photos/id/866/300/300.jpg">
            <h4>id : {{id}}</h4>
            <h4>ชื่อ : {{name}}</h4>
            <h4>ฉายา : {{lastName}}</h4>
            <h4>ศูนย์ : {{zero.addressName}}</h4>
            <h4>จังหวัด : {{zero.addressLv2}}</h4>
        </div>
    </div>
</template>

<script>
export default {
    props: {
      id: String
    },
    created () {
      this.$store.dispatch('getZero', this.id)

    },
    methods:{
    },
    computed:{
        routeString () {
          return this.$route.params.id
        },
        name(){
          return this.$route.query.name
        },
        lastName(){
            return this.$store.getters.getLastName
        },
        zero(){
            return this.$store.getters.getZeroByQueryId
        }
    }
}
</script>

<style scoped>
img {
    width : 200px;
    float : center;
}
h4 {
    text-align: center;
    margin: 0 0 15 100px;
}
</style>