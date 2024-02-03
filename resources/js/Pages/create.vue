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
                <form @submit.prevent="submit">
                    <!-- @csrf -->
                    <div class="mb-3">
                        <label for="exampleInputEmail1" class="form-label"
                            >Name</label
                        >
                        <input
                            type="text"
                            name="name"
                            id="name"
                            v-model="form.name"
                            class="form-control"
                        />
                        <div
                            v-if="form.errors.name"
                            class="text-danger text-xs"
                        >
                            {{ form.errors.name[0] }}
                        </div>
                    </div>
                    <div class="mb-3">
                        <label for="exampleInputEmail1" class="form-label"
                            >Email address</label
                        >
                        <input
                            type="email"
                            name="email"
                            id="email"
                            v-model="form.email"
                            class="form-control"
                        />
                        <div
                            v-if="form.errors.email"
                            class="text-danger text-xs"
                        >
                            {{ form.errors.email[0] }}
                        </div>
                    </div>
                    <div class="mb-3">
                        <label for="exampleInputPassword1" class="form-label"
                            >Phone</label
                        >
                        <input
                            type="number"
                            id="phone"
                            name="phone"
                            v-model="form.phone"
                            class="form-control"
                        />
                        <div
                            v-if="form.errors.phone"
                            class="text-danger text-xs"
                        >
                            {{ form.errors.phone[0] }}
                        </div>
                    </div>

                    <button type="submit" class="btn btn-primary">Save</button>
                </form>
            </div>
        </div>
    </div>
</template>
