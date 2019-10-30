<template>
  <div class="container">
    <h3 class="text-center m-5 text-info">Add New Stuff</h3>
    <div class="row justify-content-center">
      <form @submit.prevent="AddNewStuff" class="col-6">
        <div class="form-group">
          <label for="name">Name: </label>
          <input type="text" class="form-control" name="name" v-model="stuff.name" />
        </div>
        <div class="form-group">
          <label for="age">Age: </label>
          <input type="text" class="form-control" name="age" v-model="stuff.age" />
        </div>
        <div class="form-group">
          <label for="gender">Gender: </label>
          <select class="form-control" name="gender" v-model="stuff.gender">
            <option value="male">Male</option>
            <option value="female">Female</option>
            <option value="other">other</option>
          </select>
        </div>
        <div class="form-group">
          <label for="dateOfBirth">Date Of Birth: </label>
          <input type="date" class="form-control" name="dateOfBirth" v-model="stuff.dateOfBirth" />
        </div>
        <button class="btn btn-info">Add New Stuff</button>
      </form>
    </div>

  </div>
</template>

<script>
export default {
  name: "AddStuff",
  data() {
    return {
      stuff: {
        name: null,
        age: null,
        gender: null,
        dateOfBirth: null
      }
    };
  },

  methods: {
    AddNewStuff() {
      let stuffDB = JSON.parse(localStorage.getItem("c_assignment"));
      stuffDB = stuffDB ? stuffDB : [];

      const id = Math.floor(Math.random() * 10000);
      //   const id = Math.floor(Math.random() * (max - min + 1)) + min

      const { name, age, gender, dateOfBirth } = this.stuff;

      const newStuff = {
        id,
        name,
        age,
        gender,
        dateOfBirth
      };

      console.log(id, name, age, gender, dateOfBirth);

      localStorage.setItem(
        "c_assignment",
        JSON.stringify([...stuffDB, newStuff])
      );

      this.stuff = {
        name: "",
        age: "",
        gender: "",
        dateOfBirth: ""
      };
      this.$router.push("/");
    }
  }
};
</script>
