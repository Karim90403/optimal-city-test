<script setup lang="ts">
import { ref, computed } from 'vue';

interface Row{
  name: string,
  value: string
}

let newValue = ""

const indexOfRow = ref<number>(0)

const Rows = ref<Array<Row>>([
  {
     "name": "foo1",
     "value": "bar1",
   },
  {
     "name": "foo2",
     "value": "bar2",
   },
   {
     "name": "foo3",
     "value": "bar3",
   },
   {
     "name": "foo4",
     "value": "bar4",
   },
   {
     "name": "foo5",
     "value": "bar5",
   },
   {
     "name": "foo6",
     "value": "bar6",
   },
   {
     "name": "foo7",
     "value": "bar7",
   },
   {
     "name": "foo8",
     "value": "bar8",
   },
   {
     "name": "foo9",
     "value": "bar9",
   },
   {
     "name": "foo10",
     "value": "bar10",
   },
   {
     "name": "foo11",
     "value": "bar11",
   },
   {
     "name": "foo12",
     "value": "bar12",
   },
   {
     "name": "foo13",
     "value": "bar13",
   },
   {
     "name": "foo14",
     "value": "bar14",
   },
   {
     "name": "foo15",
     "value": "bar15",
   },
   {
     "name": "foo16",
     "value": "bar16",
   },
   {
     "name": "foo17",
     "value": "bar17",
   },
   {
     "name": "foo18",
     "value": "bar18",
   },
   {
     "name": "foo19",
     "value": "bar19",
   },
   {
     "name": "foo20",
     "value": "bar20",
   },
  ])

const changeIndex = (newIndex: number): void => {
  indexOfRow.value = newIndex;
  newValue = Rows.value[newIndex].value;
}

const changeValue = ():void => {
  Rows.value[indexOfRow.value].value = newValue;
  newValue = '';
}

const usingName = computed((): string => {
  return Rows.value[indexOfRow.value].name ?? "foo";
})

const usingValue = computed((): string => {
  return Rows.value[indexOfRow.value].value ?? "bar";
})
</script>

<template>
  <div class="text-center mb-10 mt-5 text-4xl font-extrabold leading-none tracking-tight text-gray-900 md:text-5xl lg:text-6xl dark:text-white">Редактирование списка значений</div>
  <div class="flex justify-center mb-10">
    <div class="m-2 p-6 w-1/2 bg-white border border-gray-200 rounded-lg shadow-m dark:bg-gray-800 dark:border-gray-700">
      <div class="flex items-center">
        <div class="block mb-2 mr-3 text-sm font-medium text-gray-900 dark:text-white">Name</div>
        <div class="block mb-2 text-xl font-medium text-gray-900 dark:text-white">{{ usingName }}</div>
      </div>
      <div class="flex items-center">
        <label for="small-input" class="block pt-2 mb-2 mr-3 text-sm font-medium text-gray-900 dark:text-white">Value</label>
        <input v-model="newValue" :placeholder="usingValue" type="text" id="small-input" class="block p-2 text-gray-900 border border-gray-300 rounded-lg bg-gray-50 sm:text-xs focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500">
      </div>
      <button @click="changeValue()" type="button" class="py-2.5 px-5 mr-2 mt-4 text-sm font-medium text-gray-900 focus:outline-none bg-white rounded-full border border-gray-200 hover:bg-gray-100 hover:text-blue-700 focus:z-10 focus:ring-4 focus:ring-gray-200 dark:focus:ring-gray-700 dark:bg-gray-800 dark:text-gray-400 dark:border-gray-600 dark:hover:text-white dark:hover:bg-gray-700">Изменить значение</button>
    </div>
  </div>
  <div class="flex justify-center">
    <div class="w-4/5">
      <div @click="changeIndex(index)" class="inline-flex flex-col text-center m-2 p-6 bg-white border border-gray-200 rounded-lg shadow-md hover:bg-gray-100 dark:bg-gray-800 dark:border-gray-700 dark:hover:bg-gray-700" v-for="(row, index) in Rows" :key="row.name">
        <div class="mb-2 text-2xl font-bold tracking-tight text-gray-900 dark:text-white">{{ row.name }}</div>
        <div class="font-normal text-gray-700 dark:text-gray-400">{{ row.value }}</div>
      </div>
    </div>
  </div>
</template>
