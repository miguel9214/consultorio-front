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

</template>

<script setup>
import { onMounted, ref } from 'vue';
import Vue3Datatable from '@bhplugin/vue3-datatable';

import { useMeta } from '/src/composables/use-meta';
import { useApi  } from '../composables/use-api';
useMeta({ title: 'Consultas' });

const cols = ref([
    { field: 'index', title: '#Id', isUnique: true },
    { field: 'pacient_id', title: 'Paciente' },
    { field: 'doctor_id', title: 'Medicos' },
    { field: 'consultation_type_id', title: 'Tipo de Consulta' },
    { field: 'date', title: 'Fecha' },
    { field: 'observation', title: 'Observacion' },
    { field: 'status', title: 'Estado' },
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
    observation: '',
    status: '',
});

const errors = ref({
    pacient_id: [],
    doctor_id: [],
    consultation_type_id: [],
    date: [],
    observation: [],
    status: [],
});

const errorsClear = () => {
    errors.value = {
        pacient_id: [],
        doctor_id: [],
        consultation_type_id: [],
        date: [],
        observation: [],
        status: [],
    }
}

const resetFormData = () => {
    formData.value = {
        pacient_id: '',
        doctor_id: '',
        consultation_type_id: '',
        date: '',
        observation: '',
        status: '',
    };
};

const fetchDataFromApi = async () => {
    try {
        let currentId = 1;
        const {data,message} = await useApi("consultation");
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

    if (has_error) return;

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

        const {data,message} = await useApi("eps/"+user.id);
        console.log('data: ', data);

        if(message == "EPS found"){
            id = user.id
            formData.value.name = data.name
            formData.value.address = data.address
            formData.value.phone = data.phone
            formData.value.code = data.code
            formData.value.contract_start_date = data.contract_start_date
            formData.value.contract_end_date = data.contract_end_date                        
        };
        console.log(id)
};

const EditEPS = async (user) => {

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
