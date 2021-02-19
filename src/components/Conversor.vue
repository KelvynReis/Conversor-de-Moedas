<template>
    <div class="conversor">
        <h2>{{moedaA}} Para {{moedaB}}</h2>
        <input type="text" v-model="moedaA_value" v-bind:placeholder="moedaA">
        <input type="button" value="converter" v-on:click="converter">
        <h2>{{moedaB_value}}</h2>
    </div>
</template>

<script>
export default {
    name: "Converosor",
    props: ["moedaA", "moedaB"],

    data(){
        return{
            moedaA_value: "",
            moedaB_value: 0
        };
    },
    methods:{

        converter(){
            let de_para = this.moedaA + "-" + this.moedaB;
            let valorA = this.moedaA

            let url = `https://economia.awesomeapi.com.br/all/${de_para}`;

            fetch(url).then(res =>{return res.json()})
                      .then(json=>{
                          let cotacao = json[valorA].ask;
                          console.log(cotacao);
                          this.moedaB_value = (cotacao * parseFloat(this.moedaA_value)).toFixed(2);
                      })

        }
    }

}
</script>

<style scoped>

</style>