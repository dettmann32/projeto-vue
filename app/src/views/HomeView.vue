<template>
  <div class="m-[50px] min-h-[250px]">
    <BanNer></BanNer>
    <BurgerForm></BurgerForm>
  </div>
</template>

<script>
import BanNer from '@/components/BanNer.vue';
import BurgerForm from '../components/BurgerForm.vue';
export default{
  components:{
    BanNer,BurgerForm
  }
}
</script>
