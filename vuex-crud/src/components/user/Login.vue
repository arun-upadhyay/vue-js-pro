<template>
    <div v-show="!$store.getters.isAuthenticated" class="login" v-cloak>

        <form @submit.prevent="login">
            <div class="form-group">
                <label>Username</label>
                <input type="username"
                       id="input-username"
                       class="form-control" placeholder="Enter username" v-model="username">
                <small id="usernameHelp" class="form-text text-muted">We'll never share your username with anyone
                    else.</small>
            </div>
            <div class="form-group">
                <label>Password</label>
                <input type="password" id="input-password" class="form-control" placeholder="Password"
                       v-model="password">
            </div>
            <button type="submit" class="btn btn-primary" style="margin-right: 20px">Submit</button>
            <button type="button" class="btn btn-primary" @click="register">Register</button>
        </form>
        <div v-if="errors.length" class="error-div">
            <b>Please correct the following errors</b>
            <ul>
                <li :key="error.id" v-for="error in errors" class="error.id">{{error.text}}</li>
            </ul>
        </div>
    </div>
</template>

<script>
    export default {
        name: "Login",
        data() {
            return {
                username: '',
                password: '',
                errors: []
            }
        },
        created() {
            if (localStorage.getItem('token')) {
                this.$store.state.token = localStorage.getItem('token');
                this.$store.state.isAuthenticated = true;
                this.$router.push({name: 'posts'})
            }
            if (this.$store.state.isAuthenticated === true) {
                this.$router.push({name: 'posts'})
            }
        },
        methods: {
            login: function (event) {
                this.validation();
                // validate form.
                if (this.errors.length !== 0) {
                    return false;
                }
                event.preventDefault();
                this.$store.dispatch(('findUser'), {
                    username: this.username,
                    password: this.password
                }).then(() => {
                    this.$router.push({name: 'posts'})
                }).catch(err => {
                    this.errors.push({id: 'error1', text: 'Invalid username or password.'});
                    console.log(err);
                });
            },
            register: function () {
                this.$router.push({name: 'register'})
            },
            validation: function () {
                this.errors = [];
                if (!this.username) {
                    this.errors.push({id: 'error1', text: 'Username required.'});
                }
                if (!this.password) {
                    this.errors.push({id: 'error2', text: 'Password required.'});
                }
            }

        }
    }
</script>

<style scoped lang="scss">
    .login {
        margin: 30px;
    }

    .error-div ul li {
        color: red;
    }

    [v-cloak] {
        display: none
    }

</style>