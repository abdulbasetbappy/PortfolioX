<template>
  <div
    :class="{ dark: isDarkMode }"
    class="2xs:max-w-screen-[345px] xs:max-w-screen-xs sm:max-w-screen-sm md:max-w-screen-md lg:max-w-screen-lg xl:max-w-screen-xl 2xl:max-w-screen-2xl scroll-smooth font-san grid auto-rows-min md:grid-cols-12 2xs:grid-cols-1 2xs:p-2 2xs:m-auto m-2 p-8 gap-3"
  >
    <NuxtLayout name="profile" class="2xs:static md:col-start-1 md:col-end-6 lg:col-span-4 md:sticky md:top-[4.8rem] left-0 h-fit"></NuxtLayout>
    <div
      class="col-span-12 md:col-span-7 lg:col-span-8 md:col-start-6 lg:col-start-5 rounded-xl p-6 backdrop-blur-3xl shadow-xl bg-slate-100 dark:bg-slate-700 dark:bg-opacity-30 bg-opacity-30 dark:text-slate-100"
    >
      <!--Title-->
      <div class="">
        <h2 class="text-[40px] font-semibold">
          My Recent Article and Publications
        </h2>
        <p class="text-lg font-normal">
          I'm here to help if you're searching for a product designer to bring
          your idea to life or a design partner to help take your business to
          the next level.
        </p>
      </div>
<div class="grid md:grid-cols-1 lg:grid-cols-2 mt-4">
      <!--Blogs Archive-->
      <ContentList 
      path="/posts"
      fields = "title,date,thumbnail,category"
      v-slot="{list}"
      :query="{
        draft: false,
        sort: [
          {
            date: -1,
          },
        ],
        limit: 10,
      }"
      >
        <!--single-Blog-->
        <div
        v-for="blog in list"
        :key="blog._path"
         class="md:col-span-1 p-4">
          <!--single-Blog-Image-->
          <div class="relative">
            <img 
            v-if="blog.thumbnail"
            :src="blog.thumbnail"
            :alt="blog.title"
            class="rounded-xl w-full h-[155px] lg:h-[220px]" />
            <p class="absolute bottom-2 left-0 dark:bg-slate-700 rounded-r-md px-5">{{ blog.category }}</p>
          </div>
          <!--single-Blog-Details-->
          <div class="pt-2">
            <NuxtLink :to="blog.slug" class="text-2xl font-semibold pb-2">{{ blog.title }}</NuxtLink>
            <div><span class="mr-6"> {{ blog.readTime }} </span><span>{{ blog.date }}</span></div>
          </div>
          
        </div>
      </ContentList>
</div>

      <!--Pagination-->
      <div class=" flex justify-center items-center gap-4 my-4">
        <NuxtLink class="dark:bg-slate-600 px-5 py-2 text-lg rounded-xl"><Icon name="material-symbols:arrow-left-alt-rounded" /></NuxtLink>
        <NuxtLink  class="dark:bg-slate-600 px-5 py-2 text-lg rounded-xl"><Icon name="material-symbols:arrow-right-alt-rounded" /></NuxtLink>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { useDarkModeStore } from "~/store/darkMood";
const darkModeStore = useDarkModeStore();
const isDarkMode = computed(() => darkModeStore.darkMode);
</script>

<style scoped></style>
