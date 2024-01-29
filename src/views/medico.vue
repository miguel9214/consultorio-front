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
                    <h5 class="modal-title" id="exampleModalLabel">Crear medico</h5>
                    <button type="button" data-dismiss="modal" data-bs-dismiss="modal" aria-label="Close" class="btn-close"
                        @click="resetFormData"></button>
                </div>
                <div class="modal-body">
                    <div class="row">
                        <div class="col-md-6">
                            <form class="text-start">
                                <div class="form">
                                    <!-- Tipo de Documento -->
                                    <div id="document-type-field" class="field-wrapper input mt-2">
                                        <div style="margin-top: 1px">
                                            <select v-model="formData.type_document"
                                                class="form-control form-control-sm border-0 pt-0"
                                                style="margin-left: 25px; width: 220px; font-family: inherit; font-weight: 600; font-size: 16px; padding: 1px 16px 9px 8px"
                                                tabindex="1">
                                                <option style="margin: 1px" value="" disabled selected>Tipo de
                                                    Documento</option>
                                                <option value="RC">RC</option>
                                                <option value="TI">TI</option>
                                                <option value="CC">CC</option>
                                                <option value="EX">EX</option>
                                            </select>
                                        </div>

                                        <template v-if="errors.type_document.length > 0">
                                            <b :key="e" v-for="e in errors.type_document" class="text-danger">
                                                {{ e }}
                                            </b>
                                        </template>
                                    </div>
                                    <!-- Nombre -->
                                    <div id="username-field" class="field-wrapper input mt-2">
                                        <label for="fullname" class="col-form-label p-1 fs-6 fw-bold">Nombre</label>
                                        <input v-model="formData.first_name" type="text" class="form-control" tabindex="3" />

                                        <template v-if="errors.first_name.length > 0">
                                            <b :key="e" v-for="e in errors.first_name" class="text-danger">
                                                {{ e }}
                                            </b>
                                        </template>
                                    </div>
                                    <!-- Sexo -->
                                    <div id="username-field" class="field-wrapper input mt-2">
                                        <label for="fullname" class="col-form-label p-1 fs-6 fw-bold">Sexo</label>
                                            <div style="margin-top: 1px">
                                                <select v-model="formData.sex"
                                                    class="form-control form-control-sm p-2 border-0 pt-0"
                                                    style="margin-left: 25px; width: 220px; font-family: inherit; font-weight: 600; font-size: 16px; padding: 1px 16px 9px 16px"
                                                    tabindex="6">
                                                    <option style="margin: 1px" value="" disabled selected>Genero
                                                    </option>
                                                    <option value="1">Masculino</option>
                                                    <option value="2">Femenino</option>
                                                </select>
                                            </div>
                                        <template v-if="errors.sex.length > 0">
                                            <b :key="e" v-for="e in errors.sex" class="text-danger">
                                                {{ e }}
                                            </b>
                                        </template>
                                    </div>
                                    <!-- Fecha de nacimiento -->
                                    <div id="username-field" class="field-wrapper input mt-2">
                                        <label for="fullname" class="col-form-label p-1 fs-6 fw-bold">Fecha de Nacimientos</label>
                                        <input v-model="formData.birthdate" type="date" class="form-control" tabindex="3" />

                                        <template v-if="errors.birthdate.length > 0">
                                            <b :key="e" v-for="e in errors.birthdate" class="text-danger">
                                                {{ e }}
                                            </b>
                                        </template>
                                    </div>
                                    <!-- Ciudad -->
                                    <div id="username-field" class="field-wrapper input mt-2">
                                        <label for="fullname" class="col-form-label p-1 fs-6 fw-bold">Ciudad</label>
                                        <input v-model="formData.city" type="date" class="form-control" tabindex="3" />

                                        <template v-if="errors.city.length > 0">
                                            <b :key="e" v-for="e in errors.city" class="text-danger">
                                                {{ e }}
                                            </b>
                                        </template>
                                    </div>
                                    <!-- Barrio -->
                                    <div id="username-field" class="field-wrapper input mt-2">
                                        <label for="fullname" class="col-form-label p-1 fs-6 fw-bold">Barrio</label>
                                        <input v-model="formData.neighborhood" type="date" class="form-control" tabindex="3" />

                                        <template v-if="errors.neighborhood.length > 0">
                                            <b :key="e" v-for="e in errors.neighborhood" class="text-danger">
                                                {{ e }}
                                            </b>
                                        </template>
                                    </div>
                                    <!-- Email -->
                                    <div id="username-field" class="field-wrapper input mt-2">
                                        <label for="fullname" class="col-form-label p-1 fs-6 fw-bold">Barrio</label>
                                        <input v-model="formData.email" type="date" class="form-control" tabindex="3" />

                                        <template v-if="errors.email.length > 0">
                                            <b :key="e" v-for="e in errors.email" class="text-danger">
                                                {{ e }}
                                            </b>
                                        </template>
                                    </div>  
                                    <!-- Contraseña -->
                                    <div id="password-field" class="field-wrapper input mb-2">
                                        <input v-model="formData.password"
                                            :type="showPassword ? 'text' : 'password'" class="form-control"
                                            placeholder="Contraseña" tabindex="15" />

                                        <template v-if="errors.password.length > 0">
                                            <b :key="e" v-for="e in errors.password" class="text-danger">
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
                                    <!-- Documento -->
                                    <div id="username-field" class="field-wrapper input">
                                        <label for="fullname" class="col-form-label p-1 fs-6 fw-bold">Dirección</label>
                                        <input v-model="formData.document" type="text" class="form-control" tabindex="2" />

                                        <template v-if="errors.document.length > 0">
                                            <b :key="e" v-for="e in errors.document" class="text-danger">
                                                {{ e }}
                                            </b>
                                        </template>
                                    </div>
                                    <!-- Apellido -->
                                    <div id="username-field" class="field-wrapper input mt-2">
                                        <label for="fullname" class="col-form-label p-1 fs-6 fw-bold">Apellido</label>
                                        <input v-model="formData.last_name" type="text" class="form-control" tabindex="3" />

                                        <template v-if="errors.last_name.length > 0">
                                            <b :key="e" v-for="e in errors.last_name" class="text-danger">
                                                {{ e }}
                                            </b>
                                        </template>
                                    </div>
                                    <!-- Telefono -->
                                    <div id="username-field" class="field-wrapper input mt-2">
                                        <label for="fullname" class="col-form-label p-1 fs-6 fw-bold">Telefono</label>
                                        <input v-model="formData.phone" type="text" class="form-control" tabindex="3" />

                                        <template v-if="errors.phone.length > 0">
                                            <b :key="e" v-for="e in errors.phone" class="text-danger">
                                                {{ e }}
                                            </b>
                                        </template>
                                    </div>
                                    <!-- Direccion -->
                                    <div id="username-field" class="field-wrapper input mt-2">
                                        <label for="fullname" class="col-form-label p-1 fs-6 fw-bold">Dirección</label>
                                        <input v-model="formData.address" type="text" class="form-control" tabindex="3" />

                                        <template v-if="errors.address.length > 0">
                                            <b :key="e" v-for="e in errors.address" class="text-danger">
                                                {{ e }}
                                            </b>
                                        </template>
                                    </div>
                                    <!-- Estado -->
                                    <div id="username-field" class="field-wrapper input mt-2">
                                        <label for="fullname" class="col-form-label p-1 fs-6 fw-bold">Estado</label>
                                        <input v-model="formData.state" type="text" class="form-control" tabindex="3" />

                                        <template v-if="errors.state.length > 0">
                                            <b :key="e" v-for="e in errors.state" class="text-danger">
                                                {{ e }}
                                            </b>
                                        </template>
                                    </div>
                                    <!-- Especialidad -->
                                    <div id="username-field" class="field-wrapper input mt-2">
                                        <label for="fullname" class="col-form-label p-1 fs-6 fw-bold">Especialidad</label>
                                        <input v-model="formData.speciality" type="text" class="form-control" tabindex="3" />

                                        <template v-if="errors.speciality.length > 0">
                                            <b :key="e" v-for="e in errors.speciality" class="text-danger">
                                                {{ e }}
                                            </b>
                                        </template>
                                    </div>
                                    <!-- Confirmar Contraseña -->
                                    <div id="confirm-password-field" class="field-wrapper input">
                                        <label for="fullname" class="col-form-label p-1 fs-6 fw-bold">Confirmar Contraseña</label>
                                        <input v-model="formData.password_confirmed"
                                            :type="showPassword ? 'text' : 'password'" class="form-control"
                                            placeholder="Confirmar Contraseña" tabindex="16" />

                                        <template v-if="errors.password_confirmed.length > 0">
                                            <b :key="e" v-for="e in errors.password_confirmed" class="text-danger">
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
                        <button type="button" class="btn btn-success" @click="createMedico">Crear</button>
                    </a>
                </div>
            </div>
        </div>
    </div>

    <div class="modal fade" id="modalEditarEPS" tabindex="-1" role="dialog" aria-labelledby="exampleModalLabel"
        aria-hidden="true">
        <div class="modal-dialog modal-lg" role="document">
            <div class="modal-content">
                <div class="modal-header">
                    <h5 class="modal-title" id="exampleModalLabel">Editar EPS</h5>
                    <button type="button" data-dismiss="modal" data-bs-dismiss="modal" aria-label="Close" class="btn-close"
                        @click="resetFormData"></button>
                </div>
                <div class="modal-body">
                    <div class="row">
                        <div class="col-md-6">
                            <form class="text-start">
                                <div class="form">
                                    <!-- Tipo de Documento -->
                                    <div id="document-type-field" class="field-wrapper input mt-2">
                                        <div style="margin-top: 1px">
                                            <select v-model="formData.type_document"
                                                class="form-control form-control-sm border-0 pt-0"
                                                style="margin-left: 25px; width: 220px; font-family: inherit; font-weight: 600; font-size: 16px; padding: 1px 16px 9px 8px"
                                                tabindex="1">
                                                <option style="margin: 1px" value="" disabled selected>Tipo de
                                                    Documento</option>
                                                <option value="RC">RC</option>
                                                <option value="TI">TI</option>
                                                <option value="CC">CC</option>
                                                <option value="EX">EX</option>
                                            </select>
                                        </div>

                                        <template v-if="errors.type_document.length > 0">
                                            <b :key="e" v-for="e in errors.type_document" class="text-danger">
                                                {{ e }}
                                            </b>
                                        </template>
                                    </div>
                                    <!-- Nombre -->
                                    <div id="username-field" class="field-wrapper input mt-2">
                                        <label for="fullname" class="col-form-label p-1 fs-6 fw-bold">Nombre</label>
                                        <input v-model="formData.first_name" type="text" class="form-control" tabindex="3" />

                                        <template v-if="errors.first_name.length > 0">
                                            <b :key="e" v-for="e in errors.first_name" class="text-danger">
                                                {{ e }}
                                            </b>
                                        </template>
                                    </div>
                                    <!-- Sexo -->
                                    <div id="username-field" class="field-wrapper input mt-2">
                                        <label for="fullname" class="col-form-label p-1 fs-6 fw-bold">Sexo</label>
                                            <div style="margin-top: 1px">
                                                <select v-model="formData.sex"
                                                    class="form-control form-control-sm p-2 border-0 pt-0"
                                                    style="margin-left: 25px; width: 220px; font-family: inherit; font-weight: 600; font-size: 16px; padding: 1px 16px 9px 16px"
                                                    tabindex="6">
                                                    <option style="margin: 1px" value="" disabled selected>Genero
                                                    </option>
                                                    <option value="1">Masculino</option>
                                                    <option value="2">Femenino</option>
                                                </select>
                                            </div>
                                        <template v-if="errors.sex.length > 0">
                                            <b :key="e" v-for="e in errors.sex" class="text-danger">
                                                {{ e }}
                                            </b>
                                        </template>
                                    </div>
                                    <!-- Fecha de nacimiento -->
                                    <div id="username-field" class="field-wrapper input mt-2">
                                        <label for="fullname" class="col-form-label p-1 fs-6 fw-bold">Fecha de Nacimientos</label>
                                        <input v-model="formData.birthdate" type="date" class="form-control" tabindex="3" />

                                        <template v-if="errors.birthdate.length > 0">
                                            <b :key="e" v-for="e in errors.birthdate" class="text-danger">
                                                {{ e }}
                                            </b>
                                        </template>
                                    </div>
                                    <!-- Ciudad -->
                                    <div id="username-field" class="field-wrapper input mt-2">
                                        <label for="fullname" class="col-form-label p-1 fs-6 fw-bold">Ciudad</label>
                                        <input v-model="formData.city" type="date" class="form-control" tabindex="3" />

                                        <template v-if="errors.city.length > 0">
                                            <b :key="e" v-for="e in errors.city" class="text-danger">
                                                {{ e }}
                                            </b>
                                        </template>
                                    </div>
                                    <!-- Barrio -->
                                    <div id="username-field" class="field-wrapper input mt-2">
                                        <label for="fullname" class="col-form-label p-1 fs-6 fw-bold">Barrio</label>
                                        <input v-model="formData.neighborhood" type="date" class="form-control" tabindex="3" />

                                        <template v-if="errors.neighborhood.length > 0">
                                            <b :key="e" v-for="e in errors.neighborhood" class="text-danger">
                                                {{ e }}
                                            </b>
                                        </template>
                                    </div>
                                    <!-- Email -->
                                    <div id="username-field" class="field-wrapper input mt-2">
                                        <label for="fullname" class="col-form-label p-1 fs-6 fw-bold">Barrio</label>
                                        <input v-model="formData.email" type="date" class="form-control" tabindex="3" />

                                        <template v-if="errors.email.length > 0">
                                            <b :key="e" v-for="e in errors.email" class="text-danger">
                                                {{ e }}
                                            </b>
                                        </template>
                                    </div>  
                                    <!-- Contraseña -->
                                    <div id="password-field" class="field-wrapper input mb-2">
                                        <input v-model="formData.password"
                                            :type="showPassword ? 'text' : 'password'" class="form-control"
                                            placeholder="Contraseña" tabindex="15" />

                                        <template v-if="errors.password.length > 0">
                                            <b :key="e" v-for="e in errors.password" class="text-danger">
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
                                    <!-- Documento -->
                                    <div id="username-field" class="field-wrapper input">
                                        <label for="fullname" class="col-form-label p-1 fs-6 fw-bold">Dirección</label>
                                        <input v-model="formData.document" type="text" class="form-control" tabindex="2" />

                                        <template v-if="errors.document.length > 0">
                                            <b :key="e" v-for="e in errors.document" class="text-danger">
                                                {{ e }}
                                            </b>
                                        </template>
                                    </div>
                                    <!-- Apellido -->
                                    <div id="username-field" class="field-wrapper input mt-2">
                                        <label for="fullname" class="col-form-label p-1 fs-6 fw-bold">Apellido</label>
                                        <input v-model="formData.last_name" type="text" class="form-control" tabindex="3" />

                                        <template v-if="errors.last_name.length > 0">
                                            <b :key="e" v-for="e in errors.last_name" class="text-danger">
                                                {{ e }}
                                            </b>
                                        </template>
                                    </div>
                                    <!-- Telefono -->
                                    <div id="username-field" class="field-wrapper input mt-2">
                                        <label for="fullname" class="col-form-label p-1 fs-6 fw-bold">Telefono</label>
                                        <input v-model="formData.phone" type="text" class="form-control" tabindex="3" />

                                        <template v-if="errors.phone.length > 0">
                                            <b :key="e" v-for="e in errors.phone" class="text-danger">
                                                {{ e }}
                                            </b>
                                        </template>
                                    </div>
                                    <!-- Direccion -->
                                    <div id="username-field" class="field-wrapper input mt-2">
                                        <label for="fullname" class="col-form-label p-1 fs-6 fw-bold">Dirección</label>
                                        <input v-model="formData.address" type="text" class="form-control" tabindex="3" />

                                        <template v-if="errors.address.length > 0">
                                            <b :key="e" v-for="e in errors.address" class="text-danger">
                                                {{ e }}
                                            </b>
                                        </template>
                                    </div>
                                    <!-- Estado -->
                                    <div id="username-field" class="field-wrapper input mt-2">
                                        <label for="fullname" class="col-form-label p-1 fs-6 fw-bold">Estado</label>
                                        <input v-model="formData.state" type="text" class="form-control" tabindex="3" />

                                        <template v-if="errors.state.length > 0">
                                            <b :key="e" v-for="e in errors.state" class="text-danger">
                                                {{ e }}
                                            </b>
                                        </template>
                                    </div>
                                    <!-- Especialidad -->
                                    <div id="username-field" class="field-wrapper input mt-2">
                                        <label for="fullname" class="col-form-label p-1 fs-6 fw-bold">Especialidad</label>
                                        <input v-model="formData.speciality" type="text" class="form-control" tabindex="3" />

                                        <template v-if="errors.speciality.length > 0">
                                            <b :key="e" v-for="e in errors.speciality" class="text-danger">
                                                {{ e }}
                                            </b>
                                        </template>
                                    </div>
                                    <!-- Confirmar Contraseña -->
                                    <div id="confirm-password-field" class="field-wrapper input">
                                        <label for="fullname" class="col-form-label p-1 fs-6 fw-bold">Confirmar Contraseña</label>
                                        <input v-model="formData.password_confirmed"
                                            :type="showPassword ? 'text' : 'password'" class="form-control"
                                            placeholder="Confirmar Contraseña" tabindex="16" />

                                        <template v-if="errors.password_confirmed.length > 0">
                                            <b :key="e" v-for="e in errors.password_confirmed" class="text-danger">
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
                        <button type="button" class="btn btn-success" @click="EditMedico">Editar</button>
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
useMeta({ title: 'Medicos' });

