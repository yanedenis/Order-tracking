<template>
    <table class="order-list">
        <thead>
            <tr>
                <th>Название товара</th>
                <th>Адрес доставки</th>
                <th>Статус</th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="order in orders" :key="order.id">
                <td>{{ order.itemName }}</td>
                <td>{{ order.address }}</td>
                <td>{{ order.status }}</td>
                <td><button @click="deleteOrder(order)">Удалить</button></td>
            </tr>
        </tbody>
    </table>
</template>
<script lang="ts" setup>
defineProps<{
    orders?: { id: number, itemName: string, address: string, status: string }[],
    deleteOrder?: Function,
}>();
</script>
<style scoped>
.order-list {
    width: 100%;
    border-collapse: collapse;
}

thead th {
    border-bottom: 2px solid black;
    padding: 0 1rem;
    text-align: center;
    font-size: 1.6rem;
}

tbody td:not(:has(button)) {
    font-size: 1.3rem;
}

button {
    background-color: var(--color-secondary);
    padding: .8rem;
    margin: 1rem;
}

@media (hover) {
    button:hover {
        background-color: var(--color-accent);
    }
}

@media (max-width: 1024px) {
    thead th {
        font-size: 1.4rem;
    }

    tbody td:not(:has(button)) {
        font-size: 1.2rem;
    }
}
</style>