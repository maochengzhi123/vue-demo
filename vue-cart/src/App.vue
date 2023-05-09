<script setup>
import { reactive, computed } from 'vue';
const productList = reactive([
  { title: '瓶子', price: 20, count: 0, img: 'src/assets/1.png' },
  { title: '鞋子', price: 50, count: 0, img: 'src/assets/2.png' },
  { title: '衣服', price: 100, count: 0, img: 'src/assets/3.png' },
]);

const handleAdd = (index) => {
  productList[index].count += 1;
};
const handleSub = (index) => {
  productList[index].count -= 1;
};

const total = computed(() => {
  let sum = 0;
  productList.map((item) => {
    sum += item.count * item.price;
  });
  return sum;
});

const cartList = computed(() => {
  return productList.filter((item) => !!item.count);
});
</script>

<template>
  <section class="product">
    <ul class="list">
      <li v-for="(item, index) in productList">
        <img :src="item.img" alt="" />
        <div class="title">{{ item.title }}</div>
        <div class="price">价格: {{ item.price }}</div>
        <div class="btn" @click="handleAdd(index)" v-if="!item.count">
          添加到购物车
        </div>
        <div class="btn-box" v-else>
          <div class="btn" @click="handleSub(index)">-</div>
          <div>{{ item.count }}</div>
          <div class="btn" @click="handleAdd(index)">+</div>
        </div>
      </li>
    </ul>
  </section>
  <section class="cart">
    <ul class="list-header">
      <li>序号</li>
      <li>名称</li>
      <li>图片</li>
      <li>数量</li>
      <li>价格</li>
    </ul>
    <ul class="list-body">
      <li v-for="(item, index) in cartList">
        <div>{{ index }}</div>
        <div>{{ item.title }}</div>
        <div><img :src="item.img" alt="" /></div>
        <div>{{ item.count }}</div>
        <div>{{ item.count * item.price }}</div>
      </li>
    </ul>
  </section>
  <section class="total"><span>总价：</span>¥{{ total }}</section>
</template>

<style scoped>
.btn {
  text-align: center;
  width: 200px;
  background-color: #4897dd;
  border-radius: 8px;
  height: 32px;
  line-height: 32px;
  color: #fff;
  cursor: pointer;
}
.btn:hover {
  background-color: #277ac3;
}
.product {
  margin-bottom: 24px;
}
.product .list {
  display: flex;
}
.product .list li {
  width: 220px;
  padding: 12px;
  border: 1px solid #ebebeb;
  border-radius: 16px;
  margin-right: 12px;
}
.product .list li .title {
  font-size: 24px;
  font-weight: bold;
  margin-bottom: 8px;
}
.product .list li .price {
  font-size: 20px;
  margin-bottom: 8px;
}
.product .list li img {
  width: 220px;
  height: 220px;
}
.product .list li .btn-box {
  display: flex;
}
.product .list li .btn-box .btn {
  width: 40px;
}
.product .list li .btn-box > div {
  flex: 1;
  text-align: center;
  line-height: 32px;
}

.cart .list-header {
  display: flex;
}

.cart .list-header li {
  flex: 1;
  border-top: 1px solid #c6c6c6;
  border-left: 1px solid #c6c6c6;
  border-bottom: 1px solid #c6c6c6;
  text-align: center;
  height: 50px;
  line-height: 50px;
  font-weight: bold;
}
.cart .list-body li {
  display: flex;
  border-top: 1px solid #c6c6c6;
  height: 60px;
  line-height: 44px;
  text-align: center;
}
.cart .list-body li:first-child {
  border-top: none;
}
.cart .list-body li:last-child {
  border-bottom: 1px solid #c6c6c6;
}
.cart .list-body li > div {
  flex: 1;
  border-left: 1px solid #c6c6c6;
  padding: 8px;
}
.cart .list-header li:last-child,
.cart .list-body li > div:last-child {
  border-right: 1px solid #c6c6c6;
}
.cart .list-body li > div img {
  width: 45px;
  height: 45px;
}

.total {
  text-align: right;
  margin-top: 24px;
  font-size: 32px;
}
.total span {
  margin-right: 12px;
}
</style>
