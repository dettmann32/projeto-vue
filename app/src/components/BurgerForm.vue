<template>
    <div>
        <h1>Monte seu Burger:</h1>
        <p>componente de mensagem</p>
        <div>
            <div class="md:w-[50%] m-auto">
                <form >
                    <div class="flex flex-col mb-[20px] ">
                        <label for="nome">Nome do cliente:</label>
                        <input type="text"  id="name" name="nome" v-model="nome" placeholder="Digite o seu nome" class="border border-gray-500">
                    </div>
                    <div class="flex flex-col mb-[20px]">
                        <label for="pão">Escolha o pão:</label>
                        <select name="pao" id="pao" v-model="pao">
                            <option value="">Selecione um pão</option>
                            <option v-for="pao in paes" :key="pao.id" :value="pao.tipo">{{ pao.tipo }} </option>
                        </select>
                    </div>
                    <div class="flex flex-col mb-[20px]">
                        <label for="carne">Escolha a carne do seu Burger:</label>
                        <select name="carne" id="carne" v-model="carne">
                            <option value="">Selecione a carne</option>
                            <option v-for="carne in carnes" :key="carne.id" :value="carne.tipo">{{ carne.tipo }}</option>
                        </select>
                    </div>
                    <div class="flex flex-col mb-[20px]">
                        <label for="opcionais" class="text-6xl">Selecione os opcionais:</label>
                        <div class="flex flex-wrap">
                            <div class="ml-5">
                                <input type="checkbox" name="opicionais" v-model="opicionais" value="salame">
                                <span>salame</span>
                            </div>
                            <div class="ml-5">
                                <input type="checkbox" name="opicionais" v-model="opicionais" value="salame">
                                <span>salame</span>
                            </div>
                            <div class="ml-5">
                                <input type="checkbox" name="opicionais" v-model="opicionais" value="salame">
                                <span>salame</span>
                            </div>
                        </div>
                    </div>
                    <div class="text-center bg-gray-600 rounded-sm hover:bg-gray-500 ">
                        <input type="submit" value="Criar meu Burger!" class="text-[#fcba03]">
                    </div>
                </form>
            </div>
        </div>    
    </div>
</template>

<script>
export default {
    name:'BurgerForm',
    data () {
        

        return {
           data:[],
           url: "http://swapi.dev/api/people"
        }
    },
   
      mounted(){
         fetch('url')
        .then( res => res.json())
        .then(dado => {
            console.log(dado)
            this.data = dado
        })
        
      }
        
    }

</script>

<style  scoped>
label{
    @apply mb-4 text-gray-950 py-1 px-2 border-l-4 border-orange-300 text-center text-xl
}

select{
    @apply border-4 border-gray-400 
}

input{
    @apply py-2 px-2
}

</style>