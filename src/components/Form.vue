<template>
    <div>
        <form @submit.prevent='onSubmit'>
            <div class="flex-container">
                <div>
                    <span v-if='!($v.lastName.$dirty && !$v.lastName.required)'>Фамилия *</span>
                    <span v-else-if='$v.lastName.$dirty && !$v.lastName.required' class="invalid">Введите фамилию</span>
                    <br>
                    <input 
                        type="text"
                        v-model.trim="$v.lastName.$model"
                        :class='{invalid: ($v.lastName.$dirty && !$v.lastName.required)}'
                    >
                </div>
                <div>
                    <span v-if='!($v.firstName.$dirty && !$v.firstName.required)'>Имя *</span>
                    <span v-else-if='$v.firstName.$dirty && !$v.firstName.required' class="invalid">Введите имя</span>
                    <br>
                    <input
                        type="text"
                        v-model.trim="$v.firstName.$model"
                        :class='{invalid: ($v.firstName.$dirty && !$v.firstName.required)}'
                    >
                </div>
                <div>
                    <span>Отчество</span><br>
                    <input type="text">
                </div>
                <div>
                    <span v-if='!($v.dateOfBirth.$dirty && !$v.dateOfBirth.required)'>Дата рождения *</span>
                    <span v-else-if='$v.dateOfBirth.$dirty && !$v.dateOfBirth.required' class="invalid">Введите дату рождения</span>
                    <br>
                    <input 
                        type="date"
                        v-model.trim="$v.dateOfBirth.$model"
                        :class='{invalid: ($v.dateOfBirth.$dirty && !$v.dateOfBirth.required)}'
                    >
                </div>
                <div>
                    <span v-if='!(($v.phoneNumber.$dirty && !$v.phoneNumber.required) || ($v.phoneNumber.$dirty && !$v.phoneNumber.numeric) || ($v.phoneNumber.$dirty && !$v.phoneNumber.phoneLength))'>Номер телефона *</span>
                    <span v-else-if='($v.phoneNumber.$dirty && !$v.phoneNumber.required)' class="invalid">Введите номер телефона</span>
                    <span v-else-if='(($v.phoneNumber.$dirty && !$v.phoneNumber.numeric) || ($v.phoneNumber.$dirty && !$v.phoneNumber.phoneLength))' class="invalid">Некорректный номер</span>
                    <br>
                    <input 
                        type="tel"
                        v-model.trim="$v.phoneNumber.$model"
                        :class='{invalid: (($v.phoneNumber.$dirty && !$v.phoneNumber.required) || ($v.phoneNumber.$dirty && !$v.phoneNumber.numeric) || ($v.phoneNumber.$dirty && !$v.phoneNumber.phoneLength))}'
                    >
                </div>
                <div>
                    <span>Пол</span><br>
                    <input type="text">
                </div>
                <div>
                    <span v-if='!($v.clientGroup.$dirty && !$v.clientGroup.required)'>Группа клиентов *</span>
                    <span v-else-if='$v.clientGroup.$dirty && !$v.clientGroup.required' class="invalid">Выберите группу клиентов</span>
                    <br>
                    <select
                        multiple
                        v-model.trim="$v.clientGroup.$model"
                        :class='{invalid: ($v.clientGroup.$dirty && !$v.clientGroup.required)}'
                    >
                        <Option 
                        v-for='option of selectOptions.clientGroup'
                        :key='option.id'
                        :option='option'
                        />
                    </select>
                </div>
                <div>
                    <span>Лечащий врач</span><br>
                    <select>
                        <option selected disabled value="">Выберите лечащего врача</option>
                        <Option 
                        v-for='option of selectOptions.doctor'
                        :key='option.id'
                        :option='option'
                        />
                    </select>
                </div>
                <div class="checkboxblock">
                    <input id="checkbox" type="checkbox"><label for='checkbox'>Не отправлять СМС</label>
                </div>
                <hr color='#00D1FF'>
                <h2>адрес</h2>
                <div>
                    <span>Индекс</span><br>
                    <input type="text">
                </div>
                <div>
                    <span>Страна</span><br>
                    <input type="text">
                </div>
                <div>
                    <span>Область</span><br>
                    <input type="text">
                </div>
                <div>
                    <span v-if='!($v.city.$dirty && !$v.city.required)'>Город *</span>
                    <span v-else-if='$v.city.$dirty && !$v.city.required' class="invalid">Введите город</span>
                    <br>
                    <input
                        type="text"
                        v-model.trim="$v.city.$model"
                        :class='{invalid: ($v.city.$dirty && !$v.city.required)}'
                    >
                </div>
                <div>
                    <span>Улица</span><br>
                    <input type="text">
                </div>
                <div>
                    <span>Дом</span><br>
                    <input type="text">
                </div>
                <hr color='#00D1FF'>
                <h2>паспорт</h2>
                <div>
                    <span v-if='!($v.document.$dirty && !$v.document.required)'>Тип документа *</span>
                    <span v-else-if='$v.document.$dirty && !$v.document.required' class="invalid">Выберите тип документа</span>
                    <br>
                    <select
                        v-model.trim="$v.document.$model"
                        :class='{invalid: ($v.document.$dirty && !$v.document.required)}'
                    >
                        <option selected disabled value="">Выберите тип документа</option>
                        <Option 
                        v-for='option of selectOptions.document'
                        :key='option.id'
                        :option='option'
                        />
                    </select>
                </div>
                <div>
                    <span>Серия</span><br>
                    <input type="text">
                </div>
                <div>
                    <span>Номер</span><br>
                    <input type="text">
                </div>
                <div>
                    <span>Кем выдан</span><br>
                    <input type="text">
                </div>
                <div>
                    <span v-if='!($v.dateOfIssue.$dirty && !$v.dateOfIssue.required)'>Дата выдачи *</span>
                    <span v-else-if='$v.dateOfIssue.$dirty && !$v.dateOfIssue.required' class="invalid">Введите дату выдачи</span>
                    <br>
                    <input 
                        type="date"
                        v-model.trim="$v.dateOfIssue.$model"
                        :class='{invalid: ($v.dateOfIssue.$dirty && !$v.dateOfIssue.required)}'
                    >
                </div>
            </div>
            <button type="submit">Отправить</button><br>
            * Поле обязательное для заполнения.
        </form>
        <Success :show='successShow' />
    </div>
