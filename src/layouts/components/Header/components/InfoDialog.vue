<template>
  <el-dialog v-model="dialogVisible" title="个人信息" width="800px" draggable>
    <div class="profile">
      <el-card>
        <h2>账号信息</h2>
        <el-form :model="form" label-position="left" label-width="120px" class="profile-form">
          <el-form-item label="工号">
            <span>{{ form.employeeId }}</span>
          </el-form-item>
          <el-form-item label="姓名">
            <span>{{ form.name }}</span>
          </el-form-item>
          <el-form-item label="邮箱">
            <span>{{ form.email }}</span>
          </el-form-item>
        </el-form>
      </el-card>
      <el-card>
        <h2>更改密码</h2>
        <el-form :model="passwordForm" label-position="left" label-width="120px" class="password-form">
          <el-form-item label="旧密码">
            <el-input placeholder="请输入旧密码" type="password" v-model="passwordForm.oldPassword" prefix-icon="Lock"></el-input>
          </el-form-item>
          <el-form-item label="新密码">
            <el-input placeholder="请输入新密码" type="password" v-model="passwordForm.newPassword" prefix-icon="Lock"></el-input>
          </el-form-item>
          <el-form-item label="确认新密码">
            <el-input
              placeholder="再次输入新密码"
              type="password"
              v-model="passwordForm.newPasswordConfirm"
              prefix-icon="Lock"
            ></el-input>
          </el-form-item>
          <div style="margin-bottom: 50px">
            <span style="color: red">*密码需为8-16位字母和数字组合</span>
          </div>
          <el-button type="primary" @click="submitPassword">更改密码</el-button>
          <el-button type="default" @click="cancel" style="margin-left: 50px">取消</el-button>
        </el-form>
      </el-card>
    </div>
    <!-- <el-button @click="dialogVisible = false">取消</el-button>
        <el-button type="primary" @click="dialogVisible = false">确认</el-button> -->
  </el-dialog>
</template>

<script setup lang="ts">
import { ref } from "vue";

const dialogVisible = ref(false);
const openDialog = () => {
  dialogVisible.value = true;
};
const form = ref({
  employeeId: "0001",
  name: "张三",
  email: "zhangsan@example.com"
});

const passwordForm = ref({
  oldPassword: "",
  newPassword: "",
  newPasswordConfirm: ""
});

const submitPassword = () => {
  // 提交修改密码表单
  const oldPassword = passwordForm.value.oldPassword;
  const newPassword = passwordForm.value.newPassword;
  const newPasswordConfirm = passwordForm.value.newPasswordConfirm;

  // 模拟后端验证旧密码的逻辑
  if (oldPassword !== "123456") {
    // 假设旧密码不匹配时，弹出错误提示
    alert("旧密码错误，请重新输入");
    return;
  }

  // 检查两次输入的新密码是否相同
  if (newPassword !== newPasswordConfirm) {
    // 假设新密码不匹配时，弹出错误提示
    alert("两次输入的新密码不一致，请重新输入");
    return;
  }

  // 如果通过验证，可以继续处理修改密码的逻辑
  // ...

  // 重置密码表单
  passwordForm.value.oldPassword = "";
  passwordForm.value.newPassword = "";
  passwordForm.value.newPasswordConfirm = "";
};
const cancel = () => {
  dialogVisible.value = false;
};

defineExpose({ openDialog });
</script>

<style scoped>
.profile {
  display: flex;
  flex-direction: column;
  gap: 20px;
  padding: 20px;
}
.profile h2 {
  text-align: left;
}
.profile-form {
  max-width: 500px;
}
.password-form {
  max-width: 400px;
}
</style>
