<template>
  <div id="app">
    <nav class="navbar navbar-expand-md navbar-light fixed-top bg-light p-2">
      <router-link class="navbar-brand" :to="{name: 'home'}">Factura Electronica</router-link>
      <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarCollapse" aria-controls="navbarCollapse" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarCollapse">
        <ul class="navbar-nav mr-auto">

          <!-- Panel -->
          <li class="nav-item dropdown" v-if="loggedIn">
            <router-link class="nav-link" :to="{name: 'panel'}">Panel</router-link>
          </li>

          <!-- Documentos -->
          <li class="nav-item dropdown" v-if="loggedIn">
            <router-link class="nav-link" :to="{name: 'documentos'}">Documentos</router-link>
          </li>

          <!-- Products -->
          <li class="nav-item dropdown" v-if="loggedIn">
            <router-link class="nav-link" :to="{name: 'productos'}">Productos</router-link>
          </li>

          <!-- Clientes -->
          <li class="nav-item dropdown" v-if="loggedIn">
            <router-link class="nav-link" :to="{name: 'clientes'}">Clientes</router-link>
          </li>
        </ul>
        <ul class="navbar-nav flex-row ml-md-auto d-none d-md-flex">
          <li class="nav-item">
            <a href="/login" v-if="!loggedIn" class="nav-link">Login</a>
          </li>
          <li class="nav-item">
            <a href="/register" v-if="!loggedIn" class="nav-link">Register</a>
          </li>

          <li class="nav-item" v-if="loggedIn">
            <span class="nav-link">{{$store.state.email}}</span>
          </li>

          <!-- Logout -->
          <li class="nav-item" v-if="loggedIn">
            <router-link class="nav-link" :to="{name: 'logout'}">
              <i class="fa fa-lock"></i> Salir
            </router-link>
          </li>
        </ul>
      </div>
    </nav>

    <div class="container" style="padding-top: 60px;">
      <router-view/>
    </div>


  </div>
</template>

<script>
  import axios from 'axios'
  export default {
    data(){
      return {
        token: '',
        // url: window.location.pathname
      }
    },
    computed: {
      loggedIn() {
        return this.$store.getters.loggedIn
      }
    }
  }

</script>