</template>

<script>

import {required, numeric} from 'vuelidate/lib/validators'
import Option from '@/components/Option.vue'
import Success from '@/components/Success.vue'

const phoneLength = (value) => value.indexOf('7') == 0 && value.length == 11

export default {
    data(){
      return {
        selectOptions: {
            clientGroup: [
                {id: 1, title: 'VIP', value: 'VIP'},
                {id: 2, title: 'Проблемные', value: 'problems'},
                {id: 3, title: 'ОМС', value: 'OMS'},
            ],
            doctor: [
                {id: 1, title: 'Иванов', value: 'Ivanov'},
                {id: 2, title: 'Захаров', value: 'Zaharov'},
                {id: 3, title: 'Чернышева', value: 'Chernysheva'},
            ],
            document: [
                {id: 1, title: 'Паспорт', value: 'passport'},
                {id: 2, title: 'Свидетельство о рождении', value: 'birth_certificate'},
                {id: 3, title: 'Вод. удостоверение', value: 'license'},
            ]
        },
        firstName: '',
        lastName: '',
        dateOfBirth: '',
        phoneNumber: '7',
        clientGroup: [],
        city: '',
        document: '',
        dateOfIssue: '',
        successShow: false
      }  
    },
    validations: {
        firstName: {required,},
        lastName: {required,},
        dateOfBirth: {required},
        phoneNumber: {required, numeric, phoneLength},
        clientGroup: {required},
        city: {required,},
        document: {required},
        dateOfIssue : {required},
    },
    components: {
        Option, Success
    },
    methods: {
        onSubmit(){
            if(this.$v.$invalid){
                this.$v.$touch()
                return
            }
        this.successShow = true
        setTimeout(()=>{this.successShow = false}, 3000)
        setTimeout(()=>{location.reload()}, 3000)
        }
    }
}
</script>

<style lang='sass' scoped>
    .flex-container
        display: flex
        justify-content: space-between
        flex-wrap: wrap

        @media all and (max-width: 1366px)
            justify-content: space-around
    form
        text-align: center

    span
        padding-left: 10px

    input
        box-sizing: border-box
        padding: 0.5px 10px
        width: 260px
        height: 35px
        border: 2px solid #00D1FF
        border-radius: 10px
        margin-top: 2px
        margin-bottom: 28px

        @media all and (max-width: 480px)
            width: 200px

    input:focus
        outline: none
        border-color: #1FF0FF

    select
        box-sizing: border-box
        padding: 5px 10px
        width: 260px
        min-height: 35px
        border: 2px solid #00D1FF
        border-radius: 10px
        margin-top: 2px
        margin-bottom: 28px

        @media all and (max-width: 480px)
            width: 200px

    select:focus
        outline: none
        border-color: #1FF0FF

    #checkbox
        width: auto
        position: relative
        top: 12px
        vertical-align: middle

    .checkboxblock
        width: 260px
        margin-top: 10px

    hr 
        width: 80%

    h2 
        width: 100%
        text-transform: uppercase
        font-size: 18px

    button
        width: 177px
        height: 55px
        border: 2px solid #00D1FF
        border-radius: 20px
        color: #00D1FF
        background-color: #fff
        font-weight: bold
        font-size: 18px
        text-transform: uppercase
        letter-spacing: 1.5px
        transition: 0.8s
        margin-bottom: 10px
    button:hover
        background-color: #00D1FF
        color: #fff
        cursor: pointer

    .invalid
        color: #FF3744
        border-color: #FF3744

    .invalid:focus
        border-color: #FF7D91
</style>