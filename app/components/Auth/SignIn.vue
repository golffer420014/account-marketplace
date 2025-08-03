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
    <UCard class=" max-w-md mx-auto mt-10 shadow-lg rounded-2xl">
        <h2 class="text-3xl font-bold text-center mb-6">เข้าสู่ระบบ</h2>

        <!-- ปุ่ม Provider -->
        <div class="space-y-3">
            <UButton block color="neutral" variant="outline" class="cursor-pointer" :avatar="{
                src: 'https://www.svgrepo.com/show/475656/google-color.svg',
            }" @click="signInWithProvider('google')">
                <span>เข้าสู่ระบบด้วย Google</span>
            </UButton>

            <UButton block color="neutral" variant="outline" class="cursor-pointer" :avatar="{
                src: 'https://www.svgrepo.com/show/452196/facebook-1.svg',
            }" @click="signInWithProvider('facebook')">
                <span>เข้าสู่ระบบด้วย Facebook</span>
            </UButton>
        </div>

        <!-- Divider -->
        <USeparator class="my-4" size="xs" />


        <!-- ฟอร์มหลัก -->
        <UForm :state="form" class="space-y-4" @submit="handleSignIn">
            <UFormField label="ชื่อผู้ใช้" name="username">
                <UInput
                    v-model="form.username"
                    class="w-full"
                    icon="i-lucide-user"
                    type="text"
                    placeholder="ชื่อผู้ใช้"
                    required
                />
            </UFormField>

            <UFormField label="รหัสผ่าน" name="password">
                <UInput 
                    v-model="form.password" 
                    class="w-full" 
                    icon="i-lucide-lock-keyhole"
                    :type="togglePasswordVisibility ? 'text' : 'password'"
                    placeholder="รหัสผ่าน" required>
                    <template #trailing>
                        <UButton 
                            color="neutral" 
                            variant="link"
                            size="sm"
                            :icon="togglePasswordVisibility ? 'i-lucide-eye' : 'i-lucide-eye-closed'"
                            :aria-label="show ? 'Hide password' : 'Show password'" 
                            :aria-pressed="show"
                            @click="togglePasswordVisibility = !togglePasswordVisibility"/>
                    </template>
                </UInput>
            </UFormField>

            <UButton type="submit" color="primary" block>เข้าสู่ระบบ</UButton>
        </UForm>
    </UCard>
</template>
