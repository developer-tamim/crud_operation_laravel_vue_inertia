<script setup>
    import { useForm } from '@inertiajs/vue3';
    import { router } from '@inertiajs/vue3';

    const form = useForm({
        name: null,
        email: null,
        phone: null,
    });

    function submit(){
        router.post('/customer' , form)
    }
</script>

<template>
    <div>
        <div class="card mt-5">
            <div class="card-header">Featured</div>
            <div class="card-body">
                <form @submit.prevent="submit">
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
                            aria-describedby="emailHelp"
                        />
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
                            aria-describedby="emailHelp"
                        />
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
                    </div>

                    <button type="submit" class="btn btn-primary">
                        Save
                    </button>
                </form>
            </div>
        </div>
    </div>
</template>
