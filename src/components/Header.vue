<script setup>
defineProps({
    totalPrice: Number
})

const emit = defineEmits(['toggleDrawer']) // Определяем функцию для передачи события toggleDrawer
</script>

<template>
  <header class="flex justify-between border-b border-slate-200 px-8 py-8">
    <RouterLink to="/">
        <div class="flex items-center gap-4">
           
            <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQNu65Wsxp-nZ0Uqu358E8vhdw_aSpkEbgZpQ&s" alt="image" class="w-10" />
        
            <div>
                <h2 class="text-xl font-bold uppercase">VUE COSMETIC BAG</h2>
            
                <p class="text-slate-400">Магазин лучшей косметики</p>
            
            </div>
           
    
        </div>
    </RouterLink>
    <ul class="flex items-center gap-10">
      
      <li
        @click="() => emit('toggleDrawer')"
        class="flex items-center cursor-pointer gap-3 text-gray-500 hover:text-slate-700"
      >
        <img src="/cart.svg" alt="" />
        
        <b>{{ totalPrice }} тенге</b>
      
      </li>
      <li class="flex items-center cursor-pointer gap-3 text-gray-500 hover:text-slate-700">
       
        <img src="/heart.svg" alt="" />
       
        <RouterLink to="/favorites"><span>Закладки</span></RouterLink>
        
      </li>
      <li class="flex items-center cursor-pointer gap-3 text-gray-500 hover:text-slate-700">
      
        <img src="/profile.svg" alt="" />
     
        <RouterLink to='/profile'><span>Профиль</span></RouterLink>
        <!-- Текст элемента -->
      </li>
    </ul>
  </header>
</template>
