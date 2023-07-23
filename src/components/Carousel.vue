<script setup>
import { reactive, computed } from 'vue'

const state = reactive({
    images:[
        {
            thumb: "https://images.unsplash.com/photo-1682685797769-481b48222adf?ixlib=rb-4.0.3&ixid=M3wxMjA3fDF8MHxlZGl0b3JpYWwtZmVlZHwxfHx8ZW58MHx8fHx8&auto=format&fit=crop&w=300&q=60",
            full: "https://images.unsplash.com/photo-1682685797769-481b48222adf?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDE2fHx8ZW58MHx8fHx8&auto=format&fit=crop&w=1024&q=60",
            name: 'image-01'
        },
        {
          thumb: "https://images.unsplash.com/photo-1682695794816-7b9da18ed470?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDZ8fHxlbnwwfHx8fHw%3D&auto=format&fit=crop&w=300&q=60",
          full: "https://images.unsplash.com/photo-1682695794816-7b9da18ed470?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDE2fHx8ZW58MHx8fHx8&auto=format&fit=crop&w=1024&q=60",
          name: 'image-02'
        },
        {
          thumb: "https://images.unsplash.com/photo-1682685797661-9e0c87f59c60?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDE4fHx8ZW58MHx8fHx8&auto=format&fit=crop&w=300&q=60",
          full: "https://images.unsplash.com/photo-1682685797661-9e0c87f59c60?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDE2fHx8ZW58MHx8fHx8&auto=format&fit=crop&w=1024&q=60",
          name: 'image-03'
        },
        {
          thumb: "https://images.unsplash.com/photo-1688841534418-b2e6ca99985a?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=300&q=60",
          full: "https://images.unsplash.com/photo-1688841534418-b2e6ca99985a?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1024&q=60",
          name: 'image-05'
        },
        {
          thumb: "https://images.unsplash.com/photo-1688118935892-b40fbf3b5e69?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=300&q=80",
          full: "https://images.unsplash.com/photo-1688118935892-b40fbf3b5e69?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1024&q=80",
          name: 'image-06'
        },
        {
          thumb: "https://images.unsplash.com/photo-1688153453932-bf45fe9d5f2c?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=300&q=80",
          full: "https://images.unsplash.com/photo-1688153453932-bf45fe9d5f2c?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1024&q=80",
          name: 'image-07'
        },
        {
          thumb: "https://images.unsplash.com/photo-1688232543149-5602b136ba11?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=300&q=80",
          full: "https://images.unsplash.com/photo-1688232543149-5602b136ba11?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1024&q=80",
          name: 'image-08'
        },
    ],
    currentIndex: 0,
});

const currentImage = computed(() => state.images[state.currentIndex]);

const next = () => {
    state.currentIndex = (state.currentIndex + 1) % state.images.length;
};

const previous = () => {
    state.currentIndex = (state.currentIndex - 1 + state.images.length) % state.images.length;
};

const goToCurrentSlide = (index) => {
      state.currentIndex = index;
};
</script>

<template>
    <p class="text-2xl font-bold my-4">Image Carousel</p>
    <div class="image-slider flex flex-col p-3 border border-black">
        <section class="flex justify-center items-center overflow-hidden mt-5">
            <button @click="previous"><span class="material-symbols-outlined">chevron_left</span></button>
        
            <div class="relative h-full m-5 flex justify-center items-center slider-item">
              <div class="image-container flex justify-center items-center relative overflow-hidden rounded-lg border-sm w-[50vh]">
                <img class="cursor-pointer w-full" :src="currentImage.full">
              </div>
              <div class="absolute bottom-0 my-4 font-medium text-xs text-slate-300">{{ currentImage.name }}</div>
            </div>
    
            <button @click="next"><span class="material-symbols-outlined">chevron_right</span></button>
        </section>

        <div class="indicators flex gap-2 justify-center items-center ">
            <div v-for="(image, index) in state.images" :key="index" class="flex justify-center items-center">              
                <span 
                    :class="{ active: index === state.currentIndex }"
                    @click="goToCurrentSlide(index)"
                    class="material-symbols-outlined text-slate-300 cursor-pointer text-lg">circle
                </span>
            </div>       
        </div>
    </div>  
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
.active{
    color: brown;
}
</style>
