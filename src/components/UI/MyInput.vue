<template>
<div class="input-wrapper">
<label
        class="label"
        :for="nameInput"
>
    {{label}}
</label>
<textarea
        v-if="nameInput === 'descr'"
        :vlaue="modelValue"
        @input="updateInput"
        class="input__description"
        :type="typeInput"
        :name="nameInput"
        rows="50" cols="80"
        :minlength="minlength"
        :maxlength="maxlength"
        :placeholder="'От 2 до 5000 символов'"
        required
>
</textarea>
<input
            v-else-if="label === 'Телефон'"
            :vlaue="modelValue"
            @input="updateInput"
            class="input"
            :type="typeInput"
            :name="nameInput"
            :minlength="minlength"
            :maxlength="maxlength"
            v-maska="'+7##########'"
            :placeholder="'+79178612300'"
            required
/>
<input
            v-else-if="label === 'Email'"
            :vlaue="modelValue"
            @input="updateInput"
            class="input"
            :type="typeInput"
            :name="nameInput"
            :minlength="minlength"
            :maxlength="maxlength"
            :placeholder="'example@mail.com'"
            required
/>

<div v-else-if="label === 'Дата начала' || label === 'Дата окончания'"
     class="inputs__row__events"
>
    <div>
        <input
                :vlaue="modelValue"
                @input="updateInput"
                class="input__event"
                style="padding-left: 1.5vw"
                :type="typeInput"
                :name="nameInput"
                :minlength="minlength"
                :maxlength="maxlength"
                v-maska="'##.##.####'"
                :placeholder="'05.03.2022'"
                required
        />
    </div>
    <div class="input__svg">
        <svg width="18" height="17" viewBox="0 0 18 17" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M6.54011 1.15324H11.0769C11.3715 1.15324 11.6661 1.38388 11.6661 1.72986V2.01817C11.6661 2.30647 11.4305 2.59478 11.0769 2.59478H6.54011C6.24551 2.59478 5.95091 2.36414 5.95091 2.01817V1.72986C6.00983 1.38388 6.24551 1.15324 6.54011 1.15324ZM5.47955 11.1287H6.06875C6.36335 11.1287 6.65795 11.3594 6.65795 11.7054V11.8207C6.65795 12.109 6.42227 12.3973 6.06875 12.3973H5.47955C5.18496 12.3973 4.89036 12.1667 4.89036 11.8207V11.7054C4.89036 11.4171 5.18496 11.1287 5.47955 11.1287ZM8.54339 11.1287H9.13259C9.42719 11.1287 9.72179 11.3594 9.72179 11.7054V11.8207C9.72179 12.109 9.48611 12.3973 9.13259 12.3973H8.54339C8.24879 12.3973 7.95419 12.1667 7.95419 11.8207V11.7054C7.95419 11.4171 8.24879 11.1287 8.54339 11.1287ZM11.6072 11.1287H12.1964C12.491 11.1287 12.7856 11.3594 12.7856 11.7054V11.8207C12.7856 12.109 12.5499 12.3973 12.1964 12.3973H11.6072C11.3126 12.3973 11.018 12.1667 11.018 11.8207V11.7054C11.018 11.4171 11.3126 11.1287 11.6072 11.1287ZM2.41572 1.78752V2.07583C2.41572 2.30647 2.29788 2.53712 2.0622 2.59478C1.70868 2.71011 1.473 3.05608 1.473 3.45971V13.8389C1.473 14.0695 1.59084 14.3001 1.7676 14.4731C1.94436 14.6461 2.18004 14.7614 2.41572 14.7614H15.3192C15.8495 14.7614 16.2619 14.3578 16.2619 13.8389V3.45971C16.2619 3.22906 16.1441 2.99842 15.9673 2.82543C15.9084 2.76777 15.7905 2.65245 15.6727 2.59478C15.437 2.53712 15.3192 2.30647 15.3192 2.07583V1.78752C15.3192 1.61453 15.3781 1.44155 15.5549 1.32622C15.7316 1.2109 15.9084 1.2109 16.0851 1.26856C16.4387 1.38389 16.7333 1.55687 17.0279 1.84518C17.4403 2.24881 17.676 2.82543 17.676 3.45971V13.8389C17.676 15.1651 16.2619 16.203 15.0246 16.203H2.41572C1.7676 16.203 1.1784 15.9147 0.707039 15.511C0.2946 15.0497 0 14.4731 0 13.8389V3.45971C0 2.4218 0.707039 1.55687 1.64976 1.26856C1.82652 1.2109 2.00328 1.2109 2.18004 1.32622C2.29788 1.44155 2.41572 1.61453 2.41572 1.78752ZM8.54339 8.7646H9.13259C9.42719 8.7646 9.72179 8.99525 9.72179 9.34122V9.45655C9.72179 9.74486 9.48611 10.0332 9.13259 10.0332H8.54339C8.24879 10.0332 7.95419 9.80252 7.95419 9.45655V9.34122C7.95419 8.99525 8.24879 8.7646 8.54339 8.7646ZM11.6072 8.7646H12.1964C12.491 8.7646 12.7856 8.99525 12.7856 9.34122V9.45655C12.7856 9.74486 12.5499 10.0332 12.1964 10.0332H11.6072C11.3126 10.0332 11.018 9.80252 11.018 9.45655V9.34122C11.018 8.99525 11.3126 8.7646 11.6072 8.7646ZM5.47955 8.7646H6.06875C6.36335 8.7646 6.65795 8.99525 6.65795 9.34122V9.45655C6.65795 9.74486 6.42227 10.0332 6.06875 10.0332H5.47955C5.18496 10.0332 4.89036 9.80252 4.89036 9.45655V9.34122C4.89036 8.99525 5.18496 8.7646 5.47955 8.7646ZM5.47955 6.34281H6.06875C6.36335 6.34281 6.65795 6.57345 6.65795 6.91943V7.03475C6.65795 7.32306 6.42227 7.61137 6.06875 7.61137H5.47955C5.18496 7.61137 4.89036 7.38072 4.89036 7.03475V6.91943C4.89036 6.63112 5.18496 6.34281 5.47955 6.34281ZM8.54339 6.34281H9.13259C9.42719 6.34281 9.72179 6.57345 9.72179 6.91943V7.03475C9.72179 7.32306 9.48611 7.61137 9.13259 7.61137H8.54339C8.24879 7.61137 7.95419 7.38072 7.95419 7.03475V6.91943C7.95419 6.63112 8.24879 6.34281 8.54339 6.34281ZM11.6072 6.34281H12.1964C12.491 6.34281 12.7856 6.57345 12.7856 6.91943V7.03475C12.7856 7.32306 12.5499 7.61137 12.1964 7.61137H11.6072C11.3126 7.61137 11.018 7.38072 11.018 7.03475V6.91943C11.018 6.63112 11.3126 6.34281 11.6072 6.34281ZM14.1997 0.576619V3.6327C14.1997 3.92101 13.964 4.20932 13.6105 4.20932H13.3159C13.0213 4.20932 12.7267 3.97867 12.7267 3.6327V0.576619C12.7267 0.288309 12.9624 0 13.3159 0H13.6105C13.964 0 14.1997 0.230647 14.1997 0.576619ZM4.89036 0.576619V3.6327C4.89036 3.92101 4.65468 4.20932 4.30116 4.20932H4.06548C3.77088 4.20932 3.47628 3.97867 3.47628 3.6327V0.576619C3.47628 0.288309 3.71196 0 4.06548 0H4.36008C4.65468 0 4.89036 0.230647 4.89036 0.576619Z" fill="#9B63F8"/>
        </svg>
    </div>
