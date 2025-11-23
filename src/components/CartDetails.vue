<script setup>
import deleteIcon from '../../images/icon-delete.svg'
import product1imgThumb from '../../images/image-product-1-thumbnail.jpg'

const props = defineProps({
    cartContent: Number
})

</script>

<template>
    <div
        class="absolute z-1 w-full max-w-[350px] right-0 mr-4 max-lg:top-0 max-lg:mt-24 lg:-mt-12 peer-hover:block rounded-lg shadow-xl bg-white ">
        <p class="font-bold border-b border-light-grayish-blue p-3 shadow-xs">Cart</p>

        <div v-if="!cartContent" class="h-40 flex justify-center items-center">
            <p class="text-medium text-dark-grayish-blue font-bold">Your cart is empty.</p>
        </div>

        <div v-else class="p-5 flex flex-col">
            <div class="flex justify-between items-center gap-4 mb-4 text-dark-grayish-blue">
                <img :src="product1imgThumb" alt="img" class="w-10 h-10 rounded">
                <div>
                    <p class="">Fall Limited Edition Sneakers</p>
                    <p>$125.00 x {{ cartContent }} <span class="font-bold text-very-dark-blue">${{ (cartContent *
                        125).toFixed(2) }}</span></p>
                </div>
                <img :src="deleteIcon" alt="delete-icon" @click="$emit('remove-item')">
            </div>
            <button
                class="bg-orange hover:bg-pale-orange active:bg-pale-orange w-full p-4 rounded-lg text-very-dark-blue font-bold">Checkout</button>
        </div>
    </div>
</template>