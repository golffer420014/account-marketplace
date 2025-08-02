<script setup lang="ts">
const form = reactive({
    username: '',
    email: '',
    password: '',
})

const handleSignUp = () => {
    // TODO: เชื่อมต่อ backend หรือ auth logic
    console.log('Sign Up:', form)
}
</script>

<template>
    <UCard class="max-w-md mx-auto mt-10 p-6">
        <h2 class="text-2xl font-bold mb-4">สมัครสมาชิก</h2>

        <UForm @submit="handleSignUp" :state="form" class="space-y-4">
            <UFormGroup label="ชื่อผู้ใช้" name="username">
                <UInput v-model="form.username" required />
            </UFormGroup>

            <UFormGroup label="อีเมล" name="email">
                <UInput v-model="form.email" type="email" required />
            </UFormGroup>

            <UFormGroup label="รหัสผ่าน" name="password">
                <UInput v-model="form.password" type="password" required />
            </UFormGroup>

            <UButton type="submit" color="primary" block>สมัครสมาชิก</UButton>
        </UForm>
    </UCard>
</template>
