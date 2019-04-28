<template>
<<<<<<< HEAD
<div id="app">
	<h1>
		<img src="./assets/logo.svg" alt="Enroller" class="logo"> System
		do zapisów na zajęcia
	</h1>
	<div v-if="authenticatedUsername">
		<h2>
			Witaj {{ authenticatedUsername }}! <a @click="logout()"
				class="float-right  button-outline button">Wyloguj</a>
		</h2>
		<meetings-page :username="authenticatedUsername"></meetings-page>
	</div>
	<div v-else>
		<button @click="registering = false"
			:class="!registering ? '' : 'button-outline'">Loguje si�</button>
		<button @click="registering = true"
			:class="registering ? '' : 'button-outline'">Rejestruje si�
		</button>
		<login-form v-if="!registering" @login="login($event)"></login-form>
		<login-form v-else button-label="Zarejestruj si�"
			@login="register($event)"></login-form>
	</div>
</div>
=======
  <div id="app">
    <h1>
      <img src="./assets/logo.svg" alt="Enroller" class="logo">
      System do zapisów na zajęcia
    </h1>
    <div v-if="authenticatedUsername">
      <h2>Witaj {{ authenticatedUsername }}!
        <a @click="logout()" class="float-right  button-outline button">Wyloguj</a>
      </h2>
      <meetings-page :username="authenticatedUsername"></meetings-page>
    </div>
    <div v-else>
      <button @click="registering = false" :class="registering ? 'button-outline' : ''">Loguję się</button>
      <button @click="registering = true" :class="!registering ? 'button-outline' : ''">Rejestruję się</button>
      <div :class="'alert alert-' + (this.isError ? 'error' : 'success')" v-if="message">{{ message }}</div>
      <login-form @submit="registering ? register($event) : login($event)" :button-label="loginButtonLabel"></login-form>
    </div>
  </div>
>>>>>>> rejestracja
</template>

<script>
    import "milligram";
    import LoginForm from "./LoginForm";
    import MeetingsPage from "./meetings/MeetingsPage";

    export default {
        components: {LoginForm, MeetingsPage},
        data() {
            return {
                authenticatedUsername: "",
<<<<<<< HEAD
                	registering : false
=======
                registering: false,
                message: '',
                isError: false
>>>>>>> rejestracja
            };
        },
        methods: {
            register(user) {
                this.clearMessage();
                this.$http.post('participants', user)
                    .then(() => {
                        this.success('Konto zostało założone. Możesz się zalogować.');
                        this.registering = false;
                    })
                    .catch(response => this.failure('Błąd przy zakładaniu konta. Kod odpowiedzi: ' + response.status));
            },
            login(user) {
                this.clearMessage();
                this.authenticatedUsername = user.login;
            },
            logout() {
                this.authenticatedUsername = '';
            },
<<<<<<< HEAD
            register(user) {
            	 this.$http.post('participants', user)
            	     .then(response => {
            	         alert('uda�o si�');
            	     })
            	     .catch(response => {
            	         alert('nie uda�o sie');     
            	     });
            	}
=======
            success(message) {
                this.message = message;
                this.isError = false;
            },
            failure(message) {
                this.message = message;
                this.isError = true;
            },
            clearMessage() {
                this.message = undefined;
            }
        },
        computed: {
            loginButtonLabel() {
                return this.registering ? 'Zarejestruj się' : 'Zaloguj się';
            }
>>>>>>> rejestracja
        }
    };
</script>

<<<<<<< HEAD
<style>
#app {
	max-width: 1000px;
	margin: 0 auto;
}

.logo {
	vertical-align: middle;
}
=======
<style lang="scss">
  #app {
    max-width: 1000px;
    margin: 0 auto;
  }

  .logo {
    vertical-align: middle;
  }

  .alert {
    padding: 10px;
    margin-bottom: 10px;
    border: 2px solid black;
    &-success {
      background: lightgreen;
      border-color: darken(lightgreen, 10%);
    }
    &-error {
      background: indianred;
      border-color: darken(indianred, 10%);
      color: white;
    }
  }

>>>>>>> rejestracja
</style>

