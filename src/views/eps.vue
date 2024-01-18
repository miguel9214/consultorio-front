<template>
    <div class="layout-px-spacing">
        <div class="seperator-header layout-top-spacing mb-4">
            <button type="button" class="btn btn-success me-3" data-bs-toggle="modal"
                data-bs-target="#modallg">Crear</button>
        </div>
        <div class="row layout-top-spacing">
            <div class="col-xl-12 col-lg-12 col-sm-12 layout-spacing">
                <div class="panel br-6 p-0">
                    <div class="vue3-datatable">
                        <vue3-datatable :rows="rows" :columns="cols" :totalRows="totalRows">
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

    <div class="modal fade" id="modallg" tabindex="-1" role="dialog" aria-labelledby="exampleModalLabel" aria-hidden="true">
        <div class="modal-dialog modal-lg" role="document">
            <div class="modal-content">
                <div class="modal-header">
                    <h5 class="modal-title" id="exampleModalLabel">Crear EPS</h5>
                    <button type="button" data-dismiss="modal" data-bs-dismiss="modal" aria-label="Close"
                        class="btn-close"></button>
                </div>
                <div class="modal-body">
                    <div class="row">
                        <div class="col-md-6">
                            <form class="text-start">
                                <div class="form">
                                    <!-- Nombre EPS -->
                                    <div id="username-field" class="field-wrapper input">
                                        <label for="fullname" class="col-form-label p-1 fs-6 fw-bold">Nombre EPS</label>
                                        <input type="text" class="form-control" tabindex="1" />
                                    </div>
                                    <!-- Telefono -->
                                    <div id="username-field" class="field-wrapper input mt-2">
                                        <label for="fullname" class="col-form-label p-1 fs-6 fw-bold">Telefono</label>
                                        <input type="number" class="form-control" tabindex="3" />
                                    </div>
                                    <!-- Fecha de Inicial Contrato -->
                                    <div id="username-field" class="field-wrapper input mt-2">
                                        <label for="fullname" class="col-form-label p-1 fs-6 fw-bold">Fecha Inicial Contrato</label>
                                        <input type="date" class="form-control" tabindex="5" />
                                    </div>
                                </div>
                            </form>
                        </div>
                        <div class="col-md-6">
                            <form class="text-start">
                                <div class="form">
                                    <!-- Direccion -->
                                    <div id="username-field" class="field-wrapper input">
                                        <label for="fullname" class="col-form-label p-1 fs-6 fw-bold">Dirección</label>
                                        <input type="text" class="form-control" tabindex="2" />
                                    </div>
                                    <!-- Codigo -->
                                    <div id="username-field" class="field-wrapper input mt-2">
                                        <label for="fullname" class="col-form-label p-1 fs-6 fw-bold">NIT</label>
                                        <input type="text" class="form-control" tabindex="4" />
                                    </div>
                                    <!-- Fecha de Final Contrato -->
                                    <div id="username-field" class="field-wrapper input mt-2">
                                        <label for="fullname" class="col-form-label p-1 fs-6 fw-bold">Fecha Final Contrato</label>
                                        <input type="date" class="form-control" tabindex="6" />
                                    </div>
                                </div>
                            </form>
                        </div>
                    </div>
                </div>
                <div class="modal-footer">
                    <a href="javascript:void(0)" data-dismiss="modal" data-bs-dismiss="modal">
                        <button type="button" class="btn btn-danger" >
                            Discard</button>
                    </a>
                    <button type="button" class="btn btn-success">Save</button>
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


onMounted(async () => {
    await fetchDataFromApi();
});

const fetchDataFromApi = async () => {
    try {
        let currentId = 1;
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
