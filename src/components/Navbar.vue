<template>
  <nav class="navbar navbar-expand-lg navbar-light bg-light">
    <router-link class="navbar-brand" to="/">CA</router-link>
    <button type="button" class="navbar-toggler" data-toggle="collapse" data-target="#assignmentOne">
      <span class="navbar-toggler-icon"></span>
    </button>

    <div class="collapse navbar-collapse" id="assignmentOne">
      <ul class="navbar-nav ml-auto">
        <li class="nav-item">
          <router-link to="/services" class="nav-link text-info">Services</router-link>
        </li>
        <li class="nav-item">
          <router-link to="/about" class="nav-link text-info">About</router-link>
        </li>
        <li class="nav-item">
          <router-link to="/contact" class="nav-link text-info">Contact</router-link>
        </li>
      </ul>
    </div>
  </nav>
</template>

<script>
export default {
  name: "Navbar"
};
</script>