</div>
    <div v-else-if="label === 'Время начала' || label === 'Время окончания'"
         class="inputs__row__events">
        <div>
            <input
                    :vlaue="modelValue"
                    @input="updateInput"
                    style="text-align: right;"
                    class="input__event"
                    :type="typeInput"
                    :name="nameInput"
                    :minlength="minlength"
                    :maxlength="maxlength"
                    v-maska="'##:##'"
                    :placeholder="'11:20'"
                    required
            />
        </div>
        <div class="input__svg">
            <svg width="17" height="17" viewBox="0 0 17 17" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M14.498 4.86347C14.1624 5.02582 14.022 5.42964 14.1844 5.76506C14.6279 6.68133 14.8527 7.66896 14.8527 8.70159C14.8527 12.4242 11.8241 15.4528 8.10149 15.4528C4.37891 15.4528 1.35025 12.4242 1.35025 8.70159C1.35025 4.97901 4.37891 1.95035 8.10149 1.95035C9.64409 1.95035 11.0932 2.45405 12.2927 3.40691C12.5836 3.63915 13.009 3.59052 13.2412 3.29862C13.4735 3.00688 13.4249 2.58196 13.1328 2.35005C11.7128 1.22149 9.92594 0.600098 8.10149 0.600098C3.63456 0.600098 0 4.23466 0 8.70159C0 13.1685 3.63456 16.8031 8.10149 16.8031C12.5684 16.8031 16.203 13.1685 16.203 8.70159C16.203 7.46375 15.9327 6.2775 15.3996 5.17713C15.2376 4.84089 14.8325 4.70079 14.498 4.86347Z" fill="#9B63F8"/>
                <path d="M8.10139 3.30054C7.72872 3.30054 7.42627 3.60299 7.42627 3.97566V8.70153C7.42627 9.0742 7.72872 9.37666 8.10139 9.37666H11.477C11.8497 9.37666 12.1521 9.0742 12.1521 8.70153C12.1521 8.32886 11.8497 8.02641 11.477 8.02641H8.77652V3.97566C8.77652 3.60299 8.47406 3.30054 8.10139 3.30054Z" fill="#9B63F8"/>
            </svg>
        </div>
    </div>
