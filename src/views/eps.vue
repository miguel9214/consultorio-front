<template>
    <div class="layout-px-spacing">
        <div class="seperator-header layout-top-spacing mb-4">
            <button type="button" class="btn btn-success me-3">Crear</button>
        </div>
        <div class="row layout-top-spacing">
            <div class="col-xl-12 col-lg-12 col-sm-12 layout-spacing">
                <div class="panel br-6 p-0">
                    <div class="vue3-datatable">
                        <vue3-datatable :rows="rows" :columns="cols" :totalRows="totalRows">
                            <template>
                                <strong>#{{ currentId++ }}</strong>
                            </template>                            
                            <template #actions="data">
                                <div class="flex">
                                    <button type="button" class="btn btn-success me-3"
                                        @click="viewUser(data.value)">Editar</button>
                                    <button type="button" class="btn btn-danger"
                                        @click="deleteUser(data.value)">Eliminar</button>
                                </div>
                            </template>
                        </vue3-datatable>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
import { onMounted, ref } from 'vue';
import Vue3Datatable from '@bhplugin/vue3-datatable';
import axios from 'axios';

import { useMeta } from '/src/composables/use-meta';
useMeta({ title: 'EPS' });

const cols = ref([
    { field: 'id', title: '#Id', isUnique: true },
    { field: 'name', title: 'Nombre' },
    { field: 'address', title: 'Direción' },
    { field: 'phone', title: 'Teleono' },
    { field: 'code', title: 'NIT' },
    { field: 'contract_start_date', title: 'Inicio de Contrato' },
    { field: 'contract_end_date', title: 'Final de Contrato' },
    { field: 'actions', title: 'Acciones' },
]);

const rows = ref([]);
const totalRows = ref(0);

let currentId = 1;

onMounted(async () => {
    await fetchDataFromApi();
});

const fetchDataFromApi = async () => {
    try {
        const response = await axios.get('http://consultorio.test/api/epsPublic');
        rows.value = response.data.data.map((item) => ({ ...item, id: currentId++ }));
        totalRows.value = response.data.data.length;
    } catch (error) {
        console.error('Error fetching data from API:', error);
    }
};

const viewUser = (user) => {
    alert('View User \n' + user.id + ', ' + user.firstName + ', ' + user.lastName + ', ' + user.email);
};

const deleteUser = (user) => {
    if (confirm('Are you sure want to delete selected row ?')) {
        rows.value = rows.value.filter((d) => d.id != user.id);
    }
};

const rowClick = (user) => {
    alert('User Details \n' + user.id + ', ' + user.firstName + ', ' + user.lastName + ', ' + user.email);
};

</script>
