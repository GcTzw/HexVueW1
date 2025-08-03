<script setup>
import { ref } from 'vue';

const data = [
  {
    "id": 1,
    "name": "珍珠奶茶",
    "description": "香濃奶茶搭配QQ珍珠",
    "price": 50,
    "stock": 20
  },
  {
    "id": 2,
    "name": "冬瓜檸檬",
    "description": "清新冬瓜配上新鮮檸檬",
    "price": 45,
    "stock": 15
  },
  {
    "id": 3,
    "name": "翡翠檸檬",
    "description": "綠茶與檸檬的完美結合",
    "price": 55,
    "stock": 30
  },
  {
    "id": 4,
    "name": "四季春茶",
    "description": "香醇四季春茶，回甘無比",
    "price": 45,
    "stock": 10
  },
  {
    "id": 5,
    "name": "阿薩姆奶茶",
    "description": "阿薩姆紅茶搭配香醇鮮奶",
    "price": 50,
    "stock": 25
  },
  {
    "id": 6,
    "name": "檸檬冰茶",
    "description": "檸檬與冰茶的清新組合",
    "price": 45,
    "stock": 20
  },
  {
    "id": 7,
    "name": "芒果綠茶",
    "description": "芒果與綠茶的獨特風味",
    "price": 55,
    "stock": 18
  },
  {
    "id": 8,
    "name": "抹茶拿鐵",
    "description": "抹茶與鮮奶的絕配",
    "price": 60,
    "stock": 20
  }
];
const drinks = ref(data);

function increaseStock(id) {
  let obj = drinks.value.find(item => item.id === id);
  if (obj) {
    obj.stock++;
  }
}

function decreaseStock(id) {
  let obj = drinks.value.find(item => item.id === id);
  if (obj && obj.stock > 0) {
    obj.stock--;
  }
}
</script>

<template>
  <table class="table">
    <thead>
      <tr>
        <th scope="col">品項</th>
        <th scope="col">描述</th>
        <th scope="col">價格</th>
        <th scope="col">庫存</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="r in drinks" :key="r.id">
        <td><input type="text" v-model="r.name"></td>
        <td><small>{{ r.description }}</small></td>
        <td>{{ r.price }}</td>
        <td><button @click="decreaseStock(r.id)">-</button><input type="number" v-model.number="r.stock" min="0" @input="r.stock = Math.max(0, r.stock)"><button @click="increaseStock(r.id)">+</button></td>
      </tr>
    </tbody>
  </table>
</template>

<style scoped></style>
