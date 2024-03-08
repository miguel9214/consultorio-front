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
                                                                style="font-weight: 600; color:#0e1726">CLINICA DE
                                                                ESPECIALISTAS MARIA AUXILIADORA</p>
                                                            <p class="inv-email-address"
                                                                style="font-weight: 600; color:#0e1726">Dirección: Calle
                                                                5 N° 32 - 07</p>
                                                            <p class="inv-email-address"
                                                                style="font-weight: 600; color:#0e1726">NIT: 800197217-9
                                                            </p>
                                                            <p class="inv-email-address"
                                                                style="font-weight: 600; color:#0e1726">Ciudad:
                                                                AGUACHICA</p>
                                                            <p class="inv-email-address"
                                                                style="font-weight: 600; color:#0e1726">Orden CONSULTA
                                                            </p>
                                                        </div>

                                                        <div class="col-sm-3 text-sm-end">
                                                            <p class="inv-street-addr">Fecha: {{ params.start_date }}
                                                            </p>
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
                                                                style="font-weight: 800; color:#0e1726">{{
                                                                params.pacient }}</p>
                                                            <p class="inv-street-addr">{{ params.address }}</p>
                                                            <p class="inv-email-address">{{ params.email }}</p>
                                                            <p class="inv-email-address">{{ params.phone }}</p>

                                                            <div class="mt-3">
                                                                <p class="inv-street-addr"
                                                                    style="font-weight: 800; color:#0e1726">Médico: {{
                                                                params.doctor }}</p>
                                                            </div>
                                                        </div>

                                                        <div
                                                            class="col-xl-4 col-lg-5 col-md-6 col-sm-8 col-12 order-sm-0 order-1">
                                                            <div class="inv--payment-info">
                                                                <p><span class="inv-street-addr">Dcto:</span><span
                                                                        class=" inv-street-addr"
                                                                        style="font-weight: 800; color:#0e1726">1065884745</span>
                                                                </p>
                                                                <p><span class="inv-street-addr">Plan:</span><span>PLAN
                                                                        UNICO</span></p>
                                                                <p><span class="inv-street-addr">Vigencia:</span><span>30
                                                                        dias</span></p>
                                                                <p><span class="inv-street-addr">Hab: </span>
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
                                                                    <th class="text-end">Dosis Medicina</th>
                                                                    <th class="text-end">Datos Clínicos</th>
                                                                </tr>
                                                            </thead>
                                                            <tbody>
                                                                <tr>
                                                                    <td>1</td>
                                                                    <td>{{ params.type_consult }}</td>
                                                                    <td>1</td>
                                                                    <td class="text-end">${{ params.price }}</td>
                                                                    <td class="text-end">${{ params.price }}
                                                                    </td>
                                                                </tr>
                                                            </tbody>
                                                        </table>
                                                    </div>
                                                </div>

                                                <div class="invoice-detail-items">
                                                    <div class="table-responsive">
                                                        <table class="table table-bordered item-table">
                                                            <thead>
                                                                <tr>
                                                                    <th class=""></th>
                                                                    <th>Description</th>
                                                                    <th class="">Rate</th>
                                                                    <th class="">Qty</th>
                                                                    <th class="text-end">Amount</th>
                                                                    <th class="text-center">Tax</th>
                                                                </tr>
                                                            </thead>
                                                            <tbody>
                                                                <tr>
                                                                    <td class="delete-item-row">
                                                                        <ul class="table-controls">
                                                                            <li>
                                                                                <a href="javascript:void(0);" class="delete-item" @click="remove_item(item)">
                                                                                    <svg
                                                                                        xmlns="http://www.w3.org/2000/svg"
                                                                                        width="24" height="24"
                                                                                        viewBox="0 0 24 24" fill="none"
                                                                                        stroke="currentColor"
                                                                                        stroke-width="2"
                                                                                        stroke-linecap="round"
                                                                                        stroke-linejoin="round"
                                                                                        class="feather feather-x-circle">
                                                                                        <circle cx="12" cy="12" r="10">
                                                                                        </circle>
                                                                                        <line x1="15" y1="9" x2="9"
                                                                                            y2="15"></line>
                                                                                        <line x1="9" y1="9" x2="15"
                                                                                            y2="15"></line>
                                                                                    </svg></a></li>
                                                                        </ul>
                                                                    </td>
                                                                    <td class="description"><input type="text"
                                                                            class="form-control form-control-sm"
                                                                            placeholder="Item Description"><textarea
                                                                            class="form-control"
                                                                            placeholder="Additional Details"></textarea>
                                                                    </td>
                                                                    <td class="rate"><input type="number"
                                                                            class="form-control form-control-sm"
                                                                            placeholder="Price"></td>
                                                                    <td class="text-end qty"><input type="number"
                                                                            class="form-control form-control-sm"
                                                                            placeholder="Quantity"></td>
                                                                    <td class="text-end amount"><span
                                                                            class="editable-amount mt-2"><span
                                                                                class="currency">$</span> <span
                                                                                class="amount">100</span></span></td>
                                                                    <td class="text-center tax">
                                                                        <div
                                                                            class="checkbox-primary custom-control custom-checkbox">
                                                                            <input type="checkbox" id="chktax-0"
                                                                                class="custom-control-input"><label
                                                                                class="custom-control-label"
                                                                                for="chktax-0"></label>
                                                                        </div>
                                                                    </td>
                                                                </tr>
                                                                <tr>
                                                                    <td class="delete-item-row">
                                                                        <ul class="table-controls">
                                                                            <li><a href="javascript:void(0);"
                                                                                    class="delete-item"><svg
                                                                                        xmlns="http://www.w3.org/2000/svg"
                                                                                        width="24" height="24"
                                                                                        viewBox="0 0 24 24" fill="none"
                                                                                        stroke="currentColor"
                                                                                        stroke-width="2"
                                                                                        stroke-linecap="round"
                                                                                        stroke-linejoin="round"
                                                                                        class="feather feather-x-circle">
                                                                                        <circle cx="12" cy="12" r="10">
                                                                                        </circle>
                                                                                        <line x1="15" y1="9" x2="9"
                                                                                            y2="15"></line>
                                                                                        <line x1="9" y1="9" x2="15"
                                                                                            y2="15"></line>
                                                                                    </svg></a></li>
                                                                        </ul>
                                                                    </td>
                                                                    <td class="description"><input type="text"
                                                                            class="form-control form-control-sm"
                                                                            placeholder="Item Description"><textarea
                                                                            class="form-control"
                                                                            placeholder="Additional Details"></textarea>
                                                                    </td>
                                                                    <td class="rate"><input type="number"
                                                                            class="form-control form-control-sm"
                                                                            placeholder="Price"></td>
                                                                    <td class="text-end qty"><input type="number"
                                                                            class="form-control form-control-sm"
                                                                            placeholder="Quantity"></td>
                                                                    <td class="text-end amount"><span
                                                                            class="editable-amount mt-2"><span
                                                                                class="currency">$</span> <span
                                                                                class="amount">0</span></span></td>
                                                                    <td class="text-center tax">
                                                                        <div
                                                                            class="checkbox-primary custom-control custom-checkbox">
                                                                            <input type="checkbox" id="chktax-1"
                                                                                class="custom-control-input"><label
                                                                                class="custom-control-label"
                                                                                for="chktax-1"></label>
                                                                        </div>
                                                                    </td>
                                                                </tr>
                                                            </tbody>
                                                        </table>
                                                    </div>
                                                    <button type="button" class="btn btn-secondary additem btn-sm"
                                                        @click="add_item()">Add Item</button>
                                                </div>

                                                <div class="inv--note">
                                                    <div class="row mt-4">
                                                        <div class="col-sm-12 col-12 order-sm-0 order-1">
                                                            <p>Nota: El cuidado de la salud es la base para una vida
                                                                plena y
                                                                satisfactoria.</p>
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
                                        <div class="col-xl-12 col-md-3 col-sm-6">
                                            <a href="javascript:;" class="btn btn-success btn-download">Descargar</a>
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
import { onMounted, ref } from "vue";
import "/src/assets/sass/apps/invoice-preview.scss";
import "/src/assets/sass/apps/invoice-add.scss";
import { useRoute } from "vue-router";

