<script setup>
import {ref} from 'vue'

const item_id = ref(0)
const shop_item = ref('')
const shop_list = ref([])
const shop = ref(false)

function add_item() {
    shop_list.value.push({
        id: item_id.value++,
        item: shop_item.value,
        status: shop.value
    })

    shop_item.value = ""
}

function removeItem(i){
    shop_list.value = shop_list.value.filter((t) => t !== i)
}

</script>


<template>
    <div class="myDiv">

        <h1> My Shopping List </h1>
        <input type='text' v-model="shop_item">
        <button @click="add_item">Add Item</button>

        <ol>
        <li v-for="i in shop_list">
            <input type="checkbox" v-model="i.status">
            <span :class="{done: i.status}">{{ i.item }}</span>
            <button @click="removeItem(i)">X</button>
        </li>
        <h5 v-if="shop_list.length < 1">No List Items</h5>
        </ol>

    </div>


</template>


<style scoped>
.done{
    text-decoration: line-through;
}
.myDiv {
  border: 5px outset lightgreen;
  background-color: lightgray;
  text-align: center;
  padding: 60px;
  color: black;
}

</style>