<template>
    <form id="signup form">
        <div class="row">
            <div class="col-12 form-group">
                <label class="col-form-label col-form-label-lg">Email <span class="text-danger">*</span></label>
                <input type="text" class="form-control form-control-lg">
            </div>

            <div class="col-12 form-group">
                <label class="col-form-label col-form-label-lg">Password <span class="text-danger">*</span></label>
                <input type="text" class="form-control form-control-lg">
            </div>

            <div class="col-12 form-group text-center">
                <button class="btn btn-vue btn-lg col-4">Signup</button>
            </div>
        </div>
    </form>
</template>
<script>
export default {
    name: 'SignupForm'
}
</script>
<style>
.btn-vue{
    background: #53B985;
    color: #31485D;
    font-weight: bold;
}
</style>