import { useMeta } from "/src/composables/use-meta";
import { useApi } from '/src/composables/use-api';
useMeta({ title: "Revisar Factura" });

const route = useRoute();

const id = ref('');

onMounted(async () => {
    items.value.push({ id: 1, title: "", description: "", rate: 0, quantity: 0, amount: 100, is_tax: false });

    id.value = route.params.id;
    console.log(id.value)
    await invoiceConsultation(id.value);
    calculateTotal();
});

const params = ref({
    doctor: "",
    pacient: "",
    date_consult: "",
    hour: "",
    observation: "",
    status_consult: "",
    type_consult: "",
    price: "",
    address: "",
    phone: "",
    email: "",
    next_invoice_number: "",
    invoice_number: '',
    start_date: '',
    due_date: '',
    status: '',
    total_amount: '',
    taxes: 0,
    discounts: 0,
    amount_paid: '',
});

const errors = ref({
    start_date: [],
    due_date: [],
    status: [],
    taxes: [],
    discounts: [],
});

const errorsClear = () => {
    errors.value = {
        start_date: [],
        due_date: [],
        status: [],
        taxes: [],
        discounts: [],
    };
};

const print = () => {
    window.print();
};

const CreateInvoices = async () => {

    errorsClear();

    let has_error = false;
    Object.entries(params.value).forEach((f) => {
        const elemento = f[0];
        console.log("elemento", elemento)
        const value = f[1];
        console.log("value", value)
        if (value == '') {
            has_error = true;
            errors.value[elemento] = 'Este campo es obligatorio';
        }
    });
    if (has_error) return;
    try {
        await useApi('invoice', 'POST', {
            invoice_number: params.value.next_invoice_number,
            start_date: params.value.date_consult,
            due_date: params.value.due_date,
            status: params.value.status,
            total_amount: params.value.price,
            taxes: params.value.taxes,
            discounts: params.value.discounts,
            amount_paid: params.value.amount_paid,
            consultation_id: id.value
        });
        Swal.fire({
            title: 'Éxito!',
            text: 'Factura creada correctamente!',
            icon: 'success',
            confirmButtonText: '¡Entendido!',
        }).then((result) => {
            if (result.isConfirmed) {
                window.location.href = 'http://localhost:5173/invoices/list';
            }
        });
    } catch (error) {
        console.error('Error en crear la factura:', error);
        Swal.fire({
            title: 'Error!',
            text: 'Hubo un problema al crear la factura. Por favor, complete todos los datos.',
            icon: 'error',
            confirmButtonText: '¡Entendido!'
        });
    }

};

