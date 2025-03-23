<template>
    <Header />
    <OrderList :orders="orders" :deleteOrder="deleteOrder" />
    <OrderForm :addOrder="addOrder" />
</template>

<script setup lang="ts">
import Header from './components/Header.vue';
import OrderList from './components/OrderList.vue';
import OrderForm from './components/OrderForm.vue';
import { reactive } from 'vue';

type OrderStatus = 'В обработке' | 'В пути' | 'Доставлено';

interface Order {
    id: number;
    itemName: string;
    address: string;
    status: OrderStatus;
}

const orders = reactive<Order[]>([]);

function addOrder(order) {
    if (order.itemName === '' || order.address === '') {
        alert('Пожалуйста, заполните все поля.');
        return;
    }

    orders.push({
        id: orders.length + 1,
        itemName: order.itemName,
        address: order.address,
        status: order.status,
    });
};

function deleteOrder(order) {
    const index = orders.findIndex(o => o.id === order.id);
    if (index !== -1) {
        orders.splice(index, 1);
    }
}
</script>

<style scoped></style>
