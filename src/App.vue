<script setup>
// // import { isReactive, reactive, ref, computed } from "vue";
// // export default {
// //   // `setup` is a special hook dedicated for composition API.
// //   setup() {
// //     const state = reactive({ count: 0, odd: true });
// //     const count = ref(0);

// //     const author = reactive({
// //       name: "John Doe",
// //       books: [
// //         "Vue 2 - Advanced Guide",
// //         "Vue 3 - Basic Guide",
// //         "Vue 4 - The Mystery",
// //       ],
// //     });

// //     // list rendering
// //     const lists = ref([{ message: "Foo" }, { message: "Bar" }]);

// //     // event handler
// //     const handleCount = (event, data, data1, data2) => {
// //       state.count++;
// //     };

// //     // computed
// //     const publishedBooksMessageFunc = () => {
// //       console.log("publishedBooksMessageFunc run");
// //       return author.books.length > 0 ? "Yes" : "No";
// //     };

// //     const publishedBooksMessage = computed(() => {
// //       console.log("publishedBooksMessage run");
// //       return author.books.length > 0 ? "Yes" : "No";
// //     });

// //     // class - style binding

// //     return {
// //       state,
// //       handleCount,
// //       count,
// //       lists,
// //       publishedBooksMessageFunc,
// //       publishedBooksMessage,
// //     };
// //   },
// // };
// //
//

import { reactive, computed } from "vue";
import Input from "./components/Input.vue";

const data = reactive({
  email: "",
  password: "",
});
a;
const handleInputByUser = (event) => {
  const { name, value } = event.target;
  data[name] = value;
};

const handleSubmit = (event) => {
  // event.preventDefault();

  console.log({
    email: data.email,
    password: data.password,
  });
};

const errorMessage = computed(() => {
  if (
    data.email !== "" &&
    !/^(([^<>()[\]\\.,;:\s@\"]+(\.[^<>()[\]\\.,;:\s@\"]+)*)|(\".+\"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/.test(
      data.email
    )
  ) {
    return "email ko hop le";
  }
});
</script>

<template>
  <main class="container is-max-desktop">
    <!-- {{ state.count }}
    <hr />
    <li v-for="(item, idx) in lists" :key="idx">
      {{ item.message }} - {{ idx }}
    </li>
    <hr />

    {{ publishedBooksMessageFunc() }}-- publishedBooksMessageFunc
    {{ publishedBooksMessage }}-- publishedBooksMessage
    <button @click="handleCount">increase count</button>
    <hr />
    <button @click="handleCount($event, '2', '4', '5')">increase count</button> -->
    {{ data }}
    <div class="card">
      <div class="card-header-title is-justify-content-center">
        <h1 class="is-size-4 has-text-weight-bold">Login</h1>
      </div>
      <div class="card-content">
        <div class="content">
          <form @submit.prevent="handleSubmit">
            <Input
              :value="data.email"
              :handle-input="handleInputByUser"
              :name="'email'"
            />

            <Input
              :value="data.password"
              :handle-input="handleInputByUser"
              :name="'password'"
              :type="'password'"
            />

            <div class="field is-grouped is-grouped-right mt-6">
              <div class="control">
                <button
                  type="submit"
                  class="button is-success is-family-monospace"
                >
                  Submit
                </button>
              </div>
            </div>
          </form>
        </div>
      </div>
    </div>
  </main>
</template>

<style scoped>
main {
  width: 50vw;
  margin: 50px auto;
  font-size: 20px;
  font-family: "Inter", sans-serif;
}
</style>
