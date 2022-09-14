<template>
  <header class="site-header" :style="isDarkMode ? { backgroundColor: 'rgb(22,22,30)' } : null">
    <div class="site-identity" :style="isDarkMode ? { color: 'white' } : null">
      <h1><a href="/beer" :style="isDarkMode ? { color: 'white' } : null">Punk Beer Api</a></h1>
    </div>
    <nav class="site-navigation">
      <ul class="nav">
        <li>
          <a href="/cart" :style="isDarkMode ? { color: 'white' } : null">
            Cart
          </a>
        </li>
        <li>
          <a href="/fav" :style="isDarkMode ? { color: 'white' } : null">
            WishList
          </a>
        </li>
        <!-- <li>
          <p>
            <a href="/beer" :style="isDarkMode ? { color: 'white', } : null">
              Beer API
            </a>
            <a :style="isDarkMode ? { color: 'white', } : null">&cir;</a>
            <a href="/cart" :style="isDarkMode ? { color: 'white', } : null">
              Cart
            </a>
    
            <a href="/cart">About</a>
            ·
            <a href="/beer">Beer API</a> 

          </p>
        </li> -->
        <li><label class="switch">
            <input type="checkbox" v-model="isDarkMode" @click="toggleDarkMode">
            <span class="slider round"></span>
          </label>
        </li>
      </ul>
    </nav>
  </header>
</template>
<script setup lang="ts">
const { isDarkMode, toggleDarkMode } = useDarkMode();
</script>
<style>
@import '~/assets/style/V-header.css';
</style>