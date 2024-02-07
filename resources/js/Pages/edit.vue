<script setup>
// import { useForm } from "@inertiajs/vue3";
import { router } from "@inertiajs/vue3";
import { useForm, usePage } from "@inertiajs/inertia-vue3";
const { $inertia } = usePage();

defineProps({
    errors: Object,
});

const form = useForm({
    name: null,
    email: null,
    phone: null,
});

// function submit(){
//     router.post('/customer' , form)
// }
function submit() {
    router
        $inertia.post("/customers/create", form)
        .then(() => {
            // Handle success or redirect if needed
        })
        .catch((error) => {
            // Update the form errors based on the server response
            if (
                error.response &&
                error.response.data &&
                error.response.data.errors
            ) {
                form.errors.name = error.response.data.errors.name;
                form.errors.email = error.response.data.errors.email;
                form.errors.phone = error.response.data.errors.phone;
            }
        });
}
</script>


<template>
    <div>
        <div class="card mt-5">
            <div class="card-header">Create Form</div>
            <div class="card-body">
               <!-- this code should be change -->
            </div>
        </div>
    </div>
</template>
