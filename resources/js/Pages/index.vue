<script setup>
    defineProps({customers: Object})
</script>

<template>
    <div>
        <div class="card mt-5 py-2">
            <table class="table table-striped">
                <thead>
                    <tr>
                        <th>#</th>
                        <th>Name</th>
                        <th>Action</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="customer in customers" :key="customer.id">
                        <th>{{ customer.id }}</th>
                        <td>{{ customer.name }}</td>
                        <td>
                            <a href="" class="btn text-info me-1"><i class="fa-regular fa-eye"></i></a>
                            <a href="" class="btn text-primary me-1"><i class="fa-regular fa-pen-to-square"></i></a>
                            <a href="" class="btn text-danger"><i class="fa-regular fa-trash-can"></i></a>
                        </td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
</template>
