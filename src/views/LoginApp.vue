<template>
  <div class="d-flex align-items-center bg-auth border-top border-top-2 border-primary" style="height: 100%; !important">
    <div class="container">
      <div class="row justify-content-center">
        <div class="col-12 col-md-5 col-xl-4 my-5">

          <!-- Heading -->
          <h1 class="display-4 text-center mb-3">
            Iniciar Sesión
          </h1>

          <!-- Subheading -->
          <p class="text-muted text-center mb-5">
            Panel administrativo
          </p>

          <!-- Form -->
          <form>
            <div v-if="msm_error" class="alert alert-danger" roles="alert">
              {{ msm_error }}
            </div>
            <!-- Email address -->
            <div class="form-group">

              <!-- Label -->
              <label class="form-label">
                Correo electrónico
              </label>

              <!-- Input -->
              <input type="email" class="form-control" v-model="email" placeholder="Ingrese su correo electrónico...">

            </div>

            <!-- Password -->
            <div class="form-group">
              <div class="row">
                <div class="col">

                  <!-- Label -->
                  <label class="form-label">
                    Contraseña
                  </label>

                </div>
              </div> <!-- / .row -->

              <!-- Input group -->
              <div class="input-group input-group-merge">

                <!-- Input -->
                <input class="form-control" v-model="password" type="password" placeholder="Ingrese su contraseña...">

                <!-- Icon -->
                <span class="input-group-text">
                  <i class="fe fe-eye"></i>
                </span>

              </div>
            </div>

            <!-- Submit -->
            <button class="btn btn-lg w-100 btn-primary mb-3" type="button" v-on:click="validar()">
              Iniciar Sesión
            </button>


          </form>

        </div>
      </div> <!-- / .row -->
    </div> <!-- / .container -->
  </div>
</template>
  
<script>
import axios from 'axios';
import store from '@/store/index';
import Swal from 'sweetalert2';

export default {
  name: 'LoginApp',
  data() {
    return {
      email: '',
      password: '',
      msm_error: ''
    }
  },
  created() {
    console.log(this.$url);
  },
  methods: {
    validar() {
      if (!this.email) {
        Swal.fire({
          title: 'Ingrese un correo electrónico',
          icon: 'error'
        });
      } else if (!this.password) {
        Swal.fire({
          title: 'Ingrese una contraseña',
          icon: 'error'
        });
      } else {
        this.msm_error = '';
        this.login();
      }
    },

    login() {
      let data = {
        email: this.email,
        password: this.password
      }

      if (!this.email || !this.password) {
        Swal.fire({
          icon: 'error',
          title: 'Error',
          text: 'Por favor, rellena todos los campos.',
        });
        return;
      }

      axios.post(this.$url + '/login_usuario', data, {
        headers: {
          'Content-Type': 'application/json'
        }
      }).then((result) => {
        if (result.data.data == undefined) {
          this.msm_error = result.data.message;
          Swal.fire({
            icon: 'error',
            title: 'Error',
            text: this.msm_error,
          });
        }
        if (result.data.token) {
          this.$store.dispatch('saveToken', result.data.token);
          this.$router.push({ name: 'dashboard' });
          Swal.fire({
            icon: 'success',
            title: 'Éxito',
            text: 'Has iniciado sesión correctamente.',
          });
        }
      }).catch((error) => {
        console.log(error);
        Swal.fire({
          icon: 'error',
          title: 'Error',
          text: 'Ha ocurrido un error al iniciar sesión.',
        });
      });
    },
    logout() {
      this.$store.dispatch('logout');
      Swal.fire({
        icon: 'success',
        title: 'Éxito',
        text: 'Has cerrado sesión correctamente.',
      });
    }
  },
  components: {
  }
}
</script>
  