const cols = ref([
    { field: 'index', title: '#Id', isUnique: true },
    { field: 'tipo_documento', title: 'T. documento' },
    { field: 'documento', title: 'Documento' },
    { field: 'nombre', title: 'Nombre' },
    { field: 'apellido', title: 'Apellido' },
    { field: 'sexo', title: 'Sexo' },
    { field: 'telefono', title: 'Telefono' },
    { field: 'fecha_nacimiento', title: 'Fecha Nacimiento' },
    { field: 'direccion', title: 'Direccion' },
    { field: 'ciudad', title: 'Telefono' },
    { field: 'estado', title: 'Departamento' },
    { field: 'barrio', title: 'Barrio' },
    { field: 'especialidad', title: 'Especialidad' },
    { field: 'email', title: 'Correo' },
    { field: 'actions', title: 'Acciones' },
]);

console.log("Columnas", cols)

const rows = ref([]);
const totalRows = ref(0);

onMounted(async () => {
    await fetchDataFromApi();
});


const formData = ref({
    type_document: '',
    document: '',
    first_name: '',
    last_name: '',
    sex: '',
    phone: '',
    birthdate: '',
    address: '',
    city: '',
    state: '',
    neighborhood: '',
    speciality: '',
    email: '',
    password: '',
    password_confirmed: ''
});

