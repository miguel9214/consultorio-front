<template>
    <div class="layout-px-spacing apps-invoice-add">
        <teleport to="#breadcrumb">
            <ul class="navbar-nav flex-row">
                <li>
                    <div class="page-header">
                        <nav class="breadcrumb-one" aria-label="breadcrumb">
                            <ol class="breadcrumb">
                                <li class="breadcrumb-item"><a href="javascript:;">Facturas</a></li>
                                <li class="breadcrumb-item active" aria-current="page"><span>Crear</span></li>
                            </ol>
                        </nav>
                    </div>
                </li>
            </ul>
        </teleport>

        <div class="row invoice layout-top-spacing layout-spacing">
            <div class="col-xl-12 col-lg-12 col-md-12 col-sm-12 col-12">
                <div class="doc-container">
                    <div class="row">
                        <div class="col-xl-9">
                            <div class="invoice-content">
                                <div class="invoice-detail-body">
                                    <div class="invoice-detail-title">
                                        <div class="invoice-logo">
                                            <div class="upload pe-md-4">
                                                <input ref="fl_profile" type="file" class="d-none" accept="image/*" @change="change_file" />
                                                <img v-if="selected_file" :src="selected_file ? selected_file : '/src/assets/images/user-profile.jpeg'" alt="profile" class="profile-preview" @click="$refs.fl_profile.click()" />
                                                <div v-else class="profile-preview upload-preview" @click="$refs.fl_profile.click()">
                                                    <div>
                                                        <svg
                                                            xmlns="http://www.w3.org/2000/svg"
                                                            width="24"
                                                            height="24"
                                                            viewBox="0 0 24 24"
                                                            fill="none"
                                                            stroke="currentColor"
                                                            stroke-width="2"
                                                            stroke-linecap="round"
                                                            stroke-linejoin="round"
                                                            class="feather feather-upload-cloud"
                                                        >
                                                            <polyline points="16 16 12 12 8 16"></polyline>
                                                            <line x1="12" y1="12" x2="12" y2="21"></line>
                                                            <path d="M20.39 18.39A5 5 0 0 0 18 9h-1.26A8 8 0 1 0 3 16.3"></path>
                                                            <polyline points="16 16 12 12 8 16"></polyline>
                                                        </svg>
                                                    </div>
                                                    <div class="mt-2">Click to Upload Picture/Logo</div>
                                                </div>
                                            </div>
                                        </div>

                                        <div class="invoice-title">
                                            <input type="text" v-model="params.title" class="form-control" placeholder="Invoice Label" />
                                        </div>
                                    </div>

                                    <div class="invoice-detail-header">
                                        <div class="row justify-content-between">
                                            <div class="col-xl-5 invoice-address-company">
                                                <h4>De:-</h4>

                                                <div class="invoice-address-company-fields">
                                                    <div class="form-group row">
                                                        <label for="company-name" class="col-sm-3 col-form-label col-form-label-sm">Nombre</label>
                                                        <div class="col-sm-9">
                                                            <input type="text" v-model="params.from.name" id="company-name" class="form-control form-control-sm" placeholder="Business Name" />
                                                        </div>
                                                    </div>

                                                    <div class="form-group row">
                                                        <label for="company-email" class="col-sm-3 col-form-label col-form-label-sm">Correo</label>
                                                        <div class="col-sm-9">
                                                            <input type="text" v-model="params.from.email" id="company-email" class="form-control form-control-sm" placeholder="name@company.com" />
                                                        </div>
                                                    </div>

                                                    <div class="form-group row">
                                                        <label for="company-address" class="col-sm-3 col-form-label col-form-label-sm">Dirección</label>
                                                        <div class="col-sm-9">
                                                            <input type="text" v-model="params.from.address" id="company-address" class="form-control form-control-sm" placeholder="XYZ Street" />
                                                        </div>
                                                    </div>

                                                    <div class="form-group row">
                                                        <label for="company-phone" class="col-sm-3 col-form-label col-form-label-sm">Telefono</label>
                                                        <div class="col-sm-9">
                                                            <input type="text" v-model="params.from.phone" id="company-phone" class="form-control form-control-sm" placeholder="(123) 456 789" />
                                                        </div>
                                                    </div>
                                                </div>
                                            </div>

                                            <div class="col-xl-5 invoice-address-client">
                                                <h4>Cobrar a:-</h4>

                                                <div class="invoice-address-client-fields">
                                                    <div class="form-group row">
                                                        <label for="client-name" class="col-sm-3 col-form-label col-form-label-sm">Nombre</label>
                                                        <div class="col-sm-9">
                                                            <input type="text" v-model="params.to.name" id="client-name" class="form-control form-control-sm" placeholder="Client Name" />
                                                        </div>
                                                    </div>

                                                    <div class="form-group row">
                                                        <label for="client-email" class="col-sm-3 col-form-label col-form-label-sm">Correo</label>
                                                        <div class="col-sm-9">
                                                            <input type="text" v-model="params.to.email" id="client-email" class="form-control form-control-sm" placeholder="name@company.com" />
                                                        </div>
                                                    </div>
                                                    <div class="form-group row">
                                                        <label for="client-address" class="col-sm-3 col-form-label col-form-label-sm">Dirección</label>
                                                        <div class="col-sm-9">
                                                            <input type="text" v-model="params.to.address" id="client-address" class="form-control form-control-sm" placeholder="XYZ Street" />
                                                        </div>
                                                    </div>

                                                    <div class="form-group row">
                                                        <label for="client-phone" class="col-sm-3 col-form-label col-form-label-sm">Telefono</label>
                                                        <div class="col-sm-9">
                                                            <input type="text" v-model="params.to.phone" id="client-phone" class="form-control form-control-sm" placeholder="(123) 456 789" />
                                                        </div>
                                                    </div>
                                                </div>
                                            </div>
                                        </div>
                                    </div>

                                    <div class="invoice-detail-terms">
                                        <div class="row justify-content-between">
                                            <div class="col-md-3">
                                                <div class="form-group mb-4">
                                                    <label for="number">Numero Factura</label>
                                                    <input type="text" v-model="params.invoice_no" id="number" class="form-control form-control-sm" placeholder="#0001" />
                                                </div>
                                            </div>

                                            <div class="col-md-3">
                                                <div class="form-group mb-4">
                                                    <label for="date">Fecha Inicial</label>
                                                    <flat-pickr v-model="params.invoice_date" class="form-control form-control-sm flatpickr active" placeholder="Invoice Date"></flat-pickr>
                                                </div>
                                            </div>

                                            <div class="col-md-3">
                                                <div class="form-group mb-4">
                                                    <label for="due">Fecha Vencimiento</label>
                                                    <flat-pickr v-model="params.due_date" class="form-control form-control-sm flatpickr active" placeholder="Due Date"></flat-pickr>
                                                </div>
                                            </div>
                                        </div>
                                    </div>

                                    <div class="invoice-detail-items">
                                        <div class="table-responsive">
                                            <table class="table table-bordered item-table">
                                                <thead>
                                                    <tr>
                                                        <th class=""></th>
                                                        <th>Descripción</th>
                                                        <th class="text-end">Cantidad</th>
                                                        <th class="text-center">Impuesto</th>
                                                    </tr>
                                                </thead>
                                                <tbody>
                                                    <tr v-for="(item, index) in items" :key="index">
                                                        <td class="delete-item-row">
                                                            <ul class="table-controls">
                                                                <li>
                                                                    <a href="javascript:void(0);" class="delete-item" @click="remove_item(item)">
                                                                        <svg
                                                                            xmlns="http://www.w3.org/2000/svg"
                                                                            width="24"
                                                                            height="24"
                                                                            viewBox="0 0 24 24"
                                                                            fill="none"
                                                                            stroke="currentColor"
                                                                            stroke-width="2"
                                                                            stroke-linecap="round"
                                                                            stroke-linejoin="round"
                                                                            class="feather feather-x-circle"
                                                                        >
                                                                            <circle cx="12" cy="12" r="10"></circle>
                                                                            <line x1="15" y1="9" x2="9" y2="15"></line>
                                                                            <line x1="9" y1="9" x2="15" y2="15"></line>
                                                                        </svg>
                                                                    </a>
                                                                </li>
                                                            </ul>
                                                        </td>
                                                        <td class="description">
                                                            <input type="text" v-model="item.title" class="form-control form-control-sm" placeholder="Item Description" />
                                                            <textarea v-model="item.description" class="form-control" placeholder="Additional Details"></textarea>
                                                        </td>
                                                        <td class="text-end amount">
                                                            <span class="editable-amount mt-2">
                                                                <span class="currency">$</span> <span class="amount">{{ item.amount }}</span>
                                                            </span>
                                                        </td>
                                                        <td class="text-center tax">
                                                            <div class="checkbox-primary custom-control custom-checkbox">
                                                                <input type="checkbox" :id="`chktax-${index}`" v-model="item.is_tax" class="custom-control-input" />
                                                                <label class="custom-control-label" :for="`chktax-${index}`"></label>
                                                            </div>
                                                        </td>
                                                    </tr>
                                                </tbody>
                                            </table>
                                        </div>

                                        <button type="button" class="btn btn-secondary additem btn-sm" @click="add_item()">Add Item</button>
                                    </div>

                                    <div class="invoice-detail-total">
                                        <div class="row">
                                            <div class="col-md-6">
                                                <div class="form-group row invoice-created-by">
                                                    <label for="payment-method-account" class="col-sm-3 col-form-label col-form-label-sm">Account #:</label>
                                                    <div class="col-sm-9">
                                                        <input type="text" v-model="params.bank_info.no" id="payment-method-account" class="form-control form-control-sm" placeholder="Bank Account Number" />
                                                    </div>
                                                </div>

                                                <div class="form-group row invoice-created-by">
                                                    <label for="payment-method-bank-name" class="col-sm-3 col-form-label col-form-label-sm">Bank Name:</label>
                                                    <div class="col-sm-9">
                                                        <input type="text" v-model="params.bank_info.name" id="payment-method-bank-name" class="form-control form-control-sm" placeholder="Insert Bank Name" />
                                                    </div>
                                                </div>

                                                <div class="form-group row invoice-created-by">
                                                    <label for="payment-method-code" class="col-sm-3 col-form-label col-form-label-sm">SWIFT code:</label>
                                                    <div class="col-sm-9">
                                                        <input type="text" v-model="params.bank_info.swift_code" id="payment-method-code" class="form-control form-control-sm" placeholder="Insert Code" />
                                                    </div>
                                                </div>
                                            </div>

                                            <div class="col-md-6">
                                                <div class="totals-row">
                                                    <div class="invoice-totals-row invoice-summary-subtotal">
                                                        <div class="invoice-summary-label">Subtotal</div>
                                                        <div class="invoice-summary-value">
                                                            <div class="subtotal-amount"><span class="currency">$</span><span class="amount">100</span></div>
                                                        </div>
                                                    </div>
                                                    <div class="invoice-totals-row invoice-summary-total">
                                                        <div class="invoice-summary-label">Discount</div>
                                                        <div class="invoice-summary-value">
                                                            <div class="total-amount"><span class="currency">$</span><span>10</span></div>
                                                        </div>
                                                    </div>
                                                    <div class="invoice-totals-row invoice-summary-tax">
                                                        <div class="invoice-summary-label">Tax</div>
                                                        <div class="invoice-summary-value">
                                                            <div class="tax-amount">
                                                                <span>0%</span>
                                                            </div>
                                                        </div>
                                                    </div>
                                                    <div class="invoice-totals-row invoice-summary-balance-due">
                                                        <div class="invoice-summary-label">Total</div>
                                                        <div class="invoice-summary-value">
                                                            <div class="balance-due-amount"><span class="currency">$</span><span>90</span></div>
                                                        </div>
                                                    </div>
                                                </div>
                                            </div>
                                        </div>
                                    </div>

                                    <div class="invoice-detail-note">
                                        <div class="row">
                                            <div class="col-md-12 align-self-center">
                                                <div class="form-group row invoice-note">
                                                    <label for="invoice-detail-notes" class="col-sm-12 col-form-label col-form-label-sm">Notes:</label>
                                                    <div class="col-sm-12">
                                                        <textarea v-model="params.notes" rows="3" id="invoice-detail-notes" class="form-control" placeholder='Notes - For example, \"Thank you for doing business with us"'></textarea>
                                                    </div>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>

                        <div class="col-xl-3">
                            <div class="invoice-actions-btn m-0">
                                <div class="invoice-action-btn">
                                    <div class="row">
                                        <div class="col-xl-12 col-md-4">
                                            <a href="javascript:;" class="btn btn-primary btn-send">Send Invoice</a>
                                        </div>
                                        <div class="col-xl-12 col-md-4">
                                            <router-link to="/invoices/preview" class="btn btn-dark btn-preview">Avance</router-link>
                                        </div>
                                        <div class="col-xl-12 col-md-4">
                                            <a href="javascript:;" class="btn btn-success btn-download">Save</a>
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
    import "/src/assets/sass/apps/invoice-add.scss";

    //flatpickr
    import flatPickr from "vue-flatpickr-component";
    import "flatpickr/dist/flatpickr.css";
    import "/src/assets/sass/forms/custom-flatpickr.css";

    import { useMeta } from "/src/composables/use-meta";

    useMeta({ title: "Crear Factura" });

    const items = ref([]);
    const selected_file = ref(null);
    const params = ref({
        title: "",
        invoice_no: "",
        status: "",
        from: { name: "Consultorio SAS", email: "consultorio@company.com.co", address: "Cra 29 # 1 - 23", phone: "3143470843" },
        to: { name: "", email: "", address: "", phone: ""},
        invoice_date: "",
        due_date: "",
        bank_info: { no: "", name: "", swift_code: "", country: "" },
        notes: "",
    });
    const currency_list = ref([]);
    const selected_currency = ref({ key: "USD - US Dollar", thumb: "flags/en.png" });
    const tax_type_list = ref([]);
    const selected_tax_type = ref({ key: "None", value: null });
    const discount_list = ref([]);
    const selected_discount = ref({ key: "None", value: null, type: "" });

    onMounted(() => {
        //set default data
        items.value.push({ id: 1, title: "", description: "", rate: 0, quantity: 0, amount: 100, is_tax: false });

        let dt = new Date();
        params.value.invoice_date = JSON.parse(JSON.stringify(dt));
        dt.setDate(dt.getDate() + 5);
        params.value.due_date = dt;

        //currency list
        currency_list.value = [
            { key: "USD - US Dollar", thumb: "flags/en.png" },
            { key: "GBP - British Pound", thumb: "flags/gbp.png" },
            { key: "IDR - Indonesian Rupiah", thumb: "flags/idr.png" },
            { key: "INR - Indian Rupee", thumb: "flags/inr.png" },
            { key: "BRL - Brazilian Real", thumb: "flags/brl.png" },
            { key: "EUR - Germany (Euro)", thumb: "flags/de.png" },
            { key: "TRY - Turkish Lira", thumb: "flags/tr.png" },
        ];

        //tax type list
        tax_type_list.value = [
            { key: "Deducted", value: 10 },
            { key: "Per Item", value: 5 },
            { key: "On Total", value: 25 },
            { key: "None", value: null },
        ];

        //discount list
        discount_list.value = [
            { key: "Percent", value: 10, type: "percent" },
            { key: "Flat Amount", value: 25, type: "amount" },
            { key: "None", value: null, type: "" },
        ];

    });

    const change_file = (event) => {
        selected_file.value = URL.createObjectURL(event.target.files[0]);
    };

    const add_item = () => {
        let max_id = 0;
        if (items.value && items.value.length) {
            max_id = items.value.reduce((max, character) => (character.id > max ? character.id : max), items.value[0].id);
        }
        items.value.push({ id: max_id + 1, title: "", description: "", rate: 0, quantity: 0, amount: 0, is_tax: false });
    };

    const remove_item = (item) => {
        items.value = items.value.filter((d) => d.id != item.id);
    };
</script>
