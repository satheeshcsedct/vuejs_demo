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
      <div class="col-sm-3">
        <sidebar :time="totalTime"></sidebar>
      </div>
      <div class="col-sm-9">
        <router-view></router-view>
      </div>
    </div>
    <footer>
      <a class="navbar-brand footer-title" href="#" >
          <i class="glyphicon glyphicon-time"></i>
          DEP Connect
        </a>
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
  position: absolute;
  bottom: 0;
  width: 100%;
  height: 60px;
  background-color: #f5f5f5;
}
footer a{
  color: #24292e !important;
}
</style>