const errors = ref({
    type_document: [],
    document: [],
    first_name: [],
    last_name: [],
    sex: [],
    phone: [],
    birthdate: [],
    address: [],
    city: [],
    state: [],
    neighborhood: [],
    speciality: [],
    email: [],
    password: [],
    password_confirmed: []
});

const errorsClear = () => {
    errors.value = {
        type_document: [],
        document: [],
        first_name: [],
        last_name: [],
        sex: [],
        phone: [],
        birthdate: [],
        address: [],
        city: [],
        state: [],
        neighborhood: [],
        speciality: [],
        email: [],
        password: [],
        password_confirmed: []
    }
}

const resetFormData = () => {
    formData.value = {
        type_document: '',
        document: '',
        first_name: '',
        last_name: '',
        sex: '',
        phone: '',
        birthdate: '',
        address: '',
        city: '',
        state: '',
        neighborhood: '',
        speciality: '',
        email: '',
        password: '',
        password_confirmed: ''        
    };
};

const fetchDataFromApi = async () => {
    try {
        let currentId = 1;
        const  { data, message } = await useApi("medico");
        rows.value = data.map((item) => ({ ...item, index: currentId++ }));
        totalRows.value = data.length;
    } catch (error) {
        console.error('Error fetching data from API:', error);
    }
};

