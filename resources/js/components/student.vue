<template>
    <div>
        <div class="container p-5">
            <button class="btn btn-primary">Add New</button>
            <table table-hover>
                <thead>
                    <td>Name</td>
                    <td>Email</td>
                    <td>Phone</td>
                    <td>Action</td>
                </thead>
                
                <tbody>
                    <span v-for="student in students" :key="student.id">
                        <tr>
                            <td>{{ student.name }}</td>
                            <td>{{ student.email }}</td>
                            <td>{{ student.phone }}</td>
                            <td>Edit</td>
                        </tr>
                    </span>
                </tbody>
            </table>
        </div>
    </div>
</template>

<script>
    import { ref, onMounted } from 'vue'
    import axios from 'axios'

    export default({
        setup() {
            const students = ref([])
            const getStudent = async() =>{
                let res = await get.axios('api/students')
                students.value = res.data
            }
            onMounted(getStudent())
            return{
                students
            }

        },
    })
</script>

<style scoped>
    table, td, th {
        border: 1px solid black;
    }

    table {
        border-collapse: collapse;
        width: 100%;
        margin-top: 5px;
    }
</style>