<template>
    <div class="layout-px-spacing">
        <div class="seperator-header layout-top-spacing mb-4">
            <button type="button" class="btn btn-success me-3" data-bs-toggle="modal" data-bs-target="#modallg">Crear</button>
        </div>
        <div class="row layout-top-spacing">
            <div class="col-xl-12 col-lg-12 col-sm-12 layout-spacing">
                <div class="panel br-6 p-0">
                    <div class="vue3-datatable">
                        <vue3-datatable :rows="rows" :columns="cols" :totalRows="totalRows">
                            <template #actions="data">
                                <div class="flex">
                                    <button type="button" class="btn btn-success me-3" data-bs-toggle="modal" data-bs-target="#modalEditarEPS" @click="viewUser(data.value)">Editar</button>
                                    <button type="button" class="btn btn-danger me-3" @click="deleteUser(data.value.id)">Eliminar</button>
                                    <router-link :to="{name: 'invoices-preview', params: {id: data.value.id }}" class="btn me-2 btn-secondary"> Facturar </router-link>
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
                    <h5 class="modal-title" id="exampleModalLabel">Crear Consulta</h5>
                    <button type="button" data-dismiss="modal" data-bs-dismiss="modal" aria-label="Close" class="btn-close" @click="resetFormData"></button>
                </div>
                <div class="modal-body">
                    <div class="row">
                        <div class="col-md-6">
                            <form class="text-start">
                                <div class="form">
                                    <!-- Nombre Medico -->
                                    <div id="consultation-field" class="field-wrapper input">
                                        <label for="fullname" class="col-form-label p-1 fs-6 fw-bold">Nombre Medico</label>
                                        <div style="margin-top: 1px">
                                            <select v-model="formData.doctor_id" class="mb-4 form-select w-100" tabindex="1">
                                                <option style="margin: 1px" value="" disabled selected>Medicos</option>
                                                <option :value="doctor.id" :key="doctor.id" v-for="doctor in doctorList">{{ doctor.doctor }}</option>
                                            </select>
                                        </div>

                                        <template v-if="errors.doctor_id.length > 0">
                                            <b :key="e" v-for="e in errors.doctor_id" class="text-danger">
                                                {{ e }}
                                            </b>
                                        </template>
                                    </div>
                                    <!-- Tipo de Consulta -->
                                    <div id="consultation-field" class="field-wrapper input">
                                        <label for="fullname" class="col-form-label p-1 fs-6 fw-bold">Tipo de Consulta</label>
                                        <div style="margin-top: 1px">
                                            <select v-model="formData.consultation_type_id" class="mb-4 form-select w-100" tabindex="3">
                                                <option style="margin: 1px" value="" disabled selected>Tipo de Consulta</option>
                                                <option :value="consultation_type.id" :key="consultation_type.id" v-for="consultation_type in consultation_typeList">
                                                    {{ consultation_type.name }}
                                                </option>
                                            </select>
                                        </div>

                                        <template v-if="errors.consultation_type_id.length > 0">
                                            <b :key="e" v-for="e in errors.consultation_type_id" class="text-danger">
                                                {{ e }}
                                            </b>
                                        </template>
                                    </div>
                                    <!-- Fecha de Consulta -->
                                    <div id="consultation-field" class="field-wrapper input mt-2">
                                        <label for="fullname" class="col-form-label p-1 fs-6 fw-bold">Fecha de Consulta</label>
                                        <input v-model="formData.date" type="date" class="form-control" tabindex="5" />

                                        <template v-if="errors.date.length > 0">
                                            <b :key="e" v-for="e in errors.date" class="text-danger">
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
                                    <!-- Nombre Paciente -->
                                    <div id="consultation-field" class="field-wrapper input">
                                        <label for="fullname" class="col-form-label p-1 fs-6 fw-bold">Nombre Paciente</label>
                                        <div style="margin-top: 1px">
                                            <select v-model="formData.pacient_id" class="mb-4 form-select w-100" tabindex="2">
                                                <option style="margin: 1px" value="" disabled selected>Pacientes</option>
                                                <option :value="pacient.id" :key="pacient.id" v-for="pacient in pacientList">{{ pacient.patient }}</option>
                                            </select>
                                        </div>

                                        <template v-if="errors.pacient_id.length > 0">
                                            <b :key="e" v-for="e in errors.pacient_id" class="text-danger">
                                                {{ e }}
                                            </b>
                                        </template>
                                    </div>
                                    <!-- Paciente Consulta -->
                                    <div id="consultation-field" class="field-wrapper input">
                                        <div class="field-wrapper input">
                                            <label for="fullname" class="col-form-label p-1 fs-6 fw-bold">Estado del Paciente</label>
                                            <select v-model="formData.status" class="mb-4 form-select w-100" tabindex="4">
                                                <option value="" disabled selected>Seleccionar estado</option>
                                                <option value="completado">Completado</option>
                                                <option value="cancelado">Cancelado</option>
                                                <option value="pendiente">Pendiente</option>
                                                <option value="esperando">Esperando</option>
                                            </select>
                                            <template v-if="errors.status.length > 0">
                                                <b :key="e" v-for="e in errors.status" class="text-danger">
                                                    {{ e }}
                                                </b>
                                            </template>
                                        </div>
                                    </div>
                                    <!-- Hora de Consulta -->
                                    <div id="consultation-field" class="field-wrapper input mt-2">
                                        <label for="fullname" class="col-form-label p-1 fs-6 fw-bold">Hora de Consulta</label>
                                        <input v-model="formData.hour" type="time" class="form-control" tabindex="5" />

                                        <template v-if="errors.hour.length > 0">
                                            <b :key="e" v-for="e in errors.hour" class="text-danger">
                                                {{ e }}
                                            </b>
                                        </template>
                                    </div>
                                </div>
                            </form>
                        </div>
                        <!-- Observación de Consulta -->
                        <div id="observation-field" class="field-wrapper input mt-2">
                            <label for="observation" class="col-form-label p-1 fs-6 fw-bold">Observación de Consulta</label>
                            <textarea v-model="formData.observation" class="form-control" rows="4" tabindex="6"></textarea>

                            <template v-if="errors.observation.length > 0">
                                <b :key="e" v-for="e in errors.observation" class="text-danger">
                                    {{ e }}
                                </b>
                            </template>
                        </div>
                    </div>
                </div>
                <div class="modal-footer">
                    <a href="javascript:void(0)" data-bs-dismiss="modal">
                        <button type="button" class="btn btn-danger" @click="resetFormData">Descartar</button>
                    </a>
                    <a href="javascript:void(0)" data-bs-dismiss="modal">
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
                    <h5 class="modal-title" id="exampleModalLabel">Editar Consulta</h5>
                    <button type="button" data-dismiss="modal" data-bs-dismiss="modal" aria-label="Close" class="btn-close" @click="resetFormData"></button>
                </div>
                <div class="modal-body">
                    <div class="row">
                        <div class="col-md-6">
                            <form class="text-start">
                                <div class="form">
                                    <!-- Nombre Medico -->
                                    <div id="consultation-field" class="field-wrapper input">
                                        <label for="fullname" class="col-form-label p-1 fs-6 fw-bold">Nombre Medico</label>
                                        <div style="margin-top: 1px">
                                            <select v-model="formData.doctor_id" class="mb-4 form-select w-100" tabindex="1">
                                                <option style="margin: 1px" value="" disabled selected>Medicos</option>
                                                <option :value="doctor.id" :key="doctor.id" v-for="doctor in doctorList">{{ doctor.doctor }}</option>
                                            </select>
                                        </div>

                                        <template v-if="errors.doctor_id.length > 0">
                                            <b :key="e" v-for="e in errors.doctor_id" class="text-danger">
                                                {{ e }}
                                            </b>
                                        </template>
                                    </div>
                                    <!-- Tipo de Consulta -->
                                    <div id="consultation-field" class="field-wrapper input">
                                        <label for="fullname" class="col-form-label p-1 fs-6 fw-bold">Tipo de Consulta</label>
                                        <div style="margin-top: 1px">
                                            <select v-model="formData.consultation_type_id" class="mb-4 form-select w-100" tabindex="3">
                                                <option style="margin: 1px" value="" disabled selected>Tipo de Consulta</option>
                                                <option :value="consultation_type.id" :key="consultation_type.id" v-for="consultation_type in consultation_typeList">
                                                    {{ consultation_type.name }}
                                                </option>
                                            </select>
                                        </div>

                                        <template v-if="errors.consultation_type_id.length > 0">
                                            <b :key="e" v-for="e in errors.consultation_type_id" class="text-danger">
                                                {{ e }}
                                            </b>
                                        </template>
                                    </div>
                                    <!-- Fecha de Consulta -->
                                    <div id="consultation-field" class="field-wrapper input mt-2">
                                        <label for="fullname" class="col-form-label p-1 fs-6 fw-bold">Fecha de Consulta</label>
                                        <input v-model="formData.date" type="date" class="form-control" tabindex="5" />

                                        <template v-if="errors.date.length > 0">
                                            <b :key="e" v-for="e in errors.date" class="text-danger">
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
                                    <!-- Nombre Paciente -->
                                    <div id="consultation-field" class="field-wrapper input">
                                        <label for="fullname" class="col-form-label p-1 fs-6 fw-bold">Nombre Paciente</label>
                                        <div style="margin-top: 1px">
                                            <select v-model="formData.pacient_id" class="mb-4 form-select w-100" tabindex="2">
                                                <option style="margin: 1px" value="" disabled selected>Pacientes</option>
                                                <option :value="pacient.id" :key="pacient.id" v-for="pacient in pacientList">{{ pacient.patient }}</option>
                                            </select>
                                        </div>

                                        <template v-if="errors.pacient_id.length > 0">
                                            <b :key="e" v-for="e in errors.pacient_id" class="text-danger">
                                                {{ e }}
                                            </b>
                                        </template>
                                    </div>
                                    <!-- Paciente Consulta -->
                                    <div id="consultation-field" class="field-wrapper input">
                                        <div class="field-wrapper input">
                                            <label for="fullname" class="col-form-label p-1 fs-6 fw-bold">Estado del Paciente</label>
                                            <select v-model="formData.status" class="mb-4 form-select w-100" tabindex="4">
                                                <option value="" disabled selected>Seleccionar estado</option>
                                                <option value="completado">Completado</option>
                                                <option value="cancelado">Cancelado</option>
                                                <option value="pendiente">Pendiente</option>
                                                <option value="esperando">Esperando</option>
                                            </select>
                                            <template v-if="errors.status.length > 0">
                                                <b :key="e" v-for="e in errors.status" class="text-danger">
                                                    {{ e }}
                                                </b>
                                            </template>
                                        </div>
                                    </div>
                                    <!-- Hora de Consulta -->
                                    <div id="consultation-field" class="field-wrapper input mt-2">
                                        <label for="fullname" class="col-form-label p-1 fs-6 fw-bold">Hora de Consulta</label>
                                        <input v-model="formData.hour" type="time" class="form-control" tabindex="5" />

                                        <template v-if="errors.hour.length > 0">
                                            <b :key="e" v-for="e in errors.hour" class="text-danger">
                                                {{ e }}
                                            </b>
                                        </template>
                                    </div>
                                </div>
                            </form>
                        </div>
                        <!-- Observación de Consulta -->
                        <div id="observation-field" class="field-wrapper input mt-2">
                            <label for="observation" class="col-form-label p-1 fs-6 fw-bold">Observación de Consulta</label>
                            <textarea v-model="formData.observation" class="form-control" rows="4" tabindex="6"></textarea>

                            <template v-if="errors.observation.length > 0">
                                <b :key="e" v-for="e in errors.observation" class="text-danger">
                                    {{ e }}
                                </b>
                            </template>
                        </div>
                    </div>
                </div>
                <div class="modal-footer">
                    <a href="javascript:void(0)" ref="discardButton" data-bs-dismiss="modal">
                        <button type="button" class="btn btn-danger" @click="resetFormData">Descartar</button>
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
    import { onMounted, ref, onBeforeMount } from 'vue';
    import Vue3Datatable from '@bhplugin/vue3-datatable';

    import { useMeta } from '/src/composables/use-meta';
    import { useApi } from '../composables/use-api';
    useMeta({ title: 'Consultas' });

    onBeforeMount(() => {
        showConsultationType();
        showDoctor();
        showPatient();
    });

    const cols = ref([
        { field: 'index', title: '#Id', isUnique: true },
        { field: 'paciente', title: 'Paciente' },
        { field: 'doctor', title: 'Medicos' },
        { field: 'tipo_consulta', title: 'Tipo de Consulta' },
        { field: 'fecha', title: 'Fecha' },
        { field: 'hora', title: 'Hora' },
        { field: 'observacion', title: 'Observacion' },
        { field: 'estado', title: 'Estado' },
        { field: 'actions', title: 'Acciones' },
    ]);

    const rows = ref([]);
    const totalRows = ref(0);

    onMounted(async () => {
        await fetchDataFromApi();
    });

    const formData = ref({
        pacient_id: '',
        doctor_id: '',
        consultation_type_id: '',
        date: '',
        hour: '',
        observation: '',
        status: '',
    });

    const errors = ref({
        pacient_id: [],
        doctor_id: [],
        consultation_type_id: [],
        date: [],
        hour: [],
        observation: [],
        status: [],
    });

    const errorsClear = () => {
        errors.value = {
            pacient_id: [],
            doctor_id: [],
            consultation_type_id: [],
            date: [],
            hour: [],
            observation: [],
            status: [],
        };
    };

    const resetFormData = () => {
        formData.value = {
            pacient_id: '',
            doctor_id: '',
            consultation_type_id: '',
            date: '',
            hour: '',
            observation: '',
            status: '',
        };
    };

    const fetchDataFromApi = async () => {
        try {
            let currentId = 1;
            const { data, message } = await useApi('consultation');
            rows.value = data.map((item) => ({ ...item, index: currentId++ }));
            totalRows.value = data.length;
        } catch (error) {
            console.error('Error fetching data from API:', error);
        }
    };

    const discardButton = ref(null);

    const CreateEPS = async () => {
        errorsClear();

        let has_error = false;
        Object.entries(formData.value).forEach((f) => {
            const elemento = f[0];
            const value = f[1];
            if (value == '') {
                has_error = true;
                errors.value[elemento] = 'Este campo es obligatorio';
            }
        });

        if (has_error) return;

        try {
            await useApi('consultation', 'POST', formData.value);
            Swal.fire({
                title: 'Éxito!',
                text: 'Consulta creada correctamente!',
                icon: 'success',
                confirmButtonText: '¡Entendido!',
            }).then(() => {
                if (discardButton.value) {
                    discardButton.value.click();
                }
                resetFormData();
            });
        } catch (error) {
            const errors_api = error.errors;
            Object.entries(errors_api).forEach((e) => {
                const elemento = e[0];
                const mensaje = e[1];
                errors.value[elemento] = mensaje;
            });
        }

        fetchDataFromApi();
    };

    let id;

    const viewUser = async (user) => {
        const { data, message } = await useApi('consultation/' + user.id);

        if (message == 'Consultation found') {
            id = user.id;
            formData.value.pacient_id = data.pacient_id;
            formData.value.doctor_id = data.doctor_id;
            formData.value.consultation_type_id = data.consultation_type_id;
            formData.value.date = data.date;
            formData.value.hour = data.hour;
            formData.value.observation = data.observation;
            formData.value.status = data.status;
        }
    };

    const EditEPS = async (user) => {
        try {
            const datosActualizados = {
                pacient_id: formData.value.pacient_id,
                doctor_id: formData.value.doctor_id,
                consultation_type_id: formData.value.consultation_type_id,
                date: formData.value.date,
                hour: formData.value.hour,
                observation: formData.value.observation,
                status: formData.value.status,
            };

            await useApi('consultation/' + id, 'PUT', datosActualizados);

            Swal.fire({
                title: 'Éxito!',
                text: 'Consulta editada correctamente!',
                icon: 'success',
                confirmButtonText: '¡Entendido!',
            }).then(() => {
                if (discardButton.value) {
                    discardButton.value.click();
                }
                resetFormData();
            });
        } catch (error) {
            console.error('Error al actualizar la Consulta:', error);
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
            confirmButtonText: 'Sí, borralo!',
        });

        if (result.isConfirmed) {
            try {
                await useApi('consultation/' + id, 'DELETE');

                rows.value = rows.value.filter((d) => d.id != id);

                Swal.fire('Eliminar!', 'Tu archivo ha sido eliminado!.', 'success');
            } catch (error) {
                Swal.fire('Error!', 'An error occurred while deleting the record.', 'error');
            }
        }
    };

    const consultation_typeList = ref([]);

    const showConsultationType = async () => {
        try {
            const { data, message } = await useApi('consultationType');
            consultation_typeList.value = data;
        } catch (error) {
            console.error('Error al obtener los Tipos de Consultas', error);
        }
    };

    const doctorList = ref([]);

    const showDoctor = async () => {
        try {
            const { data, message } = await useApi('doctor');
            doctorList.value = data;
        } catch (error) {
            console.error('Error al obtener las Consultas', error);
        }
    };

    const pacientList = ref([]);

    const showPatient = async () => {
        try {
            const { data, message } = await useApi('pacient');
            pacientList.value = data;
        } catch (error) {
            console.error('Error al obtener las Consultas', error);
        }
    };

</script>
