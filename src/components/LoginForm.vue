<template>
  <div class="card-front" style="height: 500px; align-items:center;">
    <div class="center-wrap">
      <Form
        :src="Form"
        @submit="login"
        class="section text-center"
        :validation-schema="LoginSchema"
      >
        <h4 class="mb-4 pb-3">ورود</h4>
        <div class="form-group">
          <Field
            :validateOnInput="true"
            name="email"
            type="text"
            class="form-style"
            placeholder="ایمیل خود را وارد کنید"
            autocomplete="off"
          />
          <i class="input-icon uil uil-at"></i>
        </div>
        <p class="text-danger">
          <ErrorMessage name="email" />
        </p>
        <div class="form-group mt-2">
          <Field
            :validateOnInput="true"
            name="password"
            type="password"
            class="form-style"
            placeholder="پسوورد را وارد کنید"
            autocomplete="off"
          />
          <i class="input-icon uil uil-lock-alt"></i>
        </div>
        <p class="text-danger">
          <ErrorMessage name="password" />
        </p>
        <button href="#" class="btn mt-4">کلیک</button>
        <p class="mb-0 mt-4 text-center">
          <a href="#0" class="link">آبا پسوورد خود را فراموش کردید؟</a>
        </p>
      </Form>
    </div>
  </div>
</template>

<script setup>

import { Form, Field, ErrorMessage } from "vee-validate";
import {reactive} from "vue";

// import * as yup from "yup";
import {object , string} from "yup";


// components: {
//     Form,
//     Field,
//     ErrorMessage,
//   },

// LoginFormSchema is an object for validate yup
const LoginFormSchema = object({
      email: 
        string()
        .required("ایمیل خود را وارد کنید")
        .email("ایمیل نامعتبر است"),
      password: 
        string()
        .required("پسوورد را وارد کنید")
        .min(8, "پسوورد باید بیشتر از 7 کاراکتر باشد"),
    });
      const LoginSchema = reactive(LoginFormSchema)
      // email:"",
      // password:"",
      // emailRules: yup
      //   .string()
      //   .required("ایمیل خود را وارد کنید")
      //   .email("ایمیل نامعتبر است"),
      // passwordRules: yup
      //   .string()
      //   .required("پسوورد را وارد کنید")
      //   .min(8, "پسوورد باید بیشتر از 8 کاراکتر باشد"),
    function login(values) {
      console.log(values);
    }
    // validation basics
    // validateEmail(email) {
    //   if (!email) return "ایمیل را وارد کنید";
    //   const regex = /^[A-Z0-9._%+-]+@[A-Z0-9.-]+\.[A-Z]{2,4}$/i;
    //   if (!regex.test(email)) {
    //     return "ایمیل نا معتبر";
    //   }
    //   return true;
    // },
    // validatePassword(password) {
    //   if (!password) return "پسوورد را وارد کنید";
    //   if (password.length < 8) {
    //     return "پسوورد باید بیشتر از 8 کاراکتر باشد";
    //   }
    //   return true;
    // },
</script>

<style>
</style>