const calculateTotal = () => {
    const subtotal = parseFloat(params.value.price);
    const taxes = parseFloat(params.value.taxes);
    const taxesDecimal = taxes / 100;
    const discounts = parseFloat(params.value.discounts);
    const discountsDecimal = discounts / 100;

    const valueTaxes = (subtotal * taxesDecimal) + subtotal;
    const total = valueTaxes - (valueTaxes * discountsDecimal);
    params.value.amount_paid = total;

    return total.toFixed(0);
};

const invoiceConsultation = async (id) => {
    const { data, message } = await useApi('consultation/Invoice/' + id);
    params.value.doctor = data.doctor
    params.value.pacient = data.pacient
    params.value.date_consult = data.date_consult
    params.value.hour = data.hour
    params.value.observation = data.observation
    params.value.status_consult = data.status_consult
    params.value.type_consult = data.type_consult
    params.value.price = data.price
    params.value.address = data.address
    params.value.phone = data.phone
    params.value.email = data.email
    params.value.next_invoice_number = data.next_invoice_number
    params.value.invoice_number = data.next_invoice_number
    params.value.start_date = data.date_consult
    params.value.total_amount = data.price
};

const items = ref([]);

const remove_item = (item) => {
    items.value = items.value.filter((d) => d.id != item.id);
};

const change_file = (event) => {
    selected_file.value = URL.createObjectURL(event.target.files[0]);
};

const add_item = () => {
    let max_id = 0;
    if (items.value && items.value.length) {
        max_id = items.value.reduce((max, character) => (character.id > max ? character.id : max), items.value[0].id);
    }
    items.value.push({ id: max_id + 1, title: "", description: "", rate: 0, quantity: 0, amount: 0, is_tax: false });
    console.log(items.value)
};

</script>
