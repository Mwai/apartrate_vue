<template lang="html">
  <div class="Login__Wrapper">
    <md-card class="Login__CardWrappper">
      <md-card-media class="Login__CardImage">
        <img src="../../assets/img/logo.png" alt="Apartrate" width="200" height="200">
      </md-card-media>

      <md-card-content>
        <md-input-container :class="{'md-input-invalid': errors.has('email')}">
          <label>Email</label>
          <md-input type="email"
            name="email"
            v-model="user"
            v-validate
            data-vv-name="email"
            data-vv-rules="required|email"></md-input>
          <span class="md-error"></span>
        </md-input-container>

        <!--<md-input-container :class="{'md-input-invalid': errors.has('cnpj')}">-->
          <!--<label>Email</label>-->
          <!--<md-input type="text"-->
            <!--name="cnpj"-->
            <!--v-model="cnpj"-->
            <!--v-cnpj-->
            <!--v-validate-->
            <!--data-vv-name="cnpj"-->
            <!--data-vv-rules="required|cnpj"></md-input>-->
          <!--<span class="md-error"></span>-->
        <!--</md-input-container>-->

        <md-input-container>
          <label>Password</label>
          <md-input type="password"
            v-model="password"></md-input>
        </md-input-container>

      </md-card-content>

      <md-card-actions>
        <md-button>Forgot password</md-button>
        <md-button class="md-raised md-primary"
          @click.stop="login">
          Login
        </md-button>
      </md-card-actions>
    </md-card>
  </div>
</template>

<script type="text/javascript">
  export default {
    data () {
      return {
        user: '',
        cnpj: '',
        password: ''
      }
    },
    components: {
    },
    computed: {
      cnpjError () {
        // Exemplo de computed properties
        return (this.errors) ? this.errors.first('cnpj') : ''
      },
      emailError () {
        // Exemplo de computed properties
        return (this.errors) ? this.errors.first('email') : ''
      }
    },
    methods: {
      login () {
        this.$router.push({ path: '/post-login' })
      }
    }
  }
</script>

<style lang="scss" scoped>
  .Login__Wrapper {
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .Login__CardWrappper {
    margin-top: 20vh;
    min-width: 300px;
    width: 22%;
  }

  .Login__CardImage {
    display: flex;
    justify-content: center;
    img {
      max-width: 200px;
      max-height: 150px;
    }
  }
</style>
