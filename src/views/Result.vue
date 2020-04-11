<template>
    <div class="Result">
        <div class="row">
            <img alt="proflie" src="https://i.picsum.photos/id/866/300/300.jpg">
            <h4>ชื่อ : {{name}}</h4>
            <h4>ฉายา : {{lastName}}</h4>
            <h4>ศูนย์ : {{zero.addressName}}</h4>
            <h4>จังหวัด : {{zero.addressLv2}}</h4>
        </div>
    </div>
</template>

<script>
export default {
    methods:{
    },
    computed:{
        name(){
            let getInput = this.$store.getters.getInput
            if(getInput){
                return  `พระ${getInput}`
            }else{
                return  this.$store.getters.getName
            }
        },
        lastName(){
            return this.$store.getters.getLastName
        },
        zero(){
            return this.$store.getters.getLastMem
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