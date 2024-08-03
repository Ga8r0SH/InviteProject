<template>
    <div class="max-w-screen-xl m-auto">
        <div>
            <h1 class="text-center my-14 font-serif text-4xl mx-5">
                Подтвердите, пожалуйста, cвоё присутствие на торжестве
            </h1>
            <p class="flex justify-center font-serif mx-14 text-gray-600 text-[18px] text-center">
                ВАШИ ОТВЕТЫ НА ВОПРОСЫ
                ОЧЕНЬ ПОМОГУТ НАМ ПРИ ОРГАНИЗАЦИИ НАШЕГО ТОРЖЕСТВА
            </p>
        </div>
        <div class="adp flex justify-between items-center my-5">
            <div class="flex w-full mx-7 h-auto mt-5">
                <img src="../../assets/Image/photo_2024-06-21_13-22-18.jpg" alt="" class="w-full h-full object-cover">
            </div>
            <div class="ml-8 w-2/3">
                <p class="text-gray-600 mt-8 text-xl">
                    <span class="font-semibold">
                        Мы будем ждать точный ответ до 15. 08. 2024,
                    </span>
                    <br> чтобы мы могли учесть все пожелания и организовать наше торжество наилучшим образом.
                </p>
                <form @submit.prevent="onSubmit" class="my-8 font-serif">
                    <div class="attendance-section">
                        <h3 class="mb-4 text-xl font-serif">Присутствие на торжестве</h3>
                        <div class="flex flex-col">
                            <label for="attending-yes" class="flex items-center mb-2">
                                <input type="radio" id="attending-yes" v-model="attending" :value="true" class="mr-2" />
                                <span class="text-sm">Я приду / Мы придем</span>
                            </label>

                            <label for="attending-no" class="flex items-center">
                                <input type="radio" id="attending-no" v-model="attending" :value="false" class="mr-2" />
                                <span class="text-sm">Прийти не получится</span>
                            </label>
                        </div>

                        <div class="plus-one-option mt-4 pl-5" v-if="attending">
                            <label for="bringing-plus-one" class="flex items-center">
                                <input type="checkbox" id="bringing-plus-one" v-model="bringingPlusOne" class="mx-2" />
                                <span class="text-sm">Я приду с партнером (+1)</span>
                            </label>
                        </div>
                    </div>

                    <div class="names-section mt-8">
                        <h3 class="font-bold mb-4">Имена</h3>
                        <div class="flex flex-wrap gap-4">
                            <div class="flex flex-col">
                                <label for="firstName" class="mb-2">Имя:</label>
                                <input type="text" id="firstName" v-model="firstName"
                                    class="max-w-[130px] rounded-md border border-gray-300 px-2 py-2" />
                            </div>
                            <div class="flex flex-col">
                                <label for="lastName" class="mb-2">Фамилия:</label>
                                <input type="text" id="lastName" v-model="lastName"
                                    class="max-w-[130px] rounded-md border border-gray-300 px-2 py-2" />
                            </div>
                        </div>

                        <div class="additional-names mt-4" v-if="bringingPlusOne">
                            <div class="flex flex-wrap gap-4">
                                <div class="flex flex-col">
                                    <label for="plusOneFirstName" class="mb-2">Имя партнера:</label>
                                    <input type="text" id="plusOneFirstName" v-model="plusOneFirstName"
                                        class="max-w-[150px] rounded-md border border-gray-300 px-2 py-2" />
                                </div>
                                <div class="flex flex-col">
                                    <label for="plusOneLastName" class="mb-2">Фамилия партнера:</label>
                                    <input type="text" id="plusOneLastName" v-model="plusOneLastName"
                                        class="max-w-[150px] rounded-md border border-gray-300 px-2 py-2" />
                                </div>
                            </div>
                        </div>
                    </div>

                    <div v-if="errors.length" class="bg-red-100 text-red-700 p-4 border border-red-300 rounded mt-4">
                        <ul>
                            <li v-for="error in errors" :key="error">{{ error }}</li>
                        </ul>
                    </div>

                    <div class="flex justify-center mt-16">
                        <span class="w-[640px] h-[1px] bg-gray-300 inline-block text-center clip-path-arrow"></span>
                    </div>

                    <div class="drink-preferences-section mt-8">
                        <h3 class="font-bold mb-1">Предпочтения в напитках</h3>
                        <span class="text-sm text-gray-500 bg-gray-200">можно выбрать несколько вариантов</span>
                        <div class="flex flex-wrap items-center mt-5">
                            <label for="redWine" class="flex items-center mb-2 mr-4">
                                <input type="checkbox" id="redWine" v-model="drinkPreferences" value="redWine"
                                    class="mr-2" />
                                <span class="text-sm">Красное вино</span>
                            </label>

                            <label for="whiteWine" class="flex items-center mb-2 mr-4">
                                <input type="checkbox" id="whiteWine" v-model="drinkPreferences" value="whiteWine"
                                    class="mr-2" />
                                <span class="text-sm">Белое вино</span>
                            </label>

                            <label for="cognac" class="flex items-center mb-2 mr-4">
                                <input type="checkbox" id="cognac" v-model="drinkPreferences" value="cognac"
                                    class="mr-2" />
                                <span class="text-sm">Коньяк</span>
                            </label>

                            <label for="champagne" class="flex items-center mb-2 mr-4">
                                <input type="checkbox" id="champagne" v-model="drinkPreferences" value="champagne"
                                    class="mr-2" />
                                <span class="text-sm">Шампанское</span>
                            </label>

                            <label for="nonAlcoholic" class="flex items-center mb-2">
                                <input type="checkbox" id="nonAlcoholic" v-model="drinkPreferences" value="nonAlcoholic"
                                    class="mr-2" />
                                <span class="text-sm">Что-то безалкогольное</span>
                            </label>
                        </div>
                    </div>

                    <button type="submit"
                        class="mt-12 bg-black text-white hover:bg-white hover:border hover:text-black font-bold py-3 px-5">Отправить</button>
                </form>
            </div>
        </div>
        <h1 class="text-4xl font-serif my-12 flex justify-center mx-5 text-center">
            Благодарим вас и с нетерпением ждем встречи на нашем празднике!
        </h1>
    </div>
