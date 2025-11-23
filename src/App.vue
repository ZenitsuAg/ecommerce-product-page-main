<script setup>
import { ref } from 'vue';
import Nav from './components/Nav.vue';
import iconCart from '../images/icon-cart.svg'
import ImageSlideshow from './components/ImageSlideshow.vue';
import CartDetails from './components/CartDetails.vue';

import { Analytics } from '@vercel/analytics/vue';
const count = ref(0)

function increment() {
    count.value++
    
    console.log(count.value)
}

function decrease() {
    if (count.value >= 1) {
        count.value--
    }
}

const showCart = ref(false)

function handleClick() {
    showCart.value = !showCart.value
    console.log("I've been clicked")
}

console.log(count.value)
</script>

<template>
    <Analytics />
    <Nav>
        <div class="relative cursor-pointer " @click="handleClick">
            <img :src="iconCart" alt="cart" >
            <div v-if="count" class="w-5 h-3 text-white bg-orange rounded-full absolute -top-2 -right-2 text-xs font-bold flex justify-center items-center">{{ count }}</div>
        </div>       
    </Nav>

    <main class="font-kumbh lg:grid lg:grid-cols-2 lg:mx-20 lg:py-10">
        <section class="lg:py-10">
            <ImageSlideshow />
        </section>
        <section class="p-5 lg:p-16 lg:my-20 lg:flex lg:flex-col lg:justify-center lg:gap-4">
            <p class="uppercase text-xs text-dark-grayish-blue font-bold tracking-widest">Sneaker Company</p>

            <h1 class="font-bold text-3xl my-4 lg:text-4xl">Fall Limited Edition Sneakers</h1>

            <p class="text-dark-grayish-blue mb-4">
                These low-profile sneakers are your perfect casual wear companion. Featuring a
                durable rubber outer sole, they’ll withstand everything the weather can offer.
            </p>

            <div class="flex items-baseline justify-between mb-4 lg:block">
                <div class="flex gap-4 items-baseline">
                    <h1 class="font-bold text-3xl text-very-dark-blue">$125.00</h1>
                    <p class="bg-very-dark-blue font-bold text-white py-0.5 px-2.5 rounded-lg">50%</p>
                </div>
                <p class="line-through font-bold text-dark-grayish-blue">$250.00</p>
            </div>

            <div class="lg:flex lg:gap-5 lg:items-baseline">
                <div
                    class="bg-light-grayish-blue rounded-lg flex-1 p-3 font-bold text-2xl text-orange flex justify-between lg:items-center mb-3">
                    <button class="hover:text-pale-orange active:text-pale-orange" @click="decrease">-</button>
                    <span class="text-very-dark-blue text-xl">{{ count }}</span>
                    <button class="hover:text-pale-orange active:text-pale-orange" @click="increment">+</button>
                </div>
                <button
                    class="font-bold w-full lg:w-auto lg:flex-2 rounded-lg text-very-dark-blue flex justify-center text-center gap-4 p-4 bg-orange hover:bg-pale-orange active:bg-pale-orange">
                    <img :src="iconCart" alt="cart-icon" class="fill-very-dark-blue">
                    Add to cart
                </button>
            </div>

        </section>
        <!-- Cart Modal -->
        <CartDetails v-if="showCart" :cartContent="count" @remove-item="count = 0"  />
    </main>

</template>

<style scoped></style>
