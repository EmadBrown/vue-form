<template>
    <div>
        <div class="form-group">
            <label for="firstName">First Name</label>
            <input type="text" class="form-control" id="firstName" aria-describedby="firstNameHelp" placeholder="First Name" :value="firstName" @input="createFullName(true, $event)">
            <small id="firstNameHelp" class="form-text text-muted">We'll never share your first name with anyone else.</small>
        </div>

        <div class="form-group">
            <label for="lastName">Last Name</label>
            <input type="text" class="form-control" id="lastName" aria-describedby="lastNameHelp" placeholder="Last Name" :value="lastName" @input="createFullName(false, $event)">
            <small id="lastNameHelp" class="form-text text-muted">We'll never share your last name with anyone else.</small>
        </div>
    </div>
</template>

<script>
export default {
  data() {
    return {};
  },
  props: {
    value: { default: "" }
  },
  methods: {
    createFullName(isFirst, event) {
      let fullName = "";
      if (isFirst) {
        fullName = event.target.value + " " + this.lastName;
      } else {
        fullName = this.firstName + " " + event.target.value;
      }
      this.value = fullName;
      this.$emit("input", this.value);
    }
  },
  computed: {
    firstName() {
      return this.value.split(" ")[0];
    },
     lastName() {
      return this.value.split(" ")[1];
    }
  }
};
</script>