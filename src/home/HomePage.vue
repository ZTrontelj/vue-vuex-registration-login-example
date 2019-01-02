<template>
    <div>
        <!-- Modal -->
        <div class="modal fade bd-example-modal-lg" id="exampleModalLong" tabindex="-1" role="dialog" aria-labelledby="exampleModalLongTitle" aria-hidden="true">
        <div class="modal-dialog modal-lg" role="document">
            <div class="modal-content">
            <div class="modal-header">
                <h5 class="modal-title" id="exampleModalLongTitle">Please help us with your feedback:)</h5>
                <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                <span aria-hidden="true">&times;</span>
                </button>
            </div>
            <div class="modal-body">
                <iframe src="https://docs.google.com/forms/d/e/1FAIpQLSfL8jGM-Svab7sg3bFZ4PlcAPnFxVCTgowMJiDeDwrprjAEkA/viewform?embedded=true" width="100%" height="1214" frameborder="0" marginheight="0" marginwidth="0">Nalaganje ...</iframe>
            </div>
            <div class="modal-footer">
                <button type="button" class="btn btn-secondary" data-dismiss="modal"><router-link to="/login">Logout</router-link></button>
            </div>
            </div>
        </div>
        </div>
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
                    <a class="nav-link js-scroll-trigger" data-toggle="modal" data-target="#exampleModalLong" >Logout</a>
                </li>
                </ul>
            </div>
            </div>
        </nav>
        <div class="row" style="margin-top: 20%;">
            <div class="col-md-12">
                <div class="well">
                    <form>
                        <button type="button" v-model="common" v-on:click="addBread()" class="btn btn-outline-success" style="width: 25%; float: left;">Bread</button>
                        <button type="button" v-model="common" v-on:click="addEggs()" class="btn btn-outline-success" style="width: 25%; float: left;">Eggs</button>
                        <button type="button" v-model="common" v-on:click="addCheese()" class="btn btn-outline-success" style="width: 25%; float: left;">Cheese</button>
                        <button type="button" v-model="common" v-on:click="addPasta()" class="btn btn-outline-success" style="width: 25%; float: left;">Pasta</button>
                    </form>
                </div>
            </div>
        </div>
        
        <div class="row" style="margin-top: 5%;">
            <div class="col-md-12">
                <div class="well">
                    <form>
                        <div class="form-group text-success" style="float: left; width: 75%;">
                            <input type="text" v-model="input" class="form-control" id="todoitem" placeholder="Write product name and click add" />
                        </div>
                        <button type="button" v-on:click="add()" class="btn btn-outline-primary" style="width: 25%;">Add</button>
                    </form>
                </div>
            </div>
        </div>
        <div class="row" style="margin-top: 30px;">
            <div class="col-md-12">
                <ul class="list-group">
                    <li v-for="(todo, index) in todos" :key="index" class="list-group-item">
                        {{ todo }}

                        <button type="button" v-on:click="removeElement(todo, index)" class="btn btn-outline-danger btn-sm" style="float: right">Remove item</button>
                    
                    </li>
                </ul>
            </div>
        </div>

        <form class="form-inline" style="float: center; margin-top: 10%;">
          <div class="form-group">
            <label class="sr-only" for="exampleInputAmount">Price (in euros)</label>
            <div class="input-group">
              <div class="input-group-prepend">
                <span class="input-group-text">€</span>
              </div>
              <input type="text" class="form-control" id="exampleInputAmount" placeholder="Input price after purchase to track expenses">
            </div>
          </div>
        </form>
        
        <p class="text-success" style="margin-bottom: 20%; float: center;">Price will be used to track expenses</p>
        
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
        addBread() {
            this.todos.push("Bread");
        },
        addEggs() {
            this.todos.push("Eggs");
        },
        addCheese() {
            this.todos.push("Cheese");
        },
        addPasta() {
            this.todos.push("Pasta");
        },
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