</template>


<script setup>
import { ref, computed } from 'vue';
import axios from 'axios';

const attending = ref(null);
const bringingPlusOne = ref(false);
const firstName = ref('');
const lastName = ref('');
const plusOneFirstName = ref('');
const plusOneLastName = ref('');
const drinkPreferences = ref([]);
const errors = ref([]);

const isValid = computed(() => {
    errors.value = [];
    if (attending.value === null) errors.value.push('Необходимо указать, будете ли вы присутствовать.');
    if (attending.value && !firstName.value) errors.value.push('Необходимо указать ваше имя.');
    if (attending.value && !lastName.value) errors.value.push('Необходимо указать вашу фамилию.');
    if (attending.value && bringingPlusOne.value && (!plusOneFirstName.value || !plusOneLastName.value)) {
        errors.value.push('Необходимо указать имя и фамилию партнера.');
    }
    return errors.value.length === 0;
});

const onSubmit = async () => {
    if (!isValid.value) {
        return; 
    }

    const formData = {
        attending: attending.value,
        attending_with_partner: bringingPlusOne.value,
        first_name: firstName.value,
        last_name: lastName.value,
        partner_first_name: plusOneFirstName.value,
        partner_last_name: plusOneLastName.value,
        drink_preferences: drinkPreferences.value,
    };

    try {
        const response = await axios.post('http://y67534r6.beget.tech/api/responses', { formData: formData });
        console.log('Response from POST:', response.data);
        attending.value = null;
        bringingPlusOne.value = false;
        firstName.value = '';
        lastName.value = '';
        plusOneFirstName.value = '';
        plusOneLastName.value = '';
        drinkPreferences.value = [];
    } catch (error) {
        console.error('Ошибка при отправке данных:', error);
    }
};
</script>

<style scoped>
button {
    box-sizing: border-box;
    max-width: 130px;
    width: 100%;
    box-sizing: border-box;
    border: 1px solid black;
}

.names-section label {
    font-weight: bold;
}

.names-section input {
    max-width: 130px;
    width: 100%;
}

h1 {
    font-family: 'Times New Roman', serif;
}

p {
    font-family: 'Times New Roman', serif;
}

input[type="text"],
input[type="radio"],
input[type="checkbox"] {}


@media (max-width: 768px) {
    .adp {
        display: flex;
        justify-content: center;
        flex-wrap: wrap;
    }

}

.clip-path-arrow {
    clip-path: polygon(0 50%, 100% 50%, 50% 0, 50% 100%);
}
</style>