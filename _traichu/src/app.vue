<!--     __             _      __
        / /__________ _(_)____/ /_  __  __
       / __/ ___/ __ `/ / ___/ __ \/ / / /
      / /_/ /  / /_/ / / /__/ / / / /_/ /
 _____\__/_/   \__,_/_/\___/_/ /_/\__,_/
-->

<script setup lang="ts">
import { reactive, provide } from "vue";
import { modeToken, modeKey, initial, type Mode } from "./mode"

import Traichu from "@/components/traichu/traichu.vue";
import Header from "@/components/header/header.vue"

const modeStorage = localStorage.getItem(modeKey)

const mode = reactive<Mode>(modeStorage ? JSON.parse(modeStorage) : initial)

provide(modeToken, mode)
</script>

<template>
  <main>
    <Header v-if="!mode.minimal" />
    <Traichu />
  </main>
</template>

<style>
main {
  align-items: center;
  display: flex;
  flex-direction: column;
  justify-content: center;
  min-height: 100vh;
}
</style>
