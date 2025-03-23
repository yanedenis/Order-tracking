<template>
    <div class="popup-form" id="popup-form">
        <form class="order-form" autoComplete="off">
            <label for="itemName">Название товара</label>
            <input type="text" id="itemName" v-model="order.itemName" required>
            <label for="address">Адрес доставки</label>
            <input type="text" id="address" v-model="order.address" required>
            <label for="status">Статус</label>
            <select id="status" v-model="order.status">
                <option value="В обработке">В обработке</option>
                <option value="Доставлено">Доставлено</option>
                <option value="В пути">В пути</option>
            </select>
            <button type="button" @click="addOrder(order)">Добавить заказ</button>
        </form>
    </div>
</template>
<script setup lang="ts">
defineProps<{
    addOrder: Function,
}>();

let order = {
    itemName: '',
    address: '',
    status: 'В обработке',
};
</script>
<style scoped>
.popup-form {
    display: flex;
    justify-content: center;
    align-items: center;
    position: fixed;
    bottom: 5vh;
    right: 2vh;
    font-size: 1.5rem;
    width: max-content;
    background-color: var(--color-text);
    color: var(--color-background);
    padding: .2rem 1rem;
    border-radius: 6px;
    margin: 0 auto;

}

button {
    padding: .5rem;
    margin: .8rem;
    display: block;
}

label {
    display: block;
    margin: 1rem 0 .2rem;
}

input, select {
    width: 100%;
    padding: .5rem 0;
    background-color: transparent;
    outline: 0;
    border: 0;
    font-size: 1.3rem;
    border-bottom: 4px solid var(--color-background);
    color: var(--color-background);
}

option {
    color: var(--color-text);
}

@media (max-width: 1024px) {
    .popup-form {
        font-size: 1.2rem;

        input, select {
            font-size: 1.1rem;
        }
    }
}
</style>