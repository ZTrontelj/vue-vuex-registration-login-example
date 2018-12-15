<template>
    <div>
        <!-- Navigation -->
        <nav class="navbar navbar-expand-lg navbar-dark bg-dark fixed-top" id="mainNav">
            <div class="container">
            <a class="navbar-brand js-scroll-trigger" href="#page-top">Listy shopping</a>
            <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarResponsive" aria-controls="navbarResponsive" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarResponsive">
                <ul class="navbar-nav ml-auto">
                <li class="nav-item">
                    <a class="nav-link js-scroll-trigger" href="#profile"><router-link to="/profile">Profile</router-link></a>
                </li>
                <li class="nav-item">
                    <a class="nav-link js-scroll-trigger" href="#services"><router-link to="/login">Logout</router-link></a>
                </li>
                </ul>
            </div>
            </div>
        </nav>
        
        <div class="row" style="margin-top: 100px;">
            <div class="col-md-12">
                <div class="well">
                    <h2>Hi <b>{{account.user.firstName}} {{account.user.lastName}}</b> welcome to your LISTY shopping list!</h2>
                    <form>
                        <div class="form-group">
                            <label for="todoitem">Add item</label>
                            <input type="text" v-model="input" class="form-control" id="todoitem" placeholder="Item name" />
                        </div>
                        <button type="button" v-on:click="add()" class="btn btn-default">Add</button>
                    </form>
                </div>
            </div>
        </div>
        <div class="row" style="margin-top: 30px;">
            <div class="col-md-12">
                <ul class="list-group">
                    <li v-for="(todo, index) in todos" :key="index" class="list-group-item" style="background-color: #f3f3f3;">
                        {{ todo }}
                    </li>
                </ul>
            </div>
        </div>
    </div>
</template>

<script>
import { mapState, mapActions } from 'vuex'

export default {
    name: "Todo",
        data () {
            return {
                todos: [],
                input: ""
            }
        },
    computed: {
        ...mapState({
            account: state => state.account,
            users: state => state.users.all
        })
    },
    created () {
        this.getAllUsers();
    },
    methods: {
        ...mapActions('users', {
            getAllUsers: 'getAll',
            deleteUser: 'delete'
        }),
        add() {
                this.todos.push(this.input);
                this.input = "";
            }
    }
};
</script>