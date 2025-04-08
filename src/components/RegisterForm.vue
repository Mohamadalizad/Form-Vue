<template>
  <div class="card-back" style="height: 500px; align-items:center;">
    <div class="center-wrap">
      <Form
        @submit="register"
        class="section text-center"
        :validation-schema="registerSchema"
        :initialValues="formData"
      >
        <h4 class="mb-4 pb-3">ثبت نام</h4>
        <div class="row">
          <div class="col-md-6">
            <div class="form-group">
              <Field
                :validateOnInput="true"
                name="name"
                type="text"
                class="form-style"
                placeholder="نام و نام خانوادگی را وارد کنید"
                id="logname"
                autocomplete="off"
              />
              <i class="input-icon uil uil-user"></i>
            </div>
            <p class="text-danger">
              <ErrorMessage name="name" />
            </p>
          </div>
          <div class="col-md-6">
            <div class="form-group">
              <Field
                :validateOnInput="true"
                name="email"
                type="email"
                class="form-style"
                placeholder="ایمیل خود ر وارد کنید"
                id="logemail"
                autocomplete="off"
              />
              <i class="input-icon uil uil-at"></i>
            </div>
            <p class="text-danger">
              <ErrorMessage name="email" />
            </p>
          </div>
          <div class="col-md-6">
            <div class="form-group mt-2">
              <Field
                :validateOnInput="true"
                name="password"
                type="password"
                class="form-style"
                placeholder="پسوورد خود را وارد کنید"
                id="logpass"
                autocomplete="off"
              />
              <i class="input-icon uil uil-lock-alt"></i>
            </div>
            <p class="text-danger">
              <ErrorMessage name="password" />
            </p>
          </div>
          <div class="col-md-6">
            <div class="form-group mt-2">
              <Field
                :validateOnInput="true"
                name="confirmPassword"
                type="password"
                class="form-style"
                placeholder="دوباره پسوورد خود را وارد کنید"
                id="logpass"
                autocomplete="off"
              />
              <i class="input-icon uil uil-lock-alt"></i>
            </div>
            <p class="text-danger">
              <ErrorMessage name="confirmPassword" />
            </p>
          </div>
          <div class="col-md-6">
            <div class="form-group mt-2">
              <Field
                :validateOnInput="true"
                name="phoneNumber"
                type="tel"
                class="form-style"
                placeholder="شماره تلفن خود را وارد کنید"
                id="logpass"
                autocomplete="off"
              />
              <i class="input-icon uil uil-phone"></i>
            </div>
            <p class="text-danger">
              <ErrorMessage name="phoneNumber" />
            </p>
          </div>
          <div class="col-md-6">
            <div class="form-group mt-2">
              <Field
                :validateOnInput="true"
                as="select"
                name="role"
                class="form-style"
                style="cursor: pointer"
                id="category"
              >
                <option value="">نقش خود را وارد کنید</option>
                <option value="user">کاربر</option>
                <option value="student">دانشجو</option>
                <option value="teacher">مدرس</option>
              </Field>
              <i class="input-icon uil uil-ruler"></i>
            </div>
            <p class="text-danger">
              <ErrorMessage name="role" />
            </p>
          </div>
          <div class="col-md-6">
            <div class="form-group mt-3 gap-2 d-flex text-start">
              <label for="1">نامشخص</label>
              <Field type="radio" name="gender" value="نامشخص" id="1" />
              <label for="2">آقا</label>
              <Field name="gender" type="radio" value="آقا" id="2" />
              <label for="3">خانم</label>
              <Field name="gender" type="radio" value="خانم" id="3" />
            </div>
          </div>
        </div>
        <button href="#" class="btn mt-4">کلیک</button>
      </Form>
    </div>
  </div>
</template>

<script setup>
import { Form, Field, ErrorMessage} from "vee-validate";
import { reactive } from "vue";
import { object, string, ref } from "yup";

// LoginFormSchema is an object for validate yup
    const registerFormSchema = object({
      name: string().required(),
      email: string().required().email(),
      phoneNumber: string().required().min(11).max(11),
      password: string().required().min(8),
      confirmPassword: string().required().oneOf(
        [ref("password"), null],
         "Passwords must match"),
      role: string().required(),
    });
      
      // registerSchema is a reactive
      const registerSchema = reactive(registerFormSchema)
      const formData = reactive({
        gender: "نامشخص",
        role: "user",
      })
      
    function register(values) {
      console.log(values);
    }
    
</script>

<style>
</style>