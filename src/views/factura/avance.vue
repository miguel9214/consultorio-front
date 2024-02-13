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
                                                                </span> <span class="inv-number">#{{ params.invoice_number }}</span></p>
                                                        </div>

                                                        <div class="col-sm-6 align-self-center mt-3">
                                                            <p class="inv-street-addr">XYZ Delta Street</p>
                                                            <p class="inv-email-address">info@company.com</p>
                                                            <p class="inv-email-address">(120) 456 789</p>
                                                        </div>
                                                        <div class="col-sm-6 align-self-center mt-3 text-sm-end">
                                                            <p class="inv-created-date"><span class="inv-title">Fecha Inicial
                                                                    : </span> <span class="inv-date">{{ params.start_date }}</span></p>
                                                            <p class="inv-due-date"><span class="inv-title">Fecha Vencimiento :
                                                                </span> <span class="inv-date">{{ params.due_date }}</span></p>
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
                                                
                                                <!-- <div class="inv--product-table-section">
                                                    <div class="table-responsive">
                                                        <table class="table table-hover">
                                                            <thead>
                                                                <tr>
                                                                    <th v-for="item in columns" :key="item.key" :class="[item.class]">
                                                                        {{ item.label }}
                                                                    </th>
                                                                </tr>
                                                            </thead>
                                                            <tbody>
                                                                <tr v-for="item in items" :key="item.id">
                                                                    <td>
                                                                        {{ item.id }}
                                                                    </td>
                                                                    <td>
                                                                        {{ item.title }}
                                                                    </td>
                                                                    <td>
                                                                        {{ item.quantity }}
                                                                    </td>
                                                                    <td class="text-end">${{ item.price }}</td>
                                                                    <td class="text-end">${{ item.amount }}</td>
                                                                </tr>
                                                            </tbody>
                                                        </table>
                                                    </div>
                                                </div> -->

                                                <div class="inv--product-table-section">
                                                    <div class="table-responsive">
                                                        <table class="table table-hover">
                                                            <thead>
                                                                <tr>
                                                                    <th>S.NO</th>
                                                                    <th>ITEMS</th>
                                                                    <th>QTY</th>
                                                                    <th class="text-end">PRICE</th>
                                                                    <th class="text-end">AMOUNT</th>
                                                                </tr>
                                                            </thead>
                                                            <tbody>
                                                                <tr>
                                                                    <td>1</td>
                                                                    <td>Consulta con {{ params.doctor }}</td>
                                                                    <td>1</td>
                                                                    <td class="text-end">${{ params.price }}</td>
                                                                    <td class="text-end">${{ params.total_amount }}</td>
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
                                                                        <p class="">{{ params.total_amount }}</p>
                                                                    </div>
                                                                    <div class="col-sm-8 col-7">
                                                                        <p class="">Impuestos:</p>
                                                                    </div>
                                                                    <div class="col-sm-4 col-5">
                                                                        <p class="">{{ params.taxes }}</p>
                                                                    </div>
                                                                    <div class="col-sm-8 col-7">
                                                                        <p class="discount-rate">Descuento: <span
                                                                                class="discount-percentage">{{ params.discounts }}</span></p>
                                                                    </div>
                                                                    <div class="col-sm-4 col-5">
                                                                        <p class="">{{ params.taxes }}</p>
                                                                    </div>
                                                                    <div class="col-sm-8 col-7 grand-total-title">
                                                                        <h4 class="">Total:</h4>
                                                                    </div>
                                                                    <div class="col-sm-4 col-5 grand-total-amount">
                                                                        <h4 class="">${{ params.amount_paid }}</h4>
                                                                    </div>
                                                                </div>
                                                            </div>
                                                        </div>
                                                    </div>
                                                </div>

                                                <div class="inv--note">
                                                    <div class="row mt-4">
                                                        <div class="col-sm-12 col-12 order-sm-0 order-1">
                                                            <p>Note: Thank you for doing Business with us.</p>
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
                                            <a href="javascript:;" class="btn btn-primary btn-send">Enviar Factura</a>
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

const items = ref([]);
const columns = ref([]);
const route = useRoute();

const id = ref('');

onMounted(() => {
    bind_data();
    id.value = route.params.id;
    invoiceConsultation(id.value);
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
    invoice_number: "",
    start_date: "",
    due_date: "",
    status_invoice: "",
    total_amount: "",
    discounts: "",
    taxes: "",
    amount_paid: "",
});


const bind_data = () => {
    columns.value = [
        { key: "id", label: "S.NO" },
        { key: "title", label: "ITEMS" },
        { key: "quantity", label: "QTY" },
        { key: "price", label: "PRICE", class: "text-end" },
        { key: "amount", label: "AMOUNT", class: "text-end" },
    ];
    items.value = [
        { id: 1, title: "Calendar App Customization", quantity: 1, price: "120", amount: "120" },
        { id: 2, title: "Chat App Customization", quantity: 1, price: "230", amount: "230" },
        { id: 3, title: "Laravel Integration", quantity: 1, price: "405", amount: "405" },
        { id: 4, title: "Backend UI Design", quantity: 1, price: "2500", amount: "2500" },
    ];
};


const print = () => {
    window.print();
};

const invoiceConsultation = async (id) => {
    const { data, message } = await useApi('consultation/Invoice/' +id);
    console.log('data: ', data);
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
    params.value.invoice_number = data.invoice_number
    params.value.start_date = data.start_date
    params.value.due_date = data.due_date
    params.value.status_invoice = data.status_invoice
    params.value.total_amount = data.total_amount
    params.value.taxes = data.taxes
    params.value.amount_paid = data.amount_paid

    console.log(params.value)
};

</script>
