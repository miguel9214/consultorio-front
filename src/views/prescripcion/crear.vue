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
                                                            <p class="inv-street-addr">Fecha: <span id="current-date"
                                                                    class="">{{ formattedDate }}</span></p>
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
                                                                    <th>Medicamento</th>
                                                                    <th>Tratamiento</th>
                                                                    <th class="text-end">Dosis Medicina</th>
                                                                    <th class="text-end">Instrucciones</th>
                                                                </tr>
                                                            </thead>
                                                            <tbody>
                                                                <tr v-for="(prescription, index) in prescriptionList"
                                                                    :key="index">
                                                                    <td>{{ index + 1 }}</td>
                                                                    <td>{{ prescription.medicine_code }}</td>
                                                                    <td>{{ prescription.medicine_name }}</td>
                                                                    <td>{{ prescription.treatment }}</td>
                                                                    <td class="text-end">{{ prescription.dose }}</td>
                                                                    <td class="text-end">{{
                                                                        prescription.additional_instructions }}</td>
                                                                </tr>
                                                            </tbody>
                                                        </table>
                                                    </div>
                                                </div>

                                                <div class="modal fade" id="modalEditarPrescripcion" tabindex="-1"
                                                    role="dialog" aria-labelledby="exampleModalLabel"
                                                    aria-hidden="true">
                                                    <div class="modal-dialog modal-xl" role="document">
                                                        <div class="modal-content">
                                                            <div class="modal-header">
                                                                <h5 class="modal-title" id="exampleModalLabel">Editar
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
                                                                            <input
                                                                                v-model="paramsPrescription.date_prescription"
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
                                                                                <tr v-for="(item, index) in prescriptionDataEdit"
                                                                                    :key="index">
                                                                                    <td class="delete-item-row">
                                                                                        <ul class="table-controls">
                                                                                            <li>
                                                                                                <a href="javascript:void(0);"
                                                                                                    class="delete-item"
                                                                                                    @click="remove_item_Edit(item.prescription_id)">
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
                                                                                            v-model="item.medicine_code"
                                                                                            class="form-control form-control-sm"
                                                                                            placeholder="AB1" />
                                                                                    </td>
                                                                                    <td class="description">
                                                                                        <select
                                                                                            v-model="item.medicine_id" @change="selectCodeMedi(index)"
                                                                                            class="form-select w-100">
                                                                                            <option style="margin: 1px"
                                                                                                disabled selected>
                                                                                                Medicamentos</option>
                                                                                            <option
                                                                                                v-for="medicine in medicineList"
                                                                                                :value="medicine.id"
                                                                                                :key="medicine.id"
                                                                                                :disabled="isMedicineSelected(medicine)">
                                                                                                {{ medicine.name }}
                                                                                            </option>
                                                                                        </select>
                                                                                        <textarea
                                                                                            v-model="item.treatment"
                                                                                            class="form-control"
                                                                                            placeholder="Tratamiento">
                                                                                        </textarea>
                                                                                    </td>
                                                                                    <td class="dosis">
                                                                                        <input type="text"
                                                                                            v-model="item.dose"
                                                                                            class="form-control form-control-sm"
                                                                                            placeholder="mg, mm, ml..." />
                                                                                    </td>
                                                                                    <td class="text-end qty">
                                                                                        <textarea
                                                                                            v-model="item.additional_instructions"
                                                                                            class="form-control m-0"
                                                                                            placeholder="..."></textarea>
                                                                                    </td>
                                                                                </tr>
                                                                            </tbody>
                                                                        </table>
                                                                    </div>
                                                                </div>
                                                                <button type="button"
                                                                    class="btn btn-secondary additem btn-sm"
                                                                    @click="add_item()">Agregar</button>
                                                            </div>
                                                            <div class="modal-footer">
                                                                <a href="javascript:void(0)" ref="discardButton"
                                                                    data-bs-dismiss="modal">
                                                                    <button type="button" class="btn btn-danger"
                                                                        @click="resetFormData">Descartar</button>
                                                                </a>
                                                                <a href="javascript:void(0)" data-bs-dismiss="modal">
                                                                    <button type="button" class="btn btn-success"
                                                                        @click="CreatPrescription()">Guardar</button>
                                                                </a>
                                                            </div>
                                                        </div>
                                                    </div>
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
                                                data-bs-toggle="modal" data-bs-target="#modalEditarPrescripcion"
                                                @click="openEditModal(id)">Guardar
                                                Prescripción</a>
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
    showPrescription(id.value);
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

