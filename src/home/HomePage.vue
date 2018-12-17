<template>
    <div>
        <!-- Navigation -->
        <nav class="navbar navbar-expand-lg navbar-light bg-light fixed-top" id="mainNav">
            <div class="container">
            <a class="navbar-brand js-scroll-trigger text-primary" href="#page-top">Listy shopping</a>
            <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarResponsive" aria-controls="navbarResponsive" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarResponsive">
                <ul class="navbar-nav ml-auto">
                <li class="nav-item">
                    <a class="nav-link js-scroll-trigger" href="#profile"><router-link to="/profile">Profile</router-link></a>
                </li>
                <li class="nav-item">
                    <a class="nav-link js-scroll-trigger" href="#services"><router-link to="/spendings">Expenses</router-link></a>
                </li>
                <li class="nav-item">
                    <a class="nav-link js-scroll-trigger" href="#services"><router-link to="/login">Logout</router-link></a>
                </li>
                </ul>
            </div>
            </div>
        </nav>
        
        <div class="row" style="margin-top: 30%;">
            <div class="col-md-12">
                <div class="well">
                    <form>
                        <div class="form-group text-success" style="float: left; width: 75%;">
                            <input type="text" v-model="input" class="form-control" id="todoitem" placeholder="Item name" />
                        </div>
                        <button type="button" v-on:click="add()" class="btn btn-outline-primary" style="width: 25%;">Add</button>
                    </form>
                </div>
            </div>
        </div>
        <div class="row" style="margin-top: 30px;">
            <div class="col-md-12">
                <ul class="list-group">
                    <li v-for="(todo, index) in todos" :key="index" class="list-group-item text-primary">
                        {{ todo }}

                        <button type="button" v-on:click="removeElement(todo, index)" class="btn btn-outline-primary btn-sm" style="float: right">Remove</button>
                    
                    </li>
                </ul>
            </div>
        </div>
        <form class="form-inline" style="float: right; margin-bottom: 20%; margin-top: 10%;">
          <div class="form-group">
            <label class="sr-only" for="exampleInputAmount">Amount (in euros)</label>
            <div class="input-group">
              <div class="input-group-prepend">
                <span class="input-group-text">€</span>
              </div>
              <input type="text" class="form-control" id="exampleInputAmount" placeholder="Amount">
            </div>
          </div>
        </form>
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
        } ,
        removeElement(todo, index) {
            this.$delete(this.todos, index);
        }
    }
};
</script>

<style>
#form-group {
    float: left;
    width: 75%;
}
</style>