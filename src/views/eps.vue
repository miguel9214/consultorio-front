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
                        <vue3-datatable :rows="rows" :columns="cols" :totalRows="totalRows" :sortable="true">
                            <template #actions="data">
                                <div class="flex">
                                    <button type="button" class="btn btn-success me-3"
                                    data-bs-toggle="modal" data-bs-target="#modalEditarEPS"
                                        @click="viewUser(data.value)">Editar</button>
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
                    <h5 class="modal-title" id="exampleModalLabel">Crear EPS</h5>
                    <button type="button" data-dismiss="modal" data-bs-dismiss="modal" aria-label="Close"
                        class="btn-close" @click="resetFormData"></button>
                </div>
                <div class="modal-body">
                    <div class="row">
                        <div class="col-md-6">
                            <form class="text-start">
                                <div class="form">
                                    <!-- Nombre EPS -->
                                    <div id="username-field" class="field-wrapper input">
                                        <label for="fullname" class="col-form-label p-1 fs-6 fw-bold">Nombre EPS</label>
                                        <input v-model="formData.name" type="text" class="form-control" tabindex="1" />

                                        <template v-if="errors.name.length > 0">
                                            <b :key="e" v-for="e in errors.name" class="text-danger">
                                                {{ e }}
                                            </b>
                                        </template>
                                    </div>
                                    <!-- Telefono -->
                                    <div id="username-field" class="field-wrapper input mt-2">
                                        <label for="fullname" class="col-form-label p-1 fs-6 fw-bold">Telefono</label>
                                        <input v-model="formData.phone" type="number" class="form-control" tabindex="3" />

                                        <template v-if="errors.phone.length > 0">
                                            <b :key="e" v-for="e in errors.phone" class="text-danger">
                                                {{ e }}
                                            </b>
                                        </template>
                                    </div>
                                    <!-- Fecha de Inicial Contrato -->
                                    <div id="username-field" class="field-wrapper input mt-2">
                                        <label for="fullname" class="col-form-label p-1 fs-6 fw-bold">Fecha Inicial
                                            Contrato</label>
                                        <input v-model="formData.contract_start_date" type="date" class="form-control"
                                            tabindex="5" />

                                        <template v-if="errors.contract_start_date.length > 0">
                                            <b :key="e" v-for="e in errors.contract_start_date" class="text-danger">
                                                {{ e }}
                                            </b>
                                        </template>
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
                                        <input v-model="formData.address" type="text" class="form-control" tabindex="2" />

                                        <template v-if="errors.address.length > 0">
                                            <b :key="e" v-for="e in errors.address" class="text-danger">
                                                {{ e }}
                                            </b>
                                        </template>
                                    </div>
                                    <!-- Codigo -->
                                    <div id="username-field" class="field-wrapper input mt-2">
                                        <label for="fullname" class="col-form-label p-1 fs-6 fw-bold">NIT</label>
                                        <input v-model="formData.code" type="text" class="form-control" tabindex="4" />

                                        <template v-if="errors.code.length > 0">
                                            <b :key="e" v-for="e in errors.code" class="text-danger">
                                                {{ e }}
                                            </b>
                                        </template>
                                    </div>
                                    <!-- Fecha de Final Contrato -->
                                    <div id="username-field" class="field-wrapper input mt-2">
                                        <label for="fullname" class="col-form-label p-1 fs-6 fw-bold">Fecha Final
                                            Contrato</label>
                                        <input v-model="formData.contract_end_date" type="date" class="form-control"
                                            tabindex="6" />

                                        <template v-if="errors.contract_end_date.length > 0">
                                            <b :key="e" v-for="e in errors.contract_end_date" class="text-danger">
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
                    <a href="javascript:void(0)"  data-bs-dismiss="modal">
                        <button type="button" class="btn btn-danger" @click="resetFormData">
                            Descartar
                        </button>
                    </a>
                    <a href="javascript:void(0)"  data-bs-dismiss="modal">
                        <button type="button" class="btn btn-success" @click="CreateEPS">Crear</button>
                    </a>
                </div>
            </div>
        </div>
    </div>

    <div class="modal fade" id="modalEditarEPS" tabindex="-1" role="dialog" aria-labelledby="exampleModalLabel" aria-hidden="true">
    <div class="modal-dialog modal-lg" role="document">
        <div class="modal-content">
            <div class="modal-header">
                <h5 class="modal-title" id="exampleModalLabel">Editar EPS</h5>
                <button type="button" data-dismiss="modal" data-bs-dismiss="modal" aria-label="Close"
                    class="btn-close" @click="resetFormData"></button>
            </div>
            <div class="modal-body">
                <div class="row">
                    <div class="col-md-6">
                        <form class="text-start">
                            <div class="form">
                                <!-- Nombre EPS -->
                                <div id="username-field" class="field-wrapper input">
                                    <label for="fullname" class="col-form-label p-1 fs-6 fw-bold">Nombre EPS</label>
                                    <input v-model="formData.name" type="text" class="form-control" tabindex="1" />

                                    <template v-if="errors.name.length > 0">
                                        <b :key="e" v-for="e in errors.name" class="text-danger">
                                            {{ e }}
                                        </b>
                                    </template>
                                </div>
                                <!-- Telefono -->
                                <div id="username-field" class="field-wrapper input mt-2">
                                    <label for="fullname" class="col-form-label p-1 fs-6 fw-bold">Telefono</label>
                                    <input v-model="formData.phone" type="number" class="form-control" tabindex="3" />

                                    <template v-if="errors.phone.length > 0">
                                        <b :key="e" v-for="e in errors.phone" class="text-danger">
                                            {{ e }}
                                        </b>
                                    </template>
                                </div>
                                <!-- Fecha de Inicial Contrato -->
                                <div id="username-field" class="field-wrapper input mt-2">
                                    <label for="fullname" class="col-form-label p-1 fs-6 fw-bold">Fecha Inicial
                                        Contrato</label>
                                    <input v-model="formData.contract_start_date" type="date" class="form-control"
                                        tabindex="5" />

                                    <template v-if="errors.contract_start_date.length > 0">
                                        <b :key="e" v-for="e in errors.contract_start_date" class="text-danger">
                                            {{ e }}
                                        </b>
                                    </template>
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
                                    <input v-model="formData.address" type="text" class="form-control" tabindex="2" />

                                    <template v-if="errors.address.length > 0">
                                        <b :key="e" v-for="e in errors.address" class="text-danger">
                                            {{ e }}
                                        </b>
                                    </template>
                                </div>
                                <!-- Codigo -->
                                <div id="username-field" class="field-wrapper input mt-2">
                                    <label for="fullname" class="col-form-label p-1 fs-6 fw-bold">NIT</label>
                                    <input v-model="formData.code" type="text" class="form-control" tabindex="4" />

                                    <template v-if="errors.code.length > 0">
                                        <b :key="e" v-for="e in errors.code" class="text-danger">
                                            {{ e }}
                                        </b>
                                    </template>
                                </div>
                                <!-- Fecha de Final Contrato -->
                                <div id="username-field" class="field-wrapper input mt-2">
                                    <label for="fullname" class="col-form-label p-1 fs-6 fw-bold">Fecha Final
                                        Contrato</label>
                                    <input v-model="formData.contract_end_date" type="date" class="form-control"
                                        tabindex="6" />

                                    <template v-if="errors.contract_end_date.length > 0">
                                        <b :key="e" v-for="e in errors.contract_end_date" class="text-danger">
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
                    <button type="button" class="btn btn-success" @click="EditEPS">Editar</button>
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
import { useApi  } from '../composables/use-api';
useMeta({ title: 'EPS' });

