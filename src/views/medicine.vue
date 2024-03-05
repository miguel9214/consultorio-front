<template>
    <div class="layout-px-spacing">
        <div class="seperator-header layout-top-spacing mb-4">
            <button type="button" class="btn btn-success me-3" data-bs-toggle="modal"
                data-bs-target="#modalCrearMedicamento">Crear</button>
        </div>
        <teleport to="#breadcrumb">
            <ul class="navbar-nav flex-row">
                <li>
                    <div class="page-header">
                        <nav class="breadcrumb-one" aria-label="breadcrumb">
                            <ol class="breadcrumb">
                                <li class="breadcrumb-item">
                                    <a href="javascript:;">DataTables</a>
                                </li>
                                <li class="breadcrumb-item active" aria-current="page">
                                    <span>Sorting</span>
                                </li>
                            </ol>
                        </nav>
                    </div>
                </li>
            </ul>
        </teleport>

        <div class="row layout-top-spacing">
            <div class="col-xl-12 col-lg-12 col-sm-12 layout-spacing">
                <div class="panel br-6 p-0">
                    <div class="vue3-datatable">
                        <vue3-datatable :rows="rows" :columns="cols" :totalRows="rows?.length" :sortable="true">
                            <template #actions="data">
                                <div class="flex">
                                    <button type="button" class="btn btn-success me-3"
                                    data-bs-toggle="modal" data-bs-target="#modalEditarMedicamento"
                                        @click="viewMedicine(data.value)">Editar</button>
                                    <button type="button" class="btn btn-danger"
                                        @click="deleteMedicine(data.value.id)">Eliminar</button>
                                </div>
                            </template>
                        </vue3-datatable>                        
                    </div>
                </div>
            </div>
        </div>
    </div>

    <div class="modal fade" id="modalCrearMedicamento" tabindex="-1" role="dialog" aria-labelledby="exampleModalLabel" aria-hidden="true">
        <div class="modal-dialog modal-lg" role="document">
            <div class="modal-content">
                <div class="modal-header">
                    <h5 class="modal-title" id="exampleModalLabel">Crear Medicamento</h5>
                    <button type="button" data-dismiss="modal" data-bs-dismiss="modal" aria-label="Close"
                        class="btn-close" @click="resetFormData"></button>
                </div>
                <div class="modal-body">
                    <div class="row">
                        <div class="">
                            <form class="text-start">
                                <div class="form">
                                    <!-- CODIGO MEDICAMENTO-->
                                    <div id="code-field" class="field-wrapper input">
                                        <label for="fullname" class="col-form-label p-1 fs-6 fw-bold">Codigo</label>
                                        <input v-model="formData.code" type="text" class="form-control" tabindex="1" />
                                        <template v-if="errors.code.length > 0">
                                            <b :key="e" v-for="e in errors.code" class="text-danger">
                                                {{ e }}
                                            </b>
                                        </template>
                                    </div>
                                    <!-- NOMBRE MEDICAMENTO -->
                                    <div id="name-field" class="field-wrapper input mt-2">
                                        <label for="fullname" class="col-form-label p-1 fs-6 fw-bold">Nombre</label>
                                        <input v-model="formData.name" type="text" class="form-control" tabindex="3" />

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
                    <a href="javascript:void(0)"  data-bs-dismiss="modal">
                        <button type="button" class="btn btn-success" @click="CreateMedicine">Crear</button>
                    </a>
                </div>
            </div>
        </div>
    </div>

    <div class="modal fade" id="modalEditarMedicamento" tabindex="-1" role="dialog" aria-labelledby="exampleModalLabel" aria-hidden="true">
        <div class="modal-dialog modal-lg" role="document">
            <div class="modal-content">
                <div class="modal-header">
                    <h5 class="modal-title" id="exampleModalLabel">Editar Medicamento</h5>
                    <button type="button" data-dismiss="modal" data-bs-dismiss="modal" aria-label="Close"
                        class="btn-close" @click="resetFormData"></button>
                </div>
                <div class="modal-body">
                    <div class="row">
                        <div class="">
                            <form class="text-start">
                                <div class="form">
                                    <!-- CODIGO MEDICAMENTO-->
                                    <div id="code-field" class="field-wrapper input mt-2">
                                        <label for="fullname" class="col-form-label p-1 fs-6 fw-bold">Codigo</label>
                                        <input v-model="formData.code" type="text" class="form-control" tabindex="4" />
    
                                        <template v-if="errors.code.length > 0">
                                            <b :key="e" v-for="e in errors.code" class="text-danger">
                                                {{ e }}
                                            </b>
                                        </template>
                                    </div>
                                    <!-- CODIGO MEDICAMENTO-->
                                    <div id="name-field" class="field-wrapper input">
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
                        <button type="button" class="btn btn-success" @click="EditMedicine">Editar</button>
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

    useMeta({ title: 'Medicine' });

    const cols = ref([
        { field: 'id', title: '#Id', isUnique: true },
        { field: 'code', title: 'Codigo' },
        { field: 'name', title: 'Nombre Medicamento' },
        { field: 'actions', title: 'Acciones' },

    ]);
    const rows = ref([]);
    const totalRows = ref(0);

    onMounted(async () => {
        await fetchDataFromApi();        
    });

    const formData = ref({
        code: '',
        name: '',
    });

    const errors = ref({
        code: [],
        name: [],
    });

    const errorsClear = () => {
        errors.value = {
            code: [],
            name: [],
        }
    }

    const resetFormData = () => {
        formData.value = {
            code: '',
            name: '',
        };
    };

    const fetchDataFromApi = async () => {
        try {
            let currentId = 1;
            const {data,message} = await useApi("medicine");
            rows.value = data.map((item) => ({ ...item, index: currentId++ }));
            totalRows.value = data.length;
        } catch (error) {
                console.error('Error fetching data from API:', error);
            }
    };

    const discardButton = ref(null);

    const CreateMedicine = async () => {
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
        await useApi("medicine","POST", formData.value);
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

    const viewMedicine = async (medicine) => {   

        const {data,message} = await useApi("medicine/"  + medicine.id);

        if(message == "Medicine found"){
            id = medicine.id
            formData.value.code = data.code
            formData.value.name = data.name
        };
    };

    const EditMedicine = async () => {

    try {
        const datosActualizados = {
            name: formData.value.name,
            code: formData.value.code,
        };

        await useApi("medicine/" + id,"PUT", datosActualizados);
        
        Swal.fire({
            title: 'Éxito!',
            text: 'Medicamento editado correctamente!',
            icon: 'success',
            confirmButtonText: '¡Entendido!'
        }).then(() => {
            if (discardButton.value) {
                discardButton.value.click();
            }
            resetFormData();
        });

    } catch (error) {
        console.error("Error al actualizar el Medicamento:", error);
    }

    fetchDataFromApi();

    };

    const deleteMedicine = async (id) => {
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
            await useApi("medicine/" + id,"DELETE");

            rows.value = rows.value.filter((d) => d.id != id);

            Swal.fire(
                'Eliminar!',
                'Tu archivo ha sido eliminado!.',
                'success'
            );
        } catch (error) {
            Swal.fire(
                'Error!',
                'Un error ocurrio mientras se elimina el archivo.',
                'error'
            );
        }
    }
};

</script>

