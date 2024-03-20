<template>
    <div class="layout-px-spacing">
        <teleport to="#breadcrumb">
            <ul class="navbar-nav flex-row">
                <li>
                    <div class="page-header">
                        <nav class="breadcrumb-one" aria-label="breadcrumb">
                            <ol class="breadcrumb">
                                <li class="breadcrumb-item"><a href="javascript:;">Prescripcion</a></li>
                                <li class="breadcrumb-item active" aria-current="page"><span>Crear Prescripcion</span>
                                </li>
                            </ol>
                        </nav>
                    </div>
                </li>
            </ul>
        </teleport>

        <div class="row invoice layout-top-spacing layout-spacing apps-invoice">
            <div class="col-xl-12 col-lg-12 col-md-12 col-sm-12 col-12">
                <div class="doc-container">
                    <div class="row">
                        <div class="col-xl-9">
                            <div class="invoice-container">
                                <div class="invoice-inbox">
                                    <div id="ct" class="">
                                        <div class="invoice-00001">
                                            <div class="content-section">
                                                <div class="inv--head-section inv--detail-section">
                                                    <div class="row">
                                                        <div class="col-sm-3 col-12 me-auto">
                                                            <div class="d-flex">
                                                                <img class="company-logo"
                                                                    src="/src/assets/images/cork-logo.png"
                                                                    alt="company" />
                                                                <h3 class="in-heading align-self-center">Cork Inc.</h3>
                                                            </div>
                                                        </div>

                                                        <div class="col-sm-6 text-center">
                                                            <p class="inv-street-addr"
                                                                style="font-weight: 600; color: #0e1726">CLINICA DE
                                                                ESPECIALISTAS MARIA AUXILIADORA</p>
                                                            <p class="inv-email-address"
                                                                style="font-weight: 600; color: #0e1726">Dirección:
                                                                Calle 5 N° 32 - 07</p>
                                                            <p class="inv-email-address"
                                                                style="font-weight: 600; color: #0e1726">NIT:
                                                                800197217-9</p>
                                                            <p class="inv-email-address"
                                                                style="font-weight: 600; color: #0e1726">Ciudad:
                                                                AGUACHICA</p>
                                                            <p class="inv-email-address"
                                                                style="font-weight: 600; color: #0e1726">Orden CONSULTA
                                                            </p>
                                                        </div>
                                                        <div class="col-sm-3 text-sm-end">
                                                            <p class="inv-street-addr">Fecha: <span id="current-date" class="">{{ formattedDate }}</span></p>
                                                        </div>
                                                    </div>
                                                </div>

                                                <div class="inv--detail-section inv--customer-detail-section">
                                                    <div class="row">
                                                        <div
                                                            class="col-xl-8 col-lg-7 col-md-6 col-sm-4 align-self-center">
                                                            <p class="inv-to fs-8">Prescrito a</p>
                                                        </div>

                                                        <div
                                                            class="col-xl-4 col-lg-5 col-md-6 col-sm-8 align-self-center order-sm-0 order-1 inv--payment-info">
                                                            <h6 class="inv-title"></h6>
                                                        </div>

                                                        <div class="col-xl-8 col-lg-7 col-md-6 col-sm-4">
                                                            <p class="inv-street-addr"
                                                                style="font-weight: 800; color: #0e1726">{{
                                                                params.pacient }}</p>
                                                            <p class="inv-street-addr">{{ params.address }}</p>
                                                            <p class="inv-email-address">{{ params.email }}</p>
                                                            <p class="inv-email-address">{{ params.phone }}</p>

                                                            <div class="mt-3">
                                                                <p class="inv-street-addr"
                                                                    style="font-weight: 800; color: #0e1726">Médico: {{
                                                                params.doctor }}</p>
                                                            </div>
                                                        </div>

                                                        <div
                                                            class="col-xl-4 col-lg-5 col-md-6 col-sm-8 col-12 order-sm-0 order-1">
                                                            <div class="inv--payment-info">
                                                                <p>
                                                                    <span class="inv-street-addr">Dcto:</span><span
                                                                        class="inv-street-addr"
                                                                        style="font-weight: 800; color: #0e1726">1065884745</span>
                                                                </p>
                                                                <p><span class="inv-street-addr">Plan:</span><span>PLAN
                                                                        UNICO</span></p>
                                                                <p><span class="inv-street-addr">Vigencia:</span><span>30
                                                                        dias</span></p>
                                                                <p>
                                                                    <span class="inv-street-addr">Hab: </span>
                                                                    <span>4A</span>
                                                                </p>
                                                            </div>
                                                        </div>
                                                    </div>
                                                </div>

                                                <div class="inv--product-table-section">
                                                    <div class="table-responsive">
                                                        <table class="table table-hover">
                                                            <thead>
                                                                <tr>
                                                                    <th>It</th>
                                                                    <th>Codigo</th>
                                                                    <th>Descripcion</th>
                                                                    <th>Tratamiento</th>
                                                                    <th class="text-end">Dosis Medicina</th>
                                                                    <th class="text-end">Instrucciones</th>
                                                                </tr>
                                                            </thead>
                                                            <tbody>
                                                                <tr>
                                                                    <td>1</td>
                                                                    <td>2</td>
                                                                    <td>1</td>
                                                                    <td>4</td>
                                                                    <td class="text-end">5</td>
                                                                    <td class="text-end">5</td>
                                                                </tr>
                                                            </tbody>
                                                        </table>
                                                    </div>
                                                </div>

                                                <div class="modal fade" id="modalPrescripcion" tabindex="-1"
                                                    role="dialog" aria-labelledby="exampleModalLabel"
                                                    aria-hidden="true">
                                                    <div class="modal-dialog modal-xl" role="document">
                                                        <div class="modal-content">
                                                            <div class="modal-header">
                                                                <h5 class="modal-title" id="exampleModalLabel">Crear
                                                                    Prescripción</h5>
                                                                <button type="button" data-dismiss="modal"
                                                                    data-bs-dismiss="modal" aria-label="Close"
                                                                    class="btn-close" @click="resetFormData"></button>
                                                            </div>
                                                            <div class="invoice-detail-items">
                                                                <div class="modal-body">
                                                                    <div class="col-md-3">
                                                                        <div class="form-group d-flex">
                                                                            <label for="date"
                                                                                class="m-2 text-black">Fecha:
                                                                            </label>
                                                                            <input v-model="paramsPrescription.date_prescription"
                                                                                type="date"
                                                                                class="form-control form-control-sm"
                                                                                id="invoiceDate"
                                                                                placeholder="Invoice Date">
                                                                        </div>
                                                                        <template
                                                                            v-if="errors.date_prescription.length > 0">
                                                                            <b :key="e"
                                                                                v-for="e in errors.date_prescription"
                                                                                class="text-danger">
                                                                                {{ e }}
                                                                            </b>
                                                                        </template>
                                                                    </div>
                                                                    <div class="table-responsive">
                                                                        <table class="table table-bordered item-table">
                                                                            <thead>
                                                                                <tr>
                                                                                    <th class=""></th>
                                                                                    <th class="">Codigo</th>
                                                                                    <th>Description Medicamento</th>
                                                                                    <th class="">Dosis</th>
                                                                                    <th class="text-end w-25">
                                                                                        Instrucciones Adicionales</th>
                                                                                </tr>
                                                                            </thead>
                                                                            <tbody>
                                                                                <tr v-for="(item, index) in selectedMedicine"
                                                                                    :key="index">
                                                                                    <td class="delete-item-row">
                                                                                        <ul class="table-controls">
                                                                                            <li>
                                                                                                <a href="javascript:void(0);"
                                                                                                    class="delete-item"
                                                                                                    @click="remove_item(index)">
                                                                                                    <svg xmlns="http://www.w3.org/2000/svg"
                                                                                                        width="24"
                                                                                                        height="24"
                                                                                                        viewBox="0 0 24 24"
                                                                                                        fill="none"
                                                                                                        stroke="currentColor"
                                                                                                        stroke-width="2"
                                                                                                        stroke-linecap="round"
                                                                                                        stroke-linejoin="round"
                                                                                                        class="feather feather-x-circle">
                                                                                                        <circle cx="12"
                                                                                                            cy="12"
                                                                                                            r="10">
                                                                                                        </circle>
                                                                                                        <line x1="15"
                                                                                                            y1="9"
                                                                                                            x2="9"
                                                                                                            y2="15">
                                                                                                        </line>
                                                                                                        <line x1="9"
                                                                                                            y1="9"
                                                                                                            x2="15"
                                                                                                            y2="15">
                                                                                                        </line>
                                                                                                    </svg>
                                                                                                </a>
                                                                                            </li>
                                                                                        </ul>
                                                                                    </td>
                                                                                    <td class="codigo">
                                                                                        <input type="text"
                                                                                            v-model="paramsPrescription.medicines[index].medicine.code"
                                                                                            class="form-control form-control-sm"
                                                                                            placeholder="AB1" />
                                                                                    </td>
                                                                                    <td class="description">
                                                                                        <select v-model="paramsPrescription.medicines[index].medicine" class="form-select w-100">
                                                                                            <option style="margin: 1px" disabled selected>Medicamentos</option>
                                                                                            <option
                                                                                                v-for="medicine in medicineList"
                                                                                                :value="{ id: medicine.id, name: medicine.name, code: medicine.code }"
                                                                                                :key="medicine.id"
                                                                                                :disabled="isMedicineSelected(medicine)">
                                                                                                {{ medicine.name }}
                                                                                            </option>
                                                                                        </select>
                                                                                        <textarea
                                                                                            v-model="paramsPrescription.medicines[index].treatment"
                                                                                            class="form-control"
                                                                                            placeholder="Tratamiento"></textarea>
                                                                                    </td>
                                                                                    <td class="dosis">
                                                                                        <input type="text"
                                                                                            v-model="paramsPrescription.medicines[index].dose"
                                                                                            class="form-control form-control-sm"
                                                                                            placeholder="mg, mm, ml..." />
                                                                                    </td>
                                                                                    <td class="text-end qty">
                                                                                        <textarea
                                                                                            v-model="paramsPrescription.medicines[index].additional_instructions"
                                                                                            class="form-control m-0"
                                                                                            placeholder="..."></textarea>
                                                                                    </td>
                                                                                </tr>
                                                                            </tbody>
                                                                        </table>
                                                                    </div>
                                                                    <button type="button"
                                                                        class="btn btn-secondary additem btn-sm"
                                                                        @click="add_item()">Agregar</button>
                                                                </div>
                                                            </div>
                                                            <div class="modal-footer">
                                                                <a href="javascript:void(0)" ref="discardButton"
                                                                    data-bs-dismiss="modal">
                                                                    <button type="button" class="btn btn-danger"
                                                                        @click="resetFormData">Descartar</button>
                                                                </a>
                                                                <a href="javascript:void(0)" data-bs-dismiss="modal">
                                                                    <button type="button" class="btn btn-success"
                                                                        @click="createPrescripcion">Crear</button>
                                                                </a>
                                                            </div>
                                                        </div>
                                                    </div>
                                                </div>

                                                <div style="padding: 10px 25px 10px 33px">
                                                    <button type="button" class="btn btn-success me-3"
                                                        data-bs-toggle="modal"
                                                        data-bs-target="#modalPrescripcion">Prescripcion</button>
                                                </div>

                                                <div class="inv--note">
                                                    <div class="row mt-4">
                                                        <div class="col-sm-12 col-12 order-sm-0 order-1">
                                                            <p>Nota: El cuidado de la salud es la base para una vida
                                                                plena y satisfactoria.</p>
                                                        </div>
                                                    </div>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>

                        <div class="col-xl-3">
                            <div class="invoice-actions-btn">
                                <div class="invoice-action-btn">
                                    <div class="row">
                                        <div class="col-xl-12 col-md-3 col-sm-6">
                                            <a href="javascript:;" class="btn btn-primary btn-send"
                                                @click="CreateInvoices">Guardar</a>
                                        </div>
                                        <div class="col-xl-12 col-md-3 col-sm-6">
                                            <a href="javascript:;" class="btn btn-secondary btn-print action-print"
                                                @click="print()">Imprimir</a>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
