<template>
  <Block title="Sortable">
    <ul data-controller="sortable">
      <li class="block mb-4 p-4 border border-3 border-gray-600 rounded-sm cursor-move">Pet the cat</li>
      <li class="block mb-4 p-4 border border-3 border-gray-600 rounded-sm cursor-move">Get the groceries</li>
    </ul>

    <h2 class="text-xl mt-8 mb-2">With custom handler</h2>
    <ul data-controller="sortable" data-sortable-handle-value=".handle">
      <li class="block mb-4 p-4 border border-3 border-gray-600 rounded-sm">
        <svg
          class="handle size-6 inline cursor-move"
          fill="none"
          stroke="currentColor"
          viewBox="0 0 24 24"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 8h16M4 16h16"></path>
        </svg>
        Pet the cat
      </li>

      <li class="block mb-4 p-4 border border-3 border-gray-600 rounded-sm">
        <svg
          class="handle size-6 inline cursor-move"
          fill="none"
          stroke="currentColor"
          viewBox="0 0 24 24"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 8h16M4 16h16"></path>
        </svg>
        Get the groceries
      </li>
    </ul>
  </Block>
</template>

<script setup>
import Block from "@/components/UI/Block.vue"
</script>