const cols = ref([
    { field: 'index', title: '#Id', isUnique: true },
    { field: 'name', title: 'Nombre' },
    { field: 'address', title: 'Dirección' },
    { field: 'phone', title: 'Telefono' },
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

const formData = ref({
    name: '',
    address: '',
    phone: '',
    code: '',
    contract_start_date: '',
    contract_end_date: '',
});

const errors = ref({
    name: [],
    address: [],
    phone: [],
    code: [],
    sex: [],
    contract_start_date: [],
    contract_end_date: [],
});

const errorsClear = () => {
    errors.value = {
        name: [],
        address: [],
        phone: [],
        code: [],
        sex: [],
        contract_start_date: [],
        contract_end_date: [],
    }
}

const resetFormData = () => {
    formData.value = {
        name: '',
        address: '',
        phone: '',
        code: '',
        contract_start_date: '',
        contract_end_date: '',
    };
};

const fetchDataFromApi = async () => {
    try {
        let currentId = 1;
        const {data,message} = await useApi("eps");
        rows.value = data.map((item) => ({ ...item, index: currentId++ }));
        totalRows.value = data.length;
    } catch (error) {
        console.error('Error fetching data from API:', error);
    }
};

const discardButton = ref(null);

const CreateEPS = async () => {
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

    if (has_error) {
        return;
    }

    try {
        await useApi("eps","POST", formData.value);
        Swal.fire({
            title: 'Éxito!',
            text: 'EPS creada correctamente!',
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

        const {data,message} = await useApi("eps/" + user.id);

        if(message == "EPS found"){
            id = user.id
            formData.value.name = data.name
            formData.value.address = data.address
            formData.value.phone = data.phone
            formData.value.code = data.code
            formData.value.contract_start_date = data.contract_start_date
            formData.value.contract_end_date = data.contract_end_date                        
        };
};

const EditEPS = async () => {

    try {
        const datosActualizados = {
            name: formData.value.name,
            address: formData.value.address,
            phone: formData.value.phone,
            code: formData.value.code,
            contract_start_date: formData.value.contract_start_date,
            contract_end_date: formData.value.contract_end_date
        };

        await useApi("eps/" + id,"PUT", datosActualizados);
        
        Swal.fire({
            title: 'Éxito!',
            text: 'EPS editada correctamente!',
            icon: 'success',
            confirmButtonText: '¡Entendido!'
        }).then(() => {
            if (discardButton.value) {
                discardButton.value.click();
            }
            resetFormData();
        });

    } catch (error) {
        console.error("Error al actualizar la EPS:", error);
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

    console.log("que tiene:", result)
    if (result.isConfirmed) {
        try {
            await useApi("eps/" + id,"DELETE");

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
