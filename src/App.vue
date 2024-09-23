<script setup lang="ts">
import UserCard from './components/UserCard.vue'
import {computed, ref} from "vue";

const usersToDisplay= ref<User[]>([]);
const genders = ['чоловік', 'жінка'];
const genderOption = ref('');
const sampleUsers: User[] = [
  {
    firstName: "Олена",
    lastName: "Шевченко",
    gender: "Жінка",
    age: 21,
    position: "Програміст",
    photo: "https://randomuser.me/api/portraits/women/1.jpg",
    hobbies: ["Читання", "Подорожі", "Малювання"]
  },
  {
    firstName: "Андрій",
    lastName: "Ковальчук",
    gender: "Чоловік",
    age: 40,
    position: "Керівник проектів",
    photo: "https://randomuser.me/api/portraits/men/1.jpg",
    hobbies: ["Кулінарія", "Риболовля", "Теніс"]
  },
  {
    firstName: "Максим",
    lastName: "Зеленський",
    gender: "Чоловік",
    age: 28,
    position: "Стажер",
    photo: "https://randomuser.me/api/portraits/men/2.jpg",
    hobbies: ["Футбол", "Музика", "Фотографія"]
  },
  {
    firstName: "Наталія",
    lastName: "Кравченко",
    gender: "Жінка",
    age: 15,
    position: "UX Дизайнер",
    photo: "https://randomuser.me/api/portraits/women/2.jpg",
    hobbies: ["Йога", "Фотографія", "Подорожі"]
  },
  {
    firstName: "Іван",
    lastName: "Петренко",
    gender: "Чоловік",
    age: 31,
    position: "Аналітик даних",
    photo: "https://randomuser.me/api/portraits/men/3.jpg",
    hobbies: ["Велосипед", "Шахи", "Кулінарія"]
  },
  {
    firstName: "Марія",
    lastName: "Василенко",
    gender: "Жінка",
    age: 24,
    position: "Фахівець з маркетингу",
    photo: "https://randomuser.me/api/portraits/women/3.jpg",
    hobbies: ["Мода", "Малювання", "Подорожі"]
  },
  {
    firstName: "Олексій",
    lastName: "Гончарук",
    gender: "Чоловік",
    age: 18,
    position: "Веб-розробник",
    photo: "https://randomuser.me/api/portraits/men/4.jpg",
    hobbies: ["Кодинг", "Чиназес", "Біг"]
  },
  {
    firstName: "Вікторія",
    lastName: "Бондаренко",
    gender: "Жінка",
    age: 27,
    position: "Копірайтер",
    photo: "https://randomuser.me/api/portraits/women/4.jpg",
    hobbies: ["Писання", "Подорожі", "Фотографія"]
  },
  {
    firstName: "Олег",
    lastName: "Дмитренко",
    gender: "Чоловік",
    age: 34,
    position: "Системний адміністратор",
    photo: "https://randomuser.me/api/portraits/men/5.jpg",
    hobbies: ["Ігри", "Подорожі", "Кулінарія"]
  },
  {
    firstName: "Юлія",
    lastName: "Мельник",
    gender: "Жінка",
    age: 19,
    position: "Аналітик бізнес-процесів",
    photo: "https://randomuser.me/api/portraits/women/5.jpg",
    hobbies: ["Йога", "Читання", "Подорожі"]
  }
];

const usersByGender = computed(() => {
  if (genderOption.value) {
    return usersToDisplay.value.filter(u => u.gender.toLowerCase() === genderOption.value);
  }
  return usersToDisplay.value;
});

function displayUsers(){
  usersToDisplay.value = sampleUsers;
}
</script>

<template>
  <main>
    <div class="nav-bar">
      <button v-for="gender in genders" :key="gender" class="btn" @click="genderOption = gender">{{ gender }}</button>
      <button class="btn" @click="genderOption = ''">Всі користувачі</button>
      <button class="btn" @click="displayUsers">Відобразити користувачів</button>
    </div>
    <div class="flex" v-if="usersToDisplay.length > 0">
      <UserCard v-for="user in usersByGender" :key="user" :user-data="user"></UserCard>
    </div>
    <div v-else>
      <p>Список користувачів порожній</p>
    </div>
  </main>
</template>

<style scoped>
.flex {
  display: flex;
  justify-content: space-evenly;
  flex-wrap: wrap;
  gap: 25px;
}
</style>