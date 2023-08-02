<template>
  <div class="grid grid-cols-4 text-center" >
    <div class="border-2 border-black h-40">
        <h1 class="text-2xl font-semibold mt-4 mb-4 ">Мои задачи</h1>
        <div class="">
          <form @submit.prevent="addTask" class="flex justify-center ">
            <input placeholder="Введите задачу" v-model="newTask" type="text" class="w-40 px-2 py-1 border text-gray-800 border-gray-200 bg-white focus:outline-none text-sm">
            <button  type="submit" class="px-2 rounded-r-md bg-blue-500 text-white font-semibold hover:bg-blue-600 focus:outline-none text-sm">Добавить</button>
          </form> 
        </div>
    </div>
    <div class="border-2 border-black  h-40">
        <h1 class="text-2xl font-semibold mt-4 mb-4 ">Дата</h1>
        <div class="">
          <form @submit.prevent="addDate" class="flex justify-center ">
            <input placeholder="Введите дату" v-model="newDate" type="date" class="w-40  px-2 py-1 border text-gray-800 border-gray-200 bg-white focus:outline-none text-sm">
            <button  type="submit" class="px-2 rounded-r-md bg-blue-500 text-white font-semibold hover:bg-blue-600 focus:outline-none text-sm">Добавить</button>
          </form> 
        </div>
    </div>
    <div class="border-2 border-black  h-40">
        <h1 class="text-2xl font-semibold mt-4 mb-4 ">Статус</h1>
        <div class="">
          <form @submit.prevent="addStatus" class="flex justify-center ">
            <input placeholder="Введите статус" v-model="newStatus" type="text" class="w-40  px-2 py-1 border text-gray-800 border-gray-200 bg-white focus:outline-none text-sm">
            <button  type="submit" class="px-2 rounded-r-md bg-blue-500 text-white font-semibold hover:bg-blue-600 focus:outline-none text-sm">Добавить</button>
          </form> 
        </div>
    </div>
    <div class="border-2 border-black  h-40">
      <h1 class="text-2xl font-semibold mt-4 mb-4 ">События</h1>
    </div>
  </div>
    <div class="grid grid-cols-10 text-center mt-10 ml-10" >
        <ul class="mt-4">
            <h2 class="border-2 bg-blue-500 text-white">Задачи/Дата</h2>
            <li class="border-4" v-for="(task, index) in tasks" :key="index">
              <input class="w-28 " v-model="task " @change="updateArrayTask(task, index)" />
            </li>
        </ul>
        <ul class="mt-4 border-4" v-for="date in dates" :key="date">
          {{ date }}
          <li class="border-4" v-for="(task, index) in tasks" :key="index">
            <select>
              <option v-for="(status, index) in statuses" :key="index"> {{ status }} </option>
            </select>
          </li>
        </ul>
    </div>
    <div class="mt-10 ml-10">
      Список задач: {{ tasks.join(', ') }} <br/>
      Даты: {{  dates.join(', ') }} <br/>
      Статусы: {{ statuses.join(', ') }}
    </div>
  </template>
  
  <script>
  export default {
    data() {
    return {
        newTask: "",
        tasks:  [],
        newDate: "",
        dates: [],
        newStatus: "",
        statuses: [],
        newEvent: "",
        events: [],
      }  
    },
    component: {

    },
    methods: {
      updateArrayTask(task, index) {
        this.tasks[index] = task;
      },
      addTask() {
        if (this.newTask !== '') {
          this.tasks.push(this.newTask)
          this.newTask = '';
        }
      },
      addDate() {
        if (this.newDate !== '') {
          this.dates.push(this.newDate)
          this.newDate = '';
        }
      },
      addStatus() {
        this.statuses.push(this.newStatus)
        this.newStatus = '';
      },
      addEvent() {
        this.events.push(this.newEvent)
        this.newEvent = '';
      },
    }
  }

  </script>