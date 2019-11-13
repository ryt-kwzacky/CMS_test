<template>
  <div class="items">
    <div v-for="item in items" :key="item" class="item-box">
      <div class="name">
        {{ item.title }}
      </div>
      <div class="price">
        {{ item.body }}
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data () {
    return {
      items: ''
    }
  },
  // API通信
  async asyncData () {
    const { data } = await axios.get('https://rytkwsktest.microcms.io/api/v1/article', {
      headers: { 'X-API-KEY': 'be2aeca3-f2b6-496b-b2e6-d96980bd2a14' }
    })
    return {
      items: data.contents
    }
  }
}
</script>

<style>
.items{
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 200px 0;
  flex-wrap: wrap;
  width: 500px;
  margin: 0 auto;
  color: #2d3436;
}
.item-box{
  width: 100%;
  border: solid 1px #2d3436;
  border-radius: 5px;
  margin-bottom: 20px;
  box-shadow: 0px 3px 10px rgba(0,0,0,0.5);
}
.name{
  background: #2d3436;
  padding: 5px;
  text-align: center;
  color: #dfe6e9;
  font-weight: bold;
}
.price{
  text-align: center;
  background: #636e72;
  color: #dfe6e9;
  padding: 0 10px;
}
</style>
