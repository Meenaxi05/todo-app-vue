<!-- <template>
  <div class="bg-gray-500 min-h-screen flex justify-center items-center">
    <div class="bg-white p-4 rounded w-96">
      <h1 class="text-2xl font-semibold mb-4 underline">To-Do APP</h1>
      <div class="flex">
        <input
          v-model="newTask"
          keyup.enter="addTask"
          class="w-10/12 p-2 rounded-1 outline-black"
          type="text"
          placeholder="Enter Task"
        />
        <button
          @click="addTask"
          class="w-2/12 bg-gray-400 text-black rounded-r p-2 hover:bg-gray-700 cursor-pointer"
        >
          ADD
        </button>
      </div>
      <ul class="mt-4">
        <li
          v-for="(task, index) in  "
          :key="index"
          class="flex justify-between items-center p-2 border-b"
        >
          <span>{{ task }}</span>
          <button
            @click="removeTask(todo)"
            class="text-red-700 hover:text-red-800 cursor-pointer"
          >
            &times;
          </button>
        </li>
      </ul>
    </div>
  </div>
</template>

<script setup>
import { ref , onMounted} from "vue";
// import { jsx } from "vue/jsx-runtime";

const newTask = ref("");
// const tasks = ref([]);

const tasks = ref(JSON.parse(localStorage.getItem("tasks")) || []);


const addTask = () => {
  if (newTask.value.trim() !== "") {
    tasks.value.push(newTask.value);
    newTask.value = "";
    localStorage.setItem("tasks" , JSON.stringify(tasks.value));
  }
};

const removeTask = (todo) => {
    tasks.value.splice(todo, 1);
    localStorage.setItem("tasks", JSON.stringify(tasks.value))
}

onMounted(() => {
    tasks.value = JSON.parse(localStorage.getItem("tasks")) || []
})
</script> -->
