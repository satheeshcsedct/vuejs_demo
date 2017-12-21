<template>
  <div id="wrapper">
    <nav class="navbar navbar-default enrollment-header">
      <div class="container">
        <a class="navbar-brand header-title" href="#" >
          <i class="glyphicon glyphicon-time"></i>
          DEP Connect
        </a>
        <ul class="nav navbar-nav">
         <!--  <li><a v-link="'/home'">Home</a></li>
          <li><a v-link="'/time-entries'">Time Entries</a></li> -->
        </ul>
      </div>
    </nav>
    <div class="container">
      <span>Enrollment</span>
      <span class="pull-right">
        <a href="#">
          <span class="glyphicon glyphicon-question-sign"></span>
        </a>
        <span>
    </div>

    <div class="seperator-space">
    </div>

    <div class="container">
      <div class="col-sm-6">
        <router-view></router-view>
      </div>
    </div>
    <footer>
      <div class="col-sm-12 ">
        <a href="#" ><i class="glyphicon glyphicon-time"></i> DEP Connect</a>
      </div>
      <hr>
      <div class="col-sm-4"><i>Copyright @ 2017 Apple Inc All rights reserved</i>
      </div>
       <div class="col-sm-2">Privacy Policy
      </div>
       <div class="col-sm-2">Terms of Use
      </div>
       <div class="col-sm-4">Having Trouble? Submit a Ticket
      </div>
    </footer>
  </div>
</template>

<script>
  import Sidebar from './components/Sidebar.vue'
  
  export default {
    components: { 'sidebar': Sidebar },
    data () {
      return {
        // Start with the same value as our
        // first time entry. Hard-coded for now
        // because we'll use a different approach
        // in the next article anyway
        totalTime: 1.5
      }
    },
    events: {
      // Increment the totalTime value based on the new
      // time entry that is dispatched up
      timeUpdate (timeEntry) {
        this.totalTime += parseFloat(timeEntry.totalTime)
      },
      // Decrement totalTime when a time entry is deleted
      deleteTime (timeEntry) {
        this.totalTime -= parseFloat(timeEntry.totalTime)
      }
    }
  }
</script>

<style>
.enrollment-header{
  background-color: #24292e !important;
  color: white !important;
}
.header-title{
  color: white !important;
}

footer {
  position: fixed;
  bottom: 0;
  width: 100%;
  background-color: #f5f5f5;
  padding: 20px;
}
footer a{
  color: #24292e !important;
}
.seperator-space {
  height: 30px;
  background-color: #f5f5f5;
}
</style>