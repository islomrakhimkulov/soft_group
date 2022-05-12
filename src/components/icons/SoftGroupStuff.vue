<script lang="ts">
import { defineComponent } from "vue";
export default defineComponent({
  name: "SoftGroupStuff",
  data: () => ({
    name: "",
    surname: "",
    position: "",
    selected: "",
    departments: [
      { id: 1, name: "IT" },
      { id: 2, name: "Marketing" },
      { id: 3, name: "Business" },
    ],
    users: [],
  }),
  methods: {
    addUser(
      id: number,
      name: string,
      surname: string,
      position: string,
      department: string
    ): void {
      if (this.name && this.surname && this.position) {
        let newStuff = {
          id: this.users.length + 1,
          name: this.name,
          surname: this.surname,
          position: this.position,
          department: this.departments,
        };
        this.users.push(newStuff);
        this.name = "";
        this.surname = "";
        this.position = "";
        this.departments = "";
      } else {
        alert("Forma to'ldirilmagan");
      }
    },
  },
});
</script>

<template>
  <div class="stuff">
    <h1>Soft Group Company Stuff's List</h1>
    <form action="">
      <div>
        <label for="name">Ismi</label>
        <input type="text" v-model="name" placeholder="Ism " id="name" />
      </div>
      <div>
        <label for="surname">Familya</label>
        <input
          type="text"
          v-model="surname"
          placeholder="Familya"
          id="surname"
        />
      </div>
      <div>
        <label for="department">Bo'lim</label>
        <select id="department" v-model="selected">
          <option
            v-for="department in departments"
            :key="department.id"
            v-bind:value="{ id: department.id, text: department.name }"
          >
            {{ department.name }}
          </option>
        </select>
      </div>
      <div>
        <label for="position">Lavozimi</label>
        <input
          type="text"
          v-model="position"
          placeholder="Lavozimi"
          id="position"
        />
      </div>
      <button @click="addUser" type="button">Xodim Qo'shish</button>
    </form>

    <div>
      <table>
        <tr>
          <th>Id</th>
          <th>Ism</th>
          <th>Familya</th>
          <th>Bo'limi</th>
          <th>Lavozimi</th>
        </tr>
        <tr v-for="user in users" :key="user.id">
          <td>{{ user.id }}</td>
          <td>{{ user.name }}</td>
          <td>{{ user.surname }}</td>
          <td>{{ selected.text }}</td>
          <td>{{ user.department }}</td>
          <td>{{ user.position }}</td>
        </tr>
      </table>

      <div>
        <h1>Value: {{ selected.id }}</h1>
        <h1>Text: {{ selected.text }}</h1>
      </div>
    </div>
  </div>
</template>

<style scope></style>
