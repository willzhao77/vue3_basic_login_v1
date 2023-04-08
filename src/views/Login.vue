<template>
    <div class="login">
        <el-card class="box-card">
            <template #header>
                <div class="card-header">
                    <span>Register Account</span>
                </div>
            </template>
            <el-form :model="form" label-width="120px">
                    <el-form-item label="Name">
                        <el-input v-model="form.name" />
                    </el-form-item>
                    <el-form-item label="Password">
                        <el-input v-model="form.password" />
                    </el-form-item>
                    <el-form-item>
                        <el-button type="primary" @click="onSubmit">Create</el-button>
                        <el-button>Cancel</el-button>
                    </el-form-item>
                </el-form>
        </el-card>
    </div>
</template>

<script setup>
import {reactive} from 'vue'

const form = reactive([])

function onSubmit () {
    console.log('submit', form)
}
</script>

<style lang="scss" scoped>
</style>