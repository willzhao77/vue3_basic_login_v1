<template>
    <div class="login">
        <el-card class="box-card">
            <template #header>
                <div class="card-header">
                    <span>Register Account</span>
                </div>
            </template>
            <el-form :model="form" label-width="120px" ref="ruleFormRef"
            :rules="rules"
            >
                    <el-form-item label="Name" prop="username">
                        <el-input v-model="form.username" />
                    </el-form-item>
                    <el-form-item label="Password">
                        <el-input v-model="form.password" />
                    </el-form-item>
                    <el-form-item>
                        <el-button type="primary" @click="onSubmit(ruleFormRef)">Create</el-button>
                        <el-button>Cancel</el-button>
                    </el-form-item>
                </el-form>
        </el-card>
    </div>
</template>

<script setup>
import {reactive, ref, getCurrentInstance} from 'vue'
import { ElMessage } from 'element-plus'
import {nameRule} from '../utils/validate.js'
import { setToken } from '@/utils/setToken.js'

const currentInstance = getCurrentInstance()
const { $http} = currentInstance.appContext.config.globalProperties

const ruleFormRef = ref()

const rules = {
    username: [{ validator: nameRule, trigger: 'blur' }],
}

const form = reactive({
    username: '',
    password: ''
})

const onSubmit = async (formEl) => {
  if (!formEl) return
  await formEl.validate((valid, fields) => {
    if (valid) {
      console.log('submit!')
      $http("https://jsonplaceholder.typicode.com/users/1", form)
      .then((res)=> {
        console.log(res)

        // if(res.status === 200) {
        //     //save token to local storage
        //     setToken('username', res.data.username)

        //     ElMessage({
        //         message: 'submitted!!!',
        //         type: 'success',
        //     })
        // }

    }).catch ((err) => {
        console.log('!!', err)
    })
    } else {
      console.log('error submit!', fields)
    }
  })
}

</script>

<style lang="scss" scoped>
.login {
    width: 100%;
    height: 100%;
    position: absolute;
    background: #409eff;
    .box-card {
        width: 450px;
        margin: 200px auto;
    }
}
</style>