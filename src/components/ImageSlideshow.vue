<script setup>
import product1img from '../../images/image-product-1.jpg'
import product2img from '../../images/image-product-2.jpg'
import product3img from '../../images/image-product-3.jpg'
import product4img from '../../images/image-product-4.jpg'
import product1imgThumb from '../../images/image-product-1-thumbnail.jpg'
import product2imgThumb from '../../images/image-product-2-thumbnail.jpg'
import product3imgThumb from '../../images/image-product-3-thumbnail.jpg'
import product4imgThumb from '../../images/image-product-4-thumbnail.jpg'
import { computed, ref } from 'vue'

const imgNo = ref(0)

function nextImg() {
    if (imgNo.value < 3) {
        imgNo.value++
    } else {
        imgNo.value = 0
    }
}

function prevImg() {
    if (imgNo.value > 0) {
        imgNo.value--
    } else {
        imgNo.value = 3
    }
}


// const alwaysSmall = computed((prev) => {
//     if (count.value <= 3) {
//         return count.value
//     }
//     return prev
// })
const imgArr = [product1img, product2img, product3img, product4img]
const showImg = () => {
    return imgArr[imgNo.value]
}

</script>

<template>
    <div id="image-container" class="relative">
        <div class="">
            <img :src="showImg()" alt="img" class="lg:rounded-2xl">
        </div>

        <a class="prev absolute ml-5 top-[50%] font-bold rounded-full bg-white p-1 text-center cursor-pointer w-8 h-8 lg:hidden" @click="prevImg">&#10094;</a>
        <a class="next absolute mr-5 top-[50%] font-bold rounded-full bg-white p-1 text-center cursor-pointer w-8 h-8 lg:hidden right-0" @click="nextImg">&#10095;</a>

        <!-- Thumbnail images -->
        <div class="flex gap-6 mt-5 max-lg:hidden ">
            <div class="hover:outline-2 hover:outline-orange rounded-2xl">
                <img :src="product1imgThumb" alt="product1thumb" @click="imgNo = 0" class="cursor-pointer rounded-2xl hover:opacity-35 active:opacity-25">
            </div>
            <div>
                <img :src="product2imgThumb" alt="product2thumb" @click="imgNo = 1" class="cursor-pointer rounded-2xl hover:opacity-35 active:opacity-25">
            </div>
            <div>
                <img :src="product3imgThumb" alt="product3thumb" @click="imgNo = 2" class="cursor-pointer rounded-2xl hover:opacity-35 active:opacity-25">
            </div>
            <div>
                <img :src="product4imgThumb" alt="product4thumb" @click="imgNo = 3" class="cursor-pointer rounded-2xl hover:opacity-35 active:opacity-25">
            </div>
        </div>
    </div>
</template>

<style scoped>


/* .prev,
.next {
  cursor: pointer;
  position: absolute;
  top: 40%;
  width: auto;
  padding: 16px;
  margin-top: -50px;
  color: white;
  font-weight: bold;
  font-size: 20px;
  border-radius: 0 3px 3px 0;
  user-select: none;
  -webkit-user-select: none;
} */

/* Position the "next button" to the right */
/* .next {
  right: 0;
  /* border-radius: 3px 0 0 3px;
} */

/* On hover, add a black background color with a little bit see-through */
.prev:hover,
.next:hover {
  background-color: rgba(0, 0, 0, 0.8);
}

</style>