import { onMounted, ref, computed } from 'vue';
import '/src/assets/sass/apps/invoice-preview.scss';
import '/src/assets/sass/apps/invoice-add.scss';
import { useRoute } from 'vue-router';

import { useMeta } from '/src/composables/use-meta';
import { useApi } from '/src/composables/use-api';
useMeta({ title: 'Revisar Factura' });

const route = useRoute();

const id = ref('');

onMounted(async () => {
    id.value = route.params.id;
    await invoiceConsultation(id.value);

    showMedicine();
});

const params = ref({
    doctor: '',
    pacient: '',
    phone: '',
    email: '',
});

const paramsPrescription = ref({
    date_prescription: '',
    code: [],
    treatment: [],
    dose: [],
    additional_instructions: [],
    medicines: [],
});

const errors = ref({
    date_prescription: [],
    medicine: [],
    code: [],
    treatment: [],
    dose: [],
    additional_instructions: [],
});

const errorsClear = () => {
    errors.value = {
        date_prescription: [],
        medicine: [],
        code: [],
        treatment: [],
        dose: [],
        additional_instructions: [],
    };
};

const invoiceConsultation = async (id) => {
    const { data, message } = await useApi('consultation/Invoice/' + id);
    params.value.doctor = data.doctor;
    params.value.pacient = data.pacient;
    params.value.phone = data.phone;
    params.value.email = data.email;
};

