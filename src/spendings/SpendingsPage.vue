<template>
    <div style="margin-bottom: 10%;">
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
                    <a class="nav-link js-scroll-trigger" href="#services"><router-link to="/home">Home</router-link></a>
                </li>
                <li class="nav-item">
                    <a class="nav-link js-scroll-trigger" href="#services"><router-link to="/profile">Profile</router-link></a>
                </li>
                <li class="nav-item">
                    <a class="nav-link js-scroll-trigger" href="#services"><router-link to="/login">Logout</router-link></a>
                </li>
                </ul>
            </div>
            </div>
        </nav>
        
        <div class="row" style="margin-top: 100px; text-align: center;">
            <div class="col-md-12">
                <div class="well">
                    <div class="card">
                      <img src="src/img/graph1.jpg" alt="Spendings" style="width:100%">
                    </div> 
                </div>
            </div>
        </div>
    
    </div>

</template>

<script>
import { mapState, mapActions } from 'vuex'

export default {
    computed: {
        ...mapState({
            account: state => state.account,
            users: state => state.users.all
        })
    }
};

</script>

<style>

</style>