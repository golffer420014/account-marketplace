<script setup lang="ts">
const form = reactive({
    username: '',
    password: '',
})
const togglePasswordVisibility = ref(false)

const handleSignIn = () => {
    console.log('Sign In:', form)
}

const signInWithProvider = (provider: string) => {
    console.log(`Sign in with ${provider}`)
    // TODO: เชื่อมต่อกับ OAuth (Google / Facebook)
}
</script>

<template>
    <UCard class="max-w-md mx-auto mt-10 p-6 shadow-lg rounded-2xl">
        <h2 class="text-3xl font-bold text-center mb-6 text-gray-800">เข้าสู่ระบบ</h2>

        <!-- ปุ่ม Provider -->
        <div class="space-y-3">
            <UButton block color="white" variant="solid" class="border border-gray-300 text-black hover:bg-gray-50"
                @click="signInWithProvider('google')">
                <template #leading>
                    <img src="https://www.svgrepo.com/show/475656/google-color.svg" class="w-5 h-5" />
                </template>
                เข้าสู่ระบบด้วย Google
            </UButton>

            <UButton block color="white" variant="solid" class="border border-gray-300 text-black hover:bg-gray-50"
                @click="signInWithProvider('facebook')">
                <template #leading>
                    <img src="https://www.svgrepo.com/show/506656/facebook.svg" class="w-5 h-5" />
                </template>
                เข้าสู่ระบบด้วย Facebook
            </UButton>
        </div>

        <!-- Divider -->
        <div class="my-6 text-center relative">
            <div class="absolute inset-0 flex items-center">
                <div class="w-full border-t border-gray-300"></div>
            </div>
            <div class="relative text-sm bg-white px-4 text-gray-500">หรือเข้าสู่ระบบด้วยบัญชี</div>
        </div>

        <!-- ฟอร์มหลัก -->
        <UForm @submit="handleSignIn" :state="form" class="space-y-4">
            <UFormField label="ชื่อผู้ใช้" name="username">
                <UInput v-model="form.username" class="w-full" icon="i-lucide-user" type="text" placeholder="ชื่อผู้ใช้หรืออีเมล" required />
            </UFormField>

            <UFormField label="รหัสผ่าน" name="password">
                <UInput v-model="form.password" class="w-full" icon="i-lucide-lock-keyhole" :type="togglePasswordVisibility ? 'text' : 'password'"
                    placeholder="รหัสผ่าน" required>
                    <template #trailing>
                        <UButton color="neutral" variant="link" size="sm"
                            :icon="togglePasswordVisibility ? 'i-lucide-eye' : 'i-lucide-eye-closed'"
                            @click="togglePasswordVisibility = !togglePasswordVisibility"
                            :aria-label="show ? 'Hide password' : 'Show password'" :aria-pressed="show" />
                    </template>
                </UInput>
            </UFormField>

            <UButton type="submit" color="primary" block>เข้าสู่ระบบ</UButton>
        </UForm>
    </UCard>
</template>
