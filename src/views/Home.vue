<template>
  <div class="container ">
    <div class="m-4 text-right">
      <router-link to="/add-new" class="btn btn-info">Add New <i class="fas fa-plus"></i> </router-link>
    </div>

    <div class="table-responsive">
      <table class="table table-hover">
        <thead>
          <tr>
            <th scope="col">#</th>
            <th scope="col">Name</th>
            <th scope="col">Age</th>
            <th scope="col">Gender</th>
            <th scope="col">Date Of Birth</th>
            <th scope="col">Actions</th>
          </tr>
        </thead>
        <tbody v-for="(stuff,index) in stuffs" :key="stuff.id">
          <tr>
            <th scope="row">{{ index + 1}}</th>
            <td>{{stuff.name}}</td>
            <td>{{stuff.age}}</td>
            <td>{{stuff.gender}}</td>
            <td>{{stuff.dateOfBirth}}</td>

            <div>
              <router-link :to="{name: 'EditStuff', params: {id: stuff.id}}" class="btn btn-warning m-2">Edit <i class="fas fa-pencil-alt"></i> </router-link>
              <button @click="DeleteStuff(stuff.id)" class="btn btn-danger m-2">Delete <i class="fas fa-trash-alt"></i> </button>
            </div>
          </tr>

        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: "home",
  data() {
    return {
      stuffs: JSON.parse(localStorage.getItem("c_assignment"))
    };
  },

  methods: {
    DeleteStuff(id) {
      console.log(id);
      if (
        window.confirm(`Are you sure you want to delete this stuff,
      This action cannot be undone`)
      ) {
        // const stuffs = JSON.parse(localStorage.getItem("c_assignment"));

        localStorage.setItem(
          "c_assignment",
          JSON.stringify([...this.stuffs.filter(stuff => stuff.id !== id)])
        );

        this.stuffs = JSON.parse(localStorage.getItem("c_assignment"));
      }
    }
  },

  components: {}
};
</script>