const discardButton = ref(null);

const createMedico = async () => {
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
        await useApi("medicos", "POST", formData.value);
        Swal.fire({
            title: 'Éxito!',
            text: 'Medico creado correctamente!',
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

    const data = await useApi("medicos" + user.id);

    if (data.message == "Medico found") {
        id = user.id
        formData.value.type_document = data.data.type_document
        formData.value.document = data.data.document
        formData.value.first_name = data.data.first_name
        formData.value.last_name = data.data.last_name
        formData.value.speciality = data.data.speciality
        formData.value.sex = data.data.sex
        formData.value.phone = data.data.phone
        formData.value.birthdate = data.data.birthdate
        formData.value.email = data.data.email
        formData.value.address = data.data.address
        formData.value.city = data.data.city
        formData.value.state = data.data.state
        formData.value.neighborhood = data.data.neighborhood
    };
    console.log(id)
};

const EditMedico = async (user) => {

    try {
        const datosActualizados = {
            type_document: formData.value.type_document,
            document: formData.value.document,
            first_name: formData.value.first_name,
            last_name: formData.value.last_name,
            speciality: formData.value.speciality,
            sex: formData.value.sex,
            phone: formData.value.phone,
            birthdate: formData.value.birthdate,
            email: formData.value.email,
            address: formData.value.address,
            city: formData.value.city,
            state: formData.value.state,
            neighborhood: formData.value.neighborhood,
        };

        await useApi("medico" + id, "PUT", datosActualizados);

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

    if (result.isConfirmed) {
        try {
            await useApi("eps" + id, "DELETE");

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