<input
        v-else
        :vlaue="modelValue"
        @input="updateInput"
        class="input"
        :type="typeInput"
        :name="nameInput"
        :minlength="minlength"
        :maxlength="maxlength"
        :placeholder="'От 2 до 1000 символов'"
        required
/>

</div>
</template>
<script>
import { maska } from 'maska'
export default {
  name: 'my-input',
  directives: { maska },
  props: {
    modelValue: [String, Number],
    input: {
      type: Object,
      required: {
        type: Boolean,
        default: true
      }
    },
    label: String,
    nameInput: String,
    typeInput: String,
    minlength: Number,
    maxlength: Number,
    pattern: String,
    placeholder: String

  },
  /* data () {
            return{
                minlength: 2,
                maxlength: 1000,
            }
        }, */
  methods: {
    updateInput (event) {
      this.$emit('update:modelValue', event.target.value)
    }
  }
}
</script>
<style lang="scss" scoped>
.input-wrapper{
    display: flex;
    flex-direction: column;
    box-sizing: border-box;
    width: 100%;
}
.label{
   font-weight: 600;
   font-size: 1rem;
   line-height: 20px;
    display: flex;
    box-sizing: border-box;
}
.input{
    display: flex;
    margin-top: 0.51%;
    border: 1px solid #CDB1FB;
    border-radius: 4px;
    height: 6vh;
    padding-left: 25px;
    padding-right: 25px;
    font-weight: 400;
    font-size: 16px;
    line-height: 20px;
    box-sizing: border-box;
}
.input__description{
    height: 193px;
    margin-top: 0.51%;
    border: 1px solid #CDB1FB;
    border-radius: 4px;
}
.input__event{
    font-weight: 400;
    font-size: 16px;
    line-height: 20px;
    width: 90%;
    border: none;
    height: 6vh;
}
.inputs__row__events{
    display: flex;
    flex-direction: row;
    margin-top: 0.51%;
    border: 1px solid #CDB1FB;
    border-radius: 4px;
    background-color: white;
}
.input__svg{
padding-top: 2vh;
padding-right: 1vh;
}
input:active, :hover, :focus {
    outline: 0;
    outline-offset: 0;
}
</style>
