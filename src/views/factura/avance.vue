<template>
    <div class="layout-px-spacing">
        <teleport to="#breadcrumb">
            <ul class="navbar-nav flex-row">
                <li>
                    <div class="page-header">
                        <nav class="breadcrumb-one" aria-label="breadcrumb">
                            <ol class="breadcrumb">
                                <li class="breadcrumb-item"><a href="javascript:;">Facturacion</a></li>
                                <li class="breadcrumb-item active" aria-current="page"><span>Revisar Factura</span></li>
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
                                                        <div class="col-sm-6 col-12 me-auto">
                                                            <div class="d-flex">
                                                                <img class="company-logo"
                                                                    src="/src/assets/images/cork-logo.png" alt="company" />
                                                                <h3 class="in-heading align-self-center">Cork Inc.</h3>
                                                            </div>
                                                        </div>

                                                        <div class="col-sm-6 text-sm-end">
                                                            <p class="inv-list-number"><span class="inv-title">Fact :
                                                                </span> <span class="inv-number">#{{
                                                                    params.next_invoice_number }}</span></p>
                                                        </div>

                                                        <div class="col-sm-6 align-self-center mt-3">
                                                            <p class="inv-street-addr">XYZ Delta Street</p>
                                                            <p class="inv-email-address">info@company.com</p>
                                                            <p class="inv-email-address">(120) 456 789</p>
                                                        </div>
                                                        <div class="col-sm-6 align-self-center mt-3 text-sm-end">
                                                            <p class="inv-created-date">
                                                                <span class="inv-title">Fecha Inicial : </span>
                                                                <input class="border-0 fw-bold" type="date"
                                                                    v-model="params.date_consult">
                                                            </p>
                                                            <p class="inv-created-date">
                                                                <span class="inv-title">Fecha Final : </span>
                                                                <input class="border-0 fw-bold" type="date"
                                                                    v-model="params.due_date">
                                                                <br>
                                                                <template v-if="errors.due_date.length > 0">
                                                                    <b :key="e" v-for="e in errors.due_date" class="text-danger">
                                                                        {{ e }}
                                                                    </b>
                                                                </template>
                                                            </p>
                                                        </div>
                                                    </div>
                                                </div>

                                                <div class="inv--detail-section inv--customer-detail-section">
                                                    <div class="row">
                                                        <div class="col-xl-8 col-lg-7 col-md-6 col-sm-4 align-self-center">
                                                            <p class="inv-to">Facturar a</p>
                                                        </div>

                                                        <div
                                                            class="col-xl-4 col-lg-5 col-md-6 col-sm-8 align-self-center order-sm-0 order-1 inv--payment-info">
                                                            <h6 class="inv-title">Informacion de Pago:</h6>
                                                        </div>

                                                        <div class="col-xl-8 col-lg-7 col-md-6 col-sm-4">
                                                            <p class="inv-customer-name">{{ params.pacient }}</p>
                                                            <p class="inv-street-addr">{{ params.address }}</p>
                                                            <p class="inv-email-address">{{ params.email }}</p>
                                                            <p class="inv-email-address">{{ params.phone }}</p>
                                                        </div>

                                                        <div
                                                            class="col-xl-4 col-lg-5 col-md-6 col-sm-8 col-12 order-sm-0 order-1">
                                                            <div class="inv--payment-info">
                                                                <p><span class="inv-subtitle">Bank Name:</span> <span>Bank
                                                                        of America</span></p>
                                                                <p><span class="inv-subtitle">Account Number: </span>
                                                                    <span>1234567890</span>
                                                                </p>
                                                                <p><span class="inv-subtitle">SWIFT code:</span>
                                                                    <span>VS70134</span>
                                                                </p>
                                                                <p><span class="inv-subtitle">Country: </span> <span>United
                                                                        States</span></p>
                                                            </div>
                                                        </div>
                                                    </div>
                                                </div>

                                                <div class="inv--product-table-section">
                                                    <div class="table-responsive">
                                                        <table class="table table-hover">
                                                            <thead>
                                                                <tr>
                                                                    <th>S.NO</th>
                                                                    <th>ITEMS</th>
                                                                    <th>QTY</th>
                                                                    <th class="text-end">PRECIO</th>
                                                                    <th class="text-end">TOTAL</th>
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
                                                <div class="inv--total-amounts">
                                                    <div class="row mt-4">
                                                        <div class="col-sm-5 col-12 order-sm-0 order-1"></div>
                                                        <div class="col-sm-7 col-12 order-sm-1 order-0">
                                                            <div class="text-sm-end">
                                                                <div class="row">
                                                                    <div class="col-sm-8 col-7">
                                                                        <p class="">Subtotal:</p>
                                                                    </div>
                                                                    <div class="col-sm-4 col-5">
                                                                        <p id="priceDisplay" class="">${{ params.price }}
                                                                        </p>
                                                                    </div>
                                                                    <div class="col-sm-8 col-7">
                                                                        <p class="">Impuestos:</p>
                                                                    </div>
                                                                    <div class="col-sm-4 col-5">
                                                                        <input class="border-0 text-center"
                                                                            style="width: 40px; margin-right: -5px"
                                                                            type="number" v-model="params.taxes">
                                                                            <br>
                                                                            <template v-if="errors.taxes.length > 0">
                                                                                <b :key="e" v-for="e in errors.taxes" class="text-danger">
                                                                                    {{ e }}
                                                                                </b>
                                                                            </template>
                                                                    </div>
                                                                    <div class="col-sm-8 col-7">
                                                                        <p class="discount-rate">Descuento:</p>
                                                                    </div>
                                                                    <div class="col-sm-4 col-5">
                                                                        <input class="border-0 text-center"
                                                                            style="width: 40px; margin-right: -5px"
                                                                            type="number" v-model="params.discounts">
                                                                            <br>
                                                                            <template v-if="errors.discounts.length > 0">
                                                                                <b :key="e" v-for="e in errors.discounts" class="text-danger">
                                                                                    {{ e }}
                                                                                </b>
                                                                            </template>
                                                                    </div>
                                                                    <div class="col-sm-8 col-7 grand-total-title">
                                                                        <h4 class="">Total:</h4>
                                                                    </div>
                                                                    <div class="col-sm-4 col-5 grand-total-amount">
                                                                        <h4 class="">${{ calculateTotal() }}</h4>
                                                                    </div>
                                                                </div>
                                                            </div>
                                                        </div>
                                                    </div>
                                                    <div id="preview-field" class="field-wrapper input">
                                                        <div class="field-wrapper input">
                                                            <label for="fullname" class="col-form-label fw-bold">Estado de Pago</label>
                                                            <select v-model="params.status" class="mb-4 form-select w-25 border-0">
                                                                <option value="" disabled selected>Estado</option>
                                                                <option value="pagado">Pagado</option>
                                                                <option value="pendiente">Pendiente</option>
                                                            </select>                                                                
                                                        </div>                                                        
                                                        <template v-if="errors.status.length > 0">
                                                            <b :key="e" v-for="e in errors.status" class="text-danger">
                                                                {{ e }}
                                                            </b>
                                                        </template>
                                                    </div>
                                                </div>

                                                <div class="inv--note">
                                                    <div class="row mt-4">
                                                        <div class="col-sm-12 col-12 order-sm-0 order-1">
                                                            <p>Nota: El cuidado de la salud es la base para una vida plena y
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
                                            <a href="javascript:;" class="btn btn-primary btn-send"  @click="CreateInvoices">Enviar Factura</a>
                                        </div>
                                        <div class="col-xl-12 col-md-3 col-sm-6">
                                            <a href="javascript:;" class="btn btn-secondary btn-print action-print"
                                                @click="print()">Imprimir</a>
                                        </div>
                                        <div class="col-xl-12 col-md-3 col-sm-6">
                                            <a href="javascript:;" class="btn btn-success btn-download">Descargar</a>
                                        </div>
                                        <div class="col-xl-12 col-md-3 col-sm-6">
                                            <router-link to="/invoices/edit"
                                                class="btn btn-dark btn-edit">Editar</router-link>
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
import { useRoute } from "vue-router";

import { useMeta } from "/src/composables/use-meta";
import { useApi } from '/src/composables/use-api';
useMeta({ title: "Revisar Factura" });

const route = useRoute();

const id = ref('');

onMounted(async () => {
    id.value = route.params.id;
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
    
    console.log("que sale", has_error)
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
        });
    }  catch (error) {
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

    return total;
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

</script>
