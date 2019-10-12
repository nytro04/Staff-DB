<template>
  <div class="container">
    <h3 class="text-center m-5 text-info">Edit Stuff</h3>
    <div class="row justify-content-center">
      <form @submit.prevent="UpdateStuff" class="col-6">
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
        <button class="btn btn-info">Save Edit</button>
      </form>
    </div>

  </div>
</template>

<script>
export default {
  name: "EditStuff",
  data() {
    return {
      stuff: null
    };
  },
  created() {
    const stuffDB = JSON.parse(localStorage.getItem("c_assignment"));

    const params = this.$route.params.id;

    stuffDB.map(stuff => {
      if (stuff.id === params) {
        this.stuff = stuff;
      }
    });

    // const newStuff = stuffDB.map(stuff => {
    //   if (stuff.id === params) {
    //     this.stuff = stuff;
    //   }
    //   return stuff;
    // });
  },

  methods: {
    UpdateStuff() {
      const stuffDB = JSON.parse(localStorage.getItem("c_assignment"));
      console.log(stuffDB);

      const params = this.$route.params.id;

      // remove selected item from localstorage
      localStorage.setItem(
        "c_assignment",
        JSON.stringify([
          ...stuffDB.filter(stuff => {
            return stuff.id !== params;
          })
        ])
      );

      const newStuffDB = JSON.parse(localStorage.getItem("c_assignment"));

      // check new array of staff
      console.log(newStuffDB);

      localStorage.setItem(
        "c_assignment",
        JSON.stringify([...newStuffDB, this.stuff])
      );

      const newDDD = JSON.parse(localStorage.getItem("c_assignment"));
      // check new array of staff
      console.log(newDDD);

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
