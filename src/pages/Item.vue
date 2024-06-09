<script>
import { ref, onMounted, watch } from 'vue'
import { useRoute } from 'vue-router'
import Home from './Home.vue'

export default {
  components: {
    Home
  },
  setup() {
    const route = useRoute()
    const title = ref('')
    const img = ref('')
    const price = ref('')
    const addToCart = ref('')
    const isAdded = ref('')

    const updateData = () => {
      title.value = route.query.title || ''
      img.value = route.query.img || ''
      price.value = route.query.price || ''
      addToCart.value = route.query.onclickAdd || ''
      isAdded.value = route.query.isAdded || ''
    }

    onMounted(() => {
      updateData()
    })

    watch(
      () => route.query,
      () => {
        updateData()
      }
    )

    return {
      title,
      img,
      price,
      addToCart,
      isAdded
    }
  }
}
</script>

<template>
  <div class="item-content">
    <img :src="img" :alt="title" />
    <div class="item-content-info">
      <h1>
        <strong>{{ title }}</strong>
      </h1>
      <h2>Цена: {{ price }}</h2>
      <img @click="addToCart" :src="!isAdded ? '/plus.svg' : '/checked.svg'" alt="Plus" />
    </div>
  </div>
  <Home />
</template>

<style scoped>
.item-content {
  display: flex;
  margin: 30px;
  padding: 30px;
  border-radius: 30px;
  background-color: rgb(244 244 245);

  & > img {
    object-fit: contain;
    height: 550px;
    width: 600px;
  }
}
.item-content-info {
  padding: 0 0 0 50px;
  line-height: 80px;

  & > h1 {
    font-size: 40px;
  }

  & > h2 {
    font-size: 30px;
  }

  & > img {
    height: 80px;
    width: 80px;
  }
}
</style>