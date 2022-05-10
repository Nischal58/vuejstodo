<template>
  <q-page class="flex flex-center">
    <q-card class="my-card" style="width: 600px">
      <q-card-section> <div class="text-h6">TODO LIST</div></q-card-section>

      <q-card-section>
        <div class="row justify-center">
          <div class="col-12">
            <q-input v-model="todotask" label="Input Task" />
            <q-btn color="primary" label="Add Task" @click="additem" />
          </div>
        </div>
      </q-card-section>

      <q-card-section v-if="todolist.length > 0">
        <div
          class="row justify-center q-py-md"
          v-for="(item, index) in todolist"
          :key="index"
        >
          <div class="col-8">
            
            {{ item.value }}
          </div>
        <q-btn class="q-mr-auto"
      size="10px"
      color="blue"
      label="Edit"

      @click ="editItem(index)"
    />
        <q-btn
      size="10px"
      color="red"
      label="Delete"
      @click="deleteitem(index)"
    />
         


        </div>
      </q-card-section>

      <q-card-section v-else>
        <div class="row justify-center">
          <div class="col-12">
            <div class="text-h6">No item addedd in list</div>
          </div>
        </div>
      </q-card-section>
    </q-card>
  </q-page>
</template>

<script>
import { defineComponent } from "vue";

export default defineComponent({
  name: "IndexPage",
  
  data() {
    return {
      todotask: "",
      todolist: [{ value: "Hello World" }, { value: "This is  a Todo app" }],
    };
  },

  methods: {
    additem() {
      if(this.todotask.length===0) return;
      this.todolist.push({ value: this.todotask });
      this.todotask="";
    },
    deleteitem(index) {
      this.todolist.splice(index, 1);
    },

    editItem(index){
             this.todotask= this.todolist[index].value;
      
  
    }
   

  },
});
</script>