//CREAR PRESCRIPCION
const discardButton = ref(null);

const selectedMedicine = ref([]);

const add_item = () => {
    prescriptionDataEdit.value.push(
        {
            prescription_id: "",
            medicine_id: "",
            medicine_name: "",
            medicine_code: "",
            dose: "",
            treatment: "",
            additional_instructions: "",
            date_prescription: "",
        },
    );
    selectedMedicine.value.push('');
};

const selectCodeMedi = (index) =>{
    const id = prescriptionDataEdit.value[index].medicine_id;
    const result = medicineList.value.filter((medicine)=>medicine.id === id)

    prescriptionDataEdit.value[index].medicine_code = result[0].code;
    prescriptionDataEdit.value[index].dose = result[0].dosage;
    prescriptionDataEdit.value[index].medicine_name = result[0].name;

}

const remove_item = (index) => {
    paramsPrescription.value.medicines.splice(index, 1);
    selectedMedicine.value.splice(index, 1);
};

//EDITAR PRESCRIPCION
const prescriptionDataEdit = ref([]);
const prescriptionIds = ref([]);

const viewPrescription = async (prescriptionId) => {
    try {
        const { data, message } = await useApi('prescriptionConsultation/' + prescriptionId);
        if (message == 'Prescription found - viewPrescription') {
            prescriptionDataEdit.value = data;
            paramsPrescription.value.date_prescription = data[0].date_prescription;

            prescriptionIds.value = data.map(item => item.prescription_id);
        }
    } catch (error) {
        console.error('Error:', error);
    }
};

const CreatPrescription = async () => {
    try {
        const prescriptionData = {
            date_prescription: paramsPrescription.value.date_prescription,
            medicines: prescriptionDataEdit.value.map(item => ({
                medicine_id: item.medicine_id,
                dose: item.dose,
                treatment: item.treatment,
                additional_instructions: item.additional_instructions
            })),
            consultation_id: id.value,
        };

        console.log(prescriptionData);

        await useApi('prescription', 'POST', prescriptionData);

        Swal.fire({
            title: 'Éxito!',
            text: 'Prescripción creada correctamente!',
            icon: 'success',
            confirmButtonText: '¡Entendido!',
        }).then((result) => {
            if (result.isConfirmed) {
                document.querySelector('[data-bs-dismiss="modal"]').click();
                resetFormData();
                window.location.reload();
            }
        });
    } catch (error) {
        console.log(error);
        Swal.fire('Error!', 'El medicamento ya ha sido prescrito para esta consulta.', 'error');
    }
};

const openEditModal = (prescriptionId) => {
    viewPrescription(prescriptionId);
};

const remove_item_Edit = async (prescription_id) => {
    const result = await Swal.fire({
        title: '¿Estás seguro?',
        text: '¡No podrás revertir esto!',
        icon: 'warning',
        showCancelButton: true,
        confirmButtonColor: '#3085d6',
        cancelButtonColor: '#d33',
        confirmButtonText: 'Sí, bórralo!',
    });

    if (result.isConfirmed) {
        try {
            await useApi('prescription/' + prescription_id, 'DELETE');

            prescriptionDataEdit.value = prescriptionDataEdit.value.filter(item => item.prescription_id !== prescription_id);

            Swal.fire('Eliminado!', 'Tu registro ha sido eliminado!', 'success');

        } catch (error) {
            Swal.fire('Error!', 'Ha ocurrido un error al intentar eliminar el registro.', 'error');
        }
    }
};

//LISTAR MEDICAMENTO
const medicineList = ref([]);

const showMedicine = async () => {
    try {
        const { data, message } = await useApi('medicine');
        medicineList.value = data;
    } catch (error) {
        console.error('Error al obtener los medicamentos', error);
    }
};

//LISTAR PRESCRIPTION
const prescriptionList = ref([]);

const showPrescription = async (id) => {
    try {
        const { data, message } = await useApi('prescription/' + id);
        prescriptionList.value = data;
    } catch (error) {
        console.error('Error al obtener las prescripciones', error);
    }
};

//MEDICINA SELECCIONADA
const isMedicineSelected = (medicine) => {
    return prescriptionDataEdit.value.some(selectedMedicine => selectedMedicine.medicine_id === medicine.id);
};

//FECHA ACTUAL
const currentDate = new Date();
const formattedDate = currentDate.getDate() + '-' + (currentDate.getMonth() + 1) + '-' + currentDate.getFullYear();

//IMPRIMIR PRESCRIPCION
const print = () => {
    window.print();
};
</script>
