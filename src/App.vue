<template>
    <div class="container">
        <form>
            <div class="row" v-if="submitted">
                <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                    <!-- Exercise 1 -->
                    <!-- Create a Signup Form where you retrieve the following Information -->
                    <!-- Full Name (First Name + Last Name) -->
                    <!-- Mail -->
                    <!-- Password -->
                    <!-- Store Data? Yes/No -->

                    <!-- Exercise 2 -->
                    <!-- Only display the Form if it has NOT been submitted -->
                    <!-- Display the Data Summary ONCE the Form HAS been submitted -->

                    <!-- Exercise 3 -->
                    <!-- Edit the Example from above and create a custom "Full Name" Control -->
                    <!-- which still holds the First Name and Last Name Input Field -->
                   
                    <app-full-name v-model="fullName"></app-full-name>
                    <div class="form-group">
                        <label for="email">Email address</label>
                        <input type="email" class="form-control" id="email" aria-describedby="emailHelp" placeholder="Enter email" v-model="userData.email">
                        <small id="emailHelp" class="form-text text-muted">We'll never share your email with anyone else.</small>
                    </div>
                    <div class="form-group">
                        <label for="password">Password</label>
                        <input type="password" class="form-control" id="password" placeholder="Password" v-model="userData.password">
                    </div>
                    <div class="form-group form-check">
                         <label class="form-check-label" for="exampleCheck1">Store Data?</label>
                        <div class="form-check form-check-inline">
                            <input class="form-check-input" type="radio" name="storeData" id="inlineRadio1" value="no" v-model="storeData">
                            <label class="form-check-label" for="inlineRadio1">No</label>
                        </div>
                        <div class="form-check form-check-inline">
                            <input class="form-check-input" type="radio" name="storeData" id="inlineRadio2" value="yes" v-model="storeData">
                            <label class="form-check-label" for="inlineRadio2">Yes</label>
                        </div>
                    </div>
                    <button type="submit" class="btn btn-primary" @click.prevent="displayForm">Submit</button>
                </div>
            </div>
        </form>
        <hr>
        <div class="row" v-if="!submitted">
            <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                <div class="panel panel-default">
                    <div class="panel-heading">
                        <h4>Your Data</h4>
                    </div>
                    <div class="panel-body">
                        <p>Full Name: {{fullName}}</p>
                        <p>Mail: {{userData.email}}</p>
                        <p>Password: {{userData.password}}</p>
                        <p>Store in Database?: {{storeData}} </p>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import FullName from "./components/FullName.vue";
export default {
  data() {
    return {
      userData: {
        password: "",
        email: ""
      },
      fullName: "",
      storeData: "no",
      submitted: true
    };
  },
  components: {
    appFullName: FullName
  },
  methods: {
    displayForm() {
      this.submitted = false;
    }
  },
};
</script>

<style>
</style>
