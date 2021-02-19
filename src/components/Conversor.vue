<template>
    <div class="conversor">
        <h2>{{moedaA}} Para {{moedaB}}</h2>
        <input class="input-data" type="text" v-model="moedaA_value" v-bind:placeholder="moedaA">
        <input class="input-button" type="button" value="converter" v-on:click="converter">
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
            let moeda_conversao = this.moedaA

            let url = `https://economia.awesomeapi.com.br/all/${de_para}`;

            fetch(url).then(res =>{return res.json()})
                      .then(json=>{
                          let cotacao = json[moeda_conversao].ask;
                          this.moedaB_value = (cotacao * parseFloat(this.moedaA_value)).toFixed(2);
                      });

        }
    }

}
</script>

<style scoped>
.conversor{
    padding: 30px;
    max-width: 300px;
    box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
}
.input-data{
    border: none;
    border-radius: 0.2rem;

    padding: 0.8rem;

    width: 100%;
}
.input-button{
    border: none;
    margin: 10px;
    color:black;
    padding: 10px;
    border-radius: 10px;
}
</style>