<template>
  <el-select
    class="w-full"
    clerable
    filterable
    placeholder="Поиск..."
    remote
    :remote-method="searchStore.dbRemoteMethod"
    :loading="searchStore.loading"
  >
    <div v-if="searchStore.trendsShow">
      <h1 class="h-[28px] border-b pl-[20px]">trending 🔥</h1>
      <el-option v-for="item in searchStore.trends" :key="item.id">
        <RouterLink :to="'/coin/' + item.id">
          <div style="display: flex; align-items: center; width: 100%">
            <el-image style="width: 20px; height: 20px" :src="item.large" />
            <div class="ml-5 grow">
              {{ item.name }}
            </div>
            <div class="text-right">#{{ item.market_cap_rank }}</div>
          </div>
        </RouterLink>
      </el-option>
    </div>

    <el-option v-for="item in searchStore.options" :key="item.id">
      <RouterLink :to="'/coin/' + item.id">
        <div style="display: flex; align-items: center; width: 100%">
          <el-image style="width: 20px; height: 20px" :src="item.large" />
          <div class="ml-5 grow">
            {{ item.name }}
          </div>
          <div class="text-right">#{{ item.market_cap_rank }}</div>
        </div>
      </RouterLink>
    </el-option>
  </el-select>
</template>

<script setup lang="ts">
import { useSearchStore } from '@/stores/searchStore'
const searchStore = useSearchStore()
</script>

<style scoped></style>
