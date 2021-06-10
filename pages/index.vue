<template>
  <div class="m-2">
    <div class="p-1">
      <div class="relative flex items-center">
        <div class="absolute top-0 mr-0 right-0 h-full p-2 flex items-center">
          <button
            @click="agregarTarea"
            class="
              rounded-full
              mr-0
              bg-blue-500
              h-full h-8
              w-8
              text-lg text-white text-bold
              hover:bg-blue-600
              focus:outline-none
            "
          >
            +
          </button>
        </div>
        <input
          v-model="title"
          class="
            py-2
            pl-5
            pr-12
            focus:outline-none
            border-2
            w-full
            rounded-full
            border-grey-300
          "
          type="text"
          name="title"
          id="title"
        />
      </div>
    </div>
    <Card
      @update="item.stated = !item.stated"
      :stated="item.stated"
      @delete="BorrarTarea(i)"
      :title="item.title"
      :key="i"
      v-for="(item, i) in tarea"
    />
  </div>
</template>

<script>
import Card from "~/components/Card.vue";
export default {
  components: { Card },
  data() {
    return {
      tarea: [],
      title: "",
    };
  },
  methods: {
    agregarTarea() {
      if (this.title.trim()) {
        this.tarea.push({ title: this.title.toUpperCase(), stated: false });
        this.title = "";
      }
    },
    BorrarTarea(p) {
      this.tarea.splice(p, 1);
    },
  },
};
</script>

<style>
</style>
