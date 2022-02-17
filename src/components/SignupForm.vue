<template>
    <form id="signup-form" v-on:submit.prevent="submit">
        <div class="row">
            <div class="col-12 form-group justify-content-space-around">
                <label class="col-form-label col-form-label-lg">Email <span class="text-danger">*</span></label>
                <input
                    type="email"
                    v-model.trim="$v.email.$model"
                    :class="{'is-invalid': validationStatus($v.email)}"
                    class="form-control form-control-lg"
                >
                <div v-if="!$v.email.required" class="invalid-feedback">This field is required</div>
                <div v-if="!$v.email.email" class="invalid-feedback">Please enter a valid email address</div>
            </div>

            <div class="col-12 form-group justify-content-space-around">
                <label class="col-form-label col-form-label-lg">Password <span class="text-danger">*</span></label>
                <input
                    type="password"
                    v-model.trim="$v.password.$model"
                    :class="{'is-invalid': validationStatus($v.password)}"
                    class="form-control form-control-lg"
                >
                <div v-if="!$v.password.required" class="invalid-feedback">This field is required</div>
                <div v-if="!$v.password.minLength" class="invalid-feedback">Must be at least {{ $v.password.$params.minLength.min }} characters long</div>
                <div v-if="!$v.password.maxLength" class="invalid-feedback">Must not be longer than {{ $v.password.$params.maxLength.max }} characters</div>
            </div>

            <div class="col-12 form-group justify-content-space-around">
                <label class="col-form-label col-form-label-lg">Username <span class="text-danger">*</span></label>
                <input
                    type="text"
                    v-model.trim="$v.username.$model"
                    :class="{'is-invalid': validationStatus($v.username)}"
                    class="form-control form-control-lg"
                >
                <div v-if="!$v.username.required" class="invalid-feedback">This field is required</div>
            </div>

            <div class="col-12 form-group text-center justify-content-space-around">
                <button class="btn btn-vue btn-lg col-4">Sign Up</button>
            </div>
        </div>
    </form>
</template>
<script>
import { required, email, minLength, maxLength } from 'vuelidate/lib/validators'
export default {
    name: 'SignupForm',
    data: function() {
        return {
            email: '',
            password: '',
            username: '',
        }
    },
    validations: {
        username: { required },
        email: { required, email },
        password: { required, minLength: minLength(6), maxLength: maxLength(12) }
    },

    methods: {
        validationStatus: function(validation) {
            return typeof validation != "undefined" ? validation.$error : false;
        },

        submit: function() {
            this.$v.$touch();

            if (this.$v.$pendding || this.$v.$error) return;
            alert('Data Submit');
        }
    }
}
</script>
<style>
.btn-vue{
    background: #53B985;
    color: #31485D;
    font-weight: bold;
}
</style>