const resetFormData = () => {
    paramsPrescription.value.date_prescription = '';
    paramsPrescription.value.medicines = [];
    selectedMedicine.value = [];
};

const discardButton = ref(null);

const createPrescripcion = async () => {
    errorsClear();

    let has_error = false;
    Object.entries(paramsPrescription.value).forEach((f) => {
        const elemento = f[0];
        const value = f[1];
        if (value === '') {
            has_error = true;
            errors.value[elemento] = 'Este campo es obligatorio';
        }
    });

    if (has_error) return;

    try {
        const prescriptionData = {
            date_prescription: paramsPrescription.value.date_prescription,
            medicines: paramsPrescription.value.medicines.map(medicine => ({
                medicine_id: medicine.medicine.id,
                dose: medicine.dose,
                treatment: medicine.treatment,
                additional_instructions: medicine.additional_instructions
            })),
            consultation_id: id.value,
        };

        await useApi('prescription', 'POST', prescriptionData);

        Swal.fire({
            title: 'Éxito!',
            text: 'Prescripción creada correctamente!',
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
};

const selectedMedicine = ref([]);

const add_item = () => {
    paramsPrescription.value.medicines.push({
        medicine: {
            id: "",
            code: "",
            name: "",
        },
        dose: "",
        treatment: "",
        additional_instructions: "",
    });
    selectedMedicine.value.push('');
};

const remove_item = (index) => {
    paramsPrescription.value.medicines.splice(index, 1);
    selectedMedicine.value.splice(index, 1);
};

const print = () => {
    window.print();
};

//MEDICAMENTO

const medicineList = ref([]);

const showMedicine = async () => {
    try {
        const { data, message } = await useApi('medicine');
        medicineList.value = data;
    } catch (error) {
        console.error('Error al obtener los medicamentos', error);
    }
};

//MEDICINA SELECCIONADA
const isMedicineSelected = (medicine) => {
    return paramsPrescription.value.medicines.some(selectedMedicine => selectedMedicine.medicine.id === medicine.id);
};

//FECHA ACTUAL
const currentDate = new Date();
const formattedDate = currentDate.getDate() + '-' + (currentDate.getMonth() + 1) + '-' + currentDate.getFullYear();

</script>
