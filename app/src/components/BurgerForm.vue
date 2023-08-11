<template>
    <div>
        <h1>Monte seu Burger:</h1>
        <p>componente de mensagem</p>
        <div>
            <div class="md:w-[50%] m-auto">
                <form @submit="createBurger">
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
                        <div class="flex justify-center p-10">
                            <div class="ml-5" v-for="opcao in opcionais" :key="opcao.id" >
                                <input type="checkbox" name="opicionais" v-model="opcionais" :value="opcao.tipo">
                                <span>{{ opcao.tipo }}</span>
                            </div>
                        </div>
                    </div>
                    <div class="text-center bg-gray-900 rounded-sm hover:bg-gray-700 ">
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
            paes: null,
            carnes:null,
            opcionais:null,
            data:[],
        }
    },

    methods:{
        async getIngredients(){

            const req = await fetch("http://localhost:3000/ingredientes")
            const data = await req.json()

            this.opcionais = data.opcionais
            this.carnes = data.carnes
            this.paes = data.paes
        },
        async createBurger(e){
            e.preventDefault()
            const data = {
                pao: this.paes,
                carne: this.carnes,
                opcional: Array.from( this.opcionais),
                status: "Solicitado"
            }

            console.log(data)
        }


    },
   
      mounted(){
        this.getIngredients()
        
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