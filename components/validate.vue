
import type Input from 'postcss/lib/input';
<template>
    <div>
        <h2>Validate Form</h2>
        <ValidationObserver v-slot="handleSumbit">
        <form @submit.prevent="onSumbit()">
            <ValidationProvider name="Name" rules="required | alpha" v-slot="{errors}"> 
            <div>
                <label >Name</label>
                <input type="text" v-model="form.name"> 
                <span>{{ errors[0] }}</span>
            </div>
            </ValidationProvider>

            <ValidationProvider name="E-Mail" rules="required | email" v-slot="{errors}"> 
            <div>
                <label >Email</label>
                <input type="email" v-model="form.email"> 
                <span>{{ errors[0] }}</span>
            </div>
            </ValidationProvider>

            <ValidationProvider name="Password" rules="required | max:8 | min:4" v-slot="{errors}"> 
            <div>
                <label >Password</label>
                <input type="password" v-model="form.password"> 
                <span>{{ errors[0] }}</span>
            </div>
            </ValidationProvider>

            <ValidationProvider name="Gender" rules="required " v-slot="{errors}"> 
            <div>
                <label >Gender</label>
                <select v-model="form.gender">
                    <option value="male">Male</option>
                    <option value="female">Female</option>
                    <option value="other">Other</option>
                </select>
                <span>{{ errors[0] }}</span>
            </div>
            </ValidationProvider>

            <ValidationProvider name="Accept Terms" rules="required " v-slot="{errors}"> 
            <div>
                <input type="checkbox" v-model="form.acceptTerms"> 
                <label >Accept Terms</label>
                <span>{{ errors[0] }}</span>
            </div>
            </ValidationProvider>

            <input type="submit" text="Submit">
        </form>
    </ValidationObserver>
    </div>
</template>

<script setup>

import { ref } from 'vue';
import { ValidationObserver, ValidationProvider } from 'vee-validate';

const name = ref('');

const email= ref('');
const password=('');
const gender=('');
const acceptTerms=false;

function onSubmit() {
    console.log('Hello');
}
</script>
