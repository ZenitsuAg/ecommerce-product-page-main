<script setup>
import { ref } from 'vue';
import avatarImg from '../../images/image-avatar.png'
import iconMenu from '../../images/icon-menu.svg'
import iconClose from '../../images/icon-close.svg'
import logo from '../../images/logo.svg'
import gsap from 'gsap'

const openMenu = ref(false)


function onBeforeEnter(el) {
    gsap.set(el, {
        x: -700,
        ease: 'power.inOut(2.5, 1)',
        opacity: 1
    })
}

function onEnter(el, done) {
    gsap.to(el, {
        x: 0,
        duration: 1,
        scaleX: 1,
        scaleY: 1,
        opacity: 1,
        ease: 'power.inOut(2.5, 1)',
        onComplete: done
    })
}

function onLeave(el, done) {
    gsap.to(el, {
        duration: 0.7,
        scaleX: 1,
        scaleY: 1,
        x: -700,
        ease: 'power.inOut(2.5, 1)'
    })
    gsap.to(el, {
        duration: 0.2,
        delay: 0.5,
        opacity: 0,
        onComplete: done
    })
}
</script>

<template>
    <nav class=" relative flex justify-between py-7 mx-7 font-kumbh lg:border-b lg:border-light-grayish-blue bg lg:mx-24 lg:p-0">
        <div class="flex items-baseline gap-3 lg:gap-10">
            <img :src="iconMenu" alt="icon-menu" @click="openMenu = true" class="hidden max-lg:block cursor-pointer">

            <Transition @before-enter="onBeforeEnter" @enter="onEnter" @leave="onLeave" :css="false">
                <div @click.stop="openMenu = false"
                    class="h-screen fixed z-10 left-0 top-0 w-full overflow-auto bg-black/50 flex"
                    v-if="openMenu">
                    <div @click.stop class="inner p-6 font-bold bg-white text-black min-w-[250px]">
                        <img :src="iconClose" alt="icon-close" @click="openMenu = false" class="cursor-pointer mt-3.5 mb-12">
                        <div class="flex flex-col gap-5">
                            <a href="#">Collections</a>
                            <a href="#">Men</a>
                            <a href="#">Women</a>
                            <a href="#">About</a>
                            <a href="#">Contact</a>
                        </div>
                    </div>
                </div>
            </Transition>
            <img :src="logo" alt="Logo">
            <div class="hidden lg:block">
                <div class="flex flex-row gap-5">
                    <a href="#" class="py-7 border-b-4 border-transparent text-dark-grayish-blue hover:text-very-dark-blue hover:border-b-4 hover:border-orange">Collections</a>
                    <a href="#" class="py-7 border-b-4 border-transparent text-dark-grayish-blue hover:text-very-dark-blue hover:border-b-4 hover:border-orange">Men</a>
                    <a href="#" class="py-7 border-b-4 border-transparent text-dark-grayish-blue hover:text-very-dark-blue hover:border-b-4 hover:border-orange">Women</a>
                    <a href="#" class="py-7 border-b-4 border-transparent text-dark-grayish-blue hover:text-very-dark-blue hover:border-b-4 hover:border-orange">About</a>
                    <a href="#" class="py-7 border-b-4 border-transparent text-dark-grayish-blue hover:text-very-dark-blue hover:border-b-4 hover:border-orange">Contact</a>
                </div>
            </div>
        </div>

            

        <div class="flex items-center gap-6">
            <div class="">
                <slot/>
            </div>
            <div class="w-6 h-6 lg:w-10 lg:h-10 hover:outline-2 hover:rounded-full hover:outline-orange">
                <img :src="avatarImg" alt="avatar">
            </div>
            
        </div>
    </nav>

    
</template>

