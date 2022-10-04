<template>
  <form class="p-4">
    <h1 class="text-2xl font-medium pb-9">Заказать звонок</h1>
    <div class="flex flex-col md:grid md:grid-cols-3 lg:grid-cols-4">
      <div class="md:pr-6">
        <label class=" text-gray-700 font-medium" for="phone">Телефон*</label>
        <input v-bind:value="phone" @input="phone = $event.target.value" class="w-full border-gray-300 rounded-lg mb-5"
          type="tel" v-mask="'+7(###)###-##-##'" placeholder="+7(___)___-__-__" required />
      </div>
      <div class="md:pr-6">
        <label class=" text-gray-700 font-medium" for="name">Имя*</label>
        <input oninput="this.value=this.value.replace(/[^a-zA-ZА-Яа-яЁё ]/g,'');" v-bind:value="name"
          @input="name = $event.target.value" class="w-full border-gray-300 rounded-lg mb-5" type="text"
          placeholder="Иван Иванов" required />
      </div>
      <div class="lg:pr-6">
        <label class=" text-gray-700 font-medium" for="email">Email*</label>
        <input v-bind:value="email" @input="email = $event.target.value"
          class="w-full border-gray-300 rounded-lg mb-5 md:mb-0" type='email' placeholder="you@example.com" required />
      </div>
      <div class="md:col-span-2 lg:col-span-1 md:pr-5 lg:p-0">
        <label class=" text-gray-700 font-medium" for="city">Город*</label>
        <select v-bind:value="city_id" @input="city_id = $event.target.value" class="w-full border-gray-300 rounded-lg">
          <option v-for="option in city" v-bind:value="option.id">{{option.name}}</option>
        </select>
      </div>
      <button @click="submit"
        class="w-full lg:col-start-4 md:self-end p-2 mt-5 md:mt-0 bg-green-600 hover:bg-green-700 text-white text-base rounded-lg">
        Отправить
      </button>
    </div>
  </form>
</template>

<script>
import axios from 'axios'
import { mask } from 'vue-the-mask'
export default {
  directives: { mask },
  data() {
    return {
      city: [
        { id: 1, name: "Москва" },
        { id: 2, name: "Санкт-Петербург" }
      ],
      name: '',
      phone: '',
      email: '',
      city_id: ''
    }
  },
  methods: {
    async submit() {
      axios.post('http://hh.autodrive-agency.ru/test-tasks/front/task-7/', {
        name: '',
        phone: '',
        email: '',
        city_id: '',
      })
    }
  }
}

</script>

<style>
input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  appearance: none;
  margin: 0;
}
</style>