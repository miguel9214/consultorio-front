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
                                    <button type="button" class="btn btn-success me-3" data-bs-toggle="modal"
                                        data-bs-target="#modalEditarSpeciality" @click="viewUser(data.value)">Editar</button>
                                    <button type="button" class="btn btn-danger"
                                        @click="deleteUser(data.value.id)">Eliminar</button>
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
                    <h5 class="modal-title" id="exampleModalLabel">Crear especialidad</h5>
                    <button type="button" data-dismiss="modal" data-bs-dismiss="modal" aria-label="Close" class="btn-close"
                        @click="resetFormData"></button>
                </div>
                <div class="modal-body">
                    <div class="row">
                        <div class="col-12">
                            <form class="text-start">
                                <div class="form">
                                    <!-- Nombre-->
                                    <div id="username-field" class="field-wrapper input">
                                        <label for="fullname" class="col-form-label p-1 fs-6 fw-bold">Nombre</label>
                                        <input v-model="formData.name" type="text" class="form-control" tabindex="1" />

                                        <template v-if="errors.name.length > 0">
                                            <b :key="e" v-for="e in errors.name" class="text-danger">
                                                {{ e }}
                                            </b>
                                        </template>
                                    </div>
                                </div>
                            </form>
                        </div>
                    </div>
                </div>
                <div class="modal-footer">
                    <a href="javascript:void(0)" data-bs-dismiss="modal">
                        <button type="button" class="btn btn-danger" @click="resetFormData">
                            Descartar
                        </button>
                    </a>
                    <a href="javascript:void(0)" data-bs-dismiss="modal">
                        <button type="button" class="btn btn-success" @click="CreateSpeciality">Crear</button>
                    </a>
                </div>
            </div>
        </div>
    </div>

    <div class="modal fade" id="modalEditarSpeciality" tabindex="-1" role="dialog" aria-labelledby="exampleModalLabel"
        aria-hidden="true">
        <div class="modal-dialog modal-lg" role="document">
            <div class="modal-content">
                <div class="modal-header">
                    <h5 class="modal-title" id="exampleModalLabel">Editar especialidad</h5>
                    <button type="button" data-dismiss="modal" data-bs-dismiss="modal" aria-label="Close" class="btn-close"
                        @click="resetFormData"></button>
                </div>
                <div class="modal-body">
                    <div class="row">
                        <div class="col-md-12">
                            <form class="text-start">
                                <div class="form">
                                    <!-- Nombre -->
                                    <div id="username-field" class="field-wrapper input">
                                        <label for="fullname" class="col-form-label p-1 fs-6 fw-bold">Nombre</label>
                                        <input v-model="formData.name" type="text" class="form-control" tabindex="1" />

                                        <template v-if="errors.name.length > 0">
                                            <b :key="e" v-for="e in errors.name" class="text-danger">
                                                {{ e }}
                                            </b>
                                        </template>
                                    </div>
                                </div>
                            </form>
                        </div>
                    </div>
                </div>
                <div class="modal-footer">
                    <a href="javascript:void(0)" ref="discardButton" data-bs-dismiss="modal">
                        <button type="button" class="btn btn-danger" @click="resetFormData">
                            Descartar
                        </button>
                    </a>
                    <a href="javascript:void(0)" data-bs-dismiss="modal">
                        <button type="button" class="btn btn-success" @click="EditSpeciality">Editar</button>
                    </a>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
import { onMounted, ref } from 'vue';
import Vue3Datatable from '@bhplugin/vue3-datatable';

import { useMeta } from '/src/composables/use-meta';
import { useApi } from '../composables/use-api';
useMeta({ title: 'Especialidad' });

const cols = ref([
    { field: 'index', title: '#Id', isUnique: true },
    { field: 'name', title: 'Nombre' },
    { field: 'actions', title: 'Acciones' },
]);

const rows = ref([]);
const totalRows = ref(0);

onMounted(async () => {
    await fetchDataFromApi();
});

const formData = ref({
    name: '',
});

const errors = ref({
    name: [],
});

const errorsClear = () => {
    errors.value = {
        name: [],
    }
}

const resetFormData = () => {
    formData.value = {
        name: '',
    };
};

const fetchDataFromApi = async () => {
    try {
        let currentId = 1;
        const { data, message } = await useApi("speciality");
        rows.value = data.map((item) => ({ ...item, index: currentId++ }));
        totalRows.value = data.length;
    } catch (error) {
        console.error('Error fetching data from API:', error);
    }
};

const discardButton = ref(null);

const CreateSpeciality = async () => {
    errorsClear()

    let has_error = false;
    Object.entries(formData.value).forEach(f => {
        const elemento = f[0]
        const value = f[1]
        if (value == "") {
            has_error = true
            errors.value[elemento] = "Este campo es obligatorio"
        }
    });

    if (has_error) return;

    try {
        await useApi("speciality", "POST", formData.value);
        Swal.fire({
            title: 'Éxito!',
            text: 'Especialidad creada correctamente!',
            icon: 'success',
            confirmButtonText: '¡Entendido!'
        }).then(() => {
            if (discardButton.value) {
                discardButton.value.click();
            }
            resetFormData();
        });

    } catch (error) {
        const errors_api = error.errors;
        Object.entries(errors_api).forEach(e => {
            const elemento = e[0]
            const mensaje = e[1]
            errors.value[elemento] = mensaje
        });
    }

    fetchDataFromApi();
};

let id;

const viewUser = async (user) => {

    const { data, message } = await useApi("speciality/" + user.id);

    if (message == "Speciality found") {
        id = user.id
        formData.value.name = data.name
    };
};

const EditSpeciality = async (user) => {

    try {
        const datosActualizados = {
            name: formData.value.name,
            price: formData.value.price
        };

        await useApi("speciality/" + id, "PUT", datosActualizados);

        Swal.fire({
            title: 'Éxito!',
            text: 'Especialidad editada correctamente!',
            icon: 'success',
            confirmButtonText: '¡Entendido!'
        }).then(() => {
            if (discardButton.value) {
                discardButton.value.click();
            }
            resetFormData();
        });

    } catch (error) {
        console.error("Error al actualizar la especialidad:", error);
    }

    fetchDataFromApi();

};

const deleteUser = async (id) => {
    const result = await Swal.fire({
        title: 'Estas seguro?',
        text: '¡No podrás revertir esto!',
        icon: 'warning',
        showCancelButton: true,
        confirmButtonColor: '#3085d6',
        cancelButtonColor: '#d33',
        confirmButtonText: 'Sí, borralo!'
    });

    if (result.isConfirmed) {
        try {
            await useApi("speciality/" + id, "DELETE");

            rows.value = rows.value.filter((d) => d.id != id);

            Swal.fire(
                'Eliminar!',
                'Tu archivo ha sido eliminado!.',
                'success'
            );
        } catch (error) {
            Swal.fire(
                'Error!',
                'An error occurred while deleting the record.',
                'error'
            );
        }
    }
};

</script>
