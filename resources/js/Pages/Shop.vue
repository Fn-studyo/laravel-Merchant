<template>
    <div>
        <app-layout>
            <div class=" flex w-full">
            <Sidebar/>
              <div class="main mx-9 container">
                  <h4 class="my-8">Create a new shop</h4>

                   <jet-validation-errors class="mb-4" />
                    <form  @submit.prevent="submit">                  
                        <div class="mt-4">
                            <jet-label for="name" value="Name" />
                            <jet-input id="name" type="text" class="mt-1 block" v-model="form.name" required />
                        </div>
                        <div class="mt-4">
                            <jet-label for="address" value="Address" />
                            <jet-input id="address" type="text" class="mt-1 block" v-model="form.address" required />
                        </div>
                        <div class="mt-4">
                            <jet-label for="phone" value="Phone" />
                            <jet-input id="phone" type="number" class="mt-1 block" v-model="form.phone" required />
                        </div>
                        <div class="mt-4">
                            <jet-label for="twitter" value="Twitter" />
                            <jet-input id="twitter" type="text" class="mt-1 block" v-model="form.social_media.twitter" required />
                        </div>
                        <div class="mt-4">
                            <jet-label for="facebook" value="Facebook Link" />
                            <jet-input id="facebook" type="text" class="mt-1 block" v-model="form.social_media.facebook" required />
                        </div>
                        <div class="mt-4">
                            <jet-label for="instagram" value="Instagram" />
                            <jet-input id="instagram" type="text" class="mt-1 block" v-model="form.social_media.instagram" required />
                        </div>
                        <div class="mt-4">
                            <jet-label for="description" value="Description" />
                            <textarea v-model.trim="form.description" rows="10" cols="82" id="description" class="border-gray-300 focus:border-indigo-300 focus:ring focus:ring-indigo-200 focus:ring-opacity-50 rounded-md shadow-sm">
                                
                            </textarea>
                        </div>
                        <jet-button class="mt-4" :class="{ 'opacity-25': form.processing }" :disabled="form.processing">
                            Create A Shop
                        </jet-button>
                    </form>
                </div>
            <ProductBox/>
            </div>

        </app-layout>
    </div>
</template>
<style scoped>
h4{
    font-weight: bold;
    font-size:20px;
}
input[type = 'text'], input[type = 'number']{
    width:700px;
}
</style>
<script>
import Sidebar from '@/Components/Sidebar.vue'
import JetInput from '@/Jetstream/Input'
import JetButton from '@/Jetstream/Button'
import JetLabel from '@/Jetstream/Label'
import AppLayout from '../Layouts/AppLayout.vue'
import JetValidationErrors from '@/Jetstream/ValidationErrors'

export default {
    name : 'Shop',
    data(){
        return {
            form :this.$inertia.form({
                name : '',
                address: '',
                phone: '',
                description: '',
                social_media: {
                    instagram : '',
                    facebook: '',
                    twitter: ''
                }
            })
        }
    },
    components : {
        AppLayout,
        JetInput,
        JetButton,
        JetValidationErrors,
        JetLabel,
        Sidebar
    },
    methods : {
        submit(){
            this.form.post(this.route('shop.create'), {
                onFinish:() => alert('saved shop')
                //onFinish: () => this.form.reset('password', 'password_confirmation'),
            })
        }
    }
}
</script>
    