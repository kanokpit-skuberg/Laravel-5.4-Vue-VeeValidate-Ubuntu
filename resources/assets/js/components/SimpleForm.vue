<template>
    <form @submit.prevent="validateBeforeSubmit">
        <div class="form-group">
            <label class="col-md-4 control-label text-right">Email&nbsp;:</label>
            <div class="col-md-8">
                <input name="email" v-validate.initial="'required|email'" data-vv-delay="300" :class="{'form-control': true, 'is-danger': errors.has('email') }" type="text" placeholder="Email">
                <div v-show="errors.has('email')" class="help is-danger">{{ errors.first('email') }}</div>
            </div>
        </div>
        <div class="clearfix"></div>
        <div class="form-group">
            <label class="col-md-4 control-label text-right">First Name&nbsp;:</label>
            <div class="col-md-8">
                <input name="first_name" v-model="first_name" data-vv-delay="300" v-validate.initial="'required|alpha'" :class="{'form-control': true, 'is-danger': errors.has('first_name') }" type="text" placeholder="First Name">
                <div v-show="errors.has('first_name')" class="help is-danger">{{ errors.first('first_name') }}</div>
            </div>
        </div>
        <div class="clearfix"></div>
        <div class="form-group">
            <label class="col-md-4 control-label text-right">Last Name&nbsp;:</label>
            <div class="col-md-8">
                <input name="last_name" v-model="last_name" data-vv-delay="300" v-validate.initial="'required|alpha'" :class="{'form-control': true, 'is-danger': errors.has('last_name') }" type="text" placeholder="Last Name">
                <div v-show="errors.has('last_name')" class="help is-danger">{{ errors.first('last_name') }}</div>
            </div>
        </div>
        <div class="clearfix"></div>
        <div class="form-group">
            <label class="col-md-4 control-label text-right">Full Name&nbsp;:</label>
            <div class="col-md-8">
                <input disabled :value="full_name" name="full_name" data-vv-delay="300" v-validate:full_name.initial="'required|alpha_spaces'" :class="{'form-control': true, 'is-danger': errors.has('full_name') }" type="text" placeholder="Full Name">
                <div v-show="errors.has('full_name')" class="help is-danger">{{ errors.first('full_name') }}</div>
            </div>
        </div>
        <div class="clearfix"></div>
        <div class="form-group">
            <button type="submit" class="btn btn-lg btn-block btn-success">Submit</button>
        </div>
    </form>
</template>

<script>
    export default {
        name: 'form-example',
        data: () => ({
            email: '',
            first_name: '',
            last_name: ''
        }),
        methods: {
            validateBeforeSubmit() {
                this.$validator.validateAll().then(() => {
                    alert('From Submitted!');
                }).catch(() => {
                    alert('Correct them errors!');
                });
            }
        },
        computed: {
            full_name() {
                return `${this.first_name} ${this.last_name}`;
            }
        }
    };
</script>
