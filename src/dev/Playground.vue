<template>
    <v-app>
        <v-container fluid grid-list-xl>
            <v-layout align-center wrap>
                {{fromData}}
                <lq-v-form
                    name="test_form"
                    :rules="rules"
                    ref="lqForm"
                    action="http://localhost:8080"
                    content-type="formdata"
                >
                    <v-text-field
                        id="namejhj"
                        @input="chala"
                        v-lq-model
                        value="sdqwdqwdw"
                        v-if="show"
                    />
                    <v-select
                        :items="items4"
                        v-lq-model="{id: 'select1'}"
                        value="Foo"
                        label="Standard"
                        v-if="show"
                    />
                    <v-checkbox
                        id="checkbox1"
                        v-if="show"
                        v-lq-model="{id: 'checkbox1'}"
                        label="Checkbox 1"
                    ></v-checkbox>
                    <v-checkbox id="checkbox2"  v-trap="checkbox"  label="Checkbox 1"></v-checkbox>
                    <!--  <v-radio-group v-lq-model="{id: 'radio1'}" id="radio1">
                        <v-radio v-for="n in 3" :key="n" :label="`Radio ${n}`" :value="n"></v-radio>
                    </v-radio-group>
                    <v-switch v-lq-model="{id: 'switch1'}" id="switch1" label="Switch 1:"></v-switch>-->
                    <!-- <input type="text" value="Test My Value" id="_pp" v-lq-model v-if="show" :keep-alive="false" /> -->

                    <button type="button" @click="() => show = !show">Show Hide</button>
                    <!-- <v-flex xs12 sm12>
                        <lq-v-date-range id="date_range" display-format="dd/MM/yyyy" />
                    </v-flex>
                    <v-flex xs12 sm12>
                        <lq-v-text-field
                            id="name"
                            label="Name"
                            hint="Type a Email only"
                            :persistent-hint="true"
                            autofocus
                            :clearable="true"
                            append-outer-icon="mdi-send"
                            @click:append-outer="sendMessage"
                        >
                            <template v-slot:prepend>
                                <select name="jhdkj">
                                    <option value="1">1</option>
                                    <option value="1">1</option>
                                    <option value="1">1</option>
                                    <option value="1">1</option>
                                    <option value="1">1</option>
                                    <option value="1">1</option>
                                </select>
                            </template>
                        </lq-v-text-field>
                    </v-flex>
                    <v-flex xs12 sm12>
                        mobile_no
                        <lq-v-select
                            id="mobile_no"
                            :options="items2"
                            :value="1"
                            label="Mobile Number"
                            :is-output-object="false"
                            validate-on-event="blur"
                            @change="SelectChange"
                            placeholder="Type Mobile Number jhere.."
                            item-value="id"
                            item-text="login"
                            clearable
                        ></lq-v-select>
                    </v-flex>
                    <v-flex xs12 sm12>
                        <lq-v-textarea id="textarea" :rows="2" />
                    </v-flex>
                    <v-flex xs12 sm12>
                        <lq-v-rating id="rating" :half-increments="true" :valueue="3" />
                    </v-flex>
                    <v-flex xs12 sm12 md12>
                        <date-picker id="date_of_birth" label="Date Of Birth" />
                    </v-flex>
                    <v-flex xs12 sm12 md12>
                        <date-picker id="date_of_birth2" multiple label="Date Of Birth" />
                    </v-flex>
                    <v-flex xs12 sm12 md12>
                        <lq-v-autocomplete
                            id="autocomplete"
                            :master-of="['combobox']"
                            :loading="loading"
                            :options="items2"
                            :search-input.sync="search"
                            class="mx-3"
                            flat
                            multiple
                            clearable
                            item-value="id"
                            item-text="login"
                            label="What state are you from?"
                        ></lq-v-autocomplete>
                    </v-flex>
                    <v-flex xs12 sm12 md12>
                        <lq-v-combobox
                            id="combobox"
                            hide-selected
                            hint="Maximum of 5 tags"
                            label="Add some tags"
                            multiple
                            item-value="id"
                            item-text="login"
                            persistent-hint
                            small-chips
                        ></lq-v-combobox>
                    </v-flex>
                    <v-flex xs12 sm12 md12>
                        <lq-v-checkbox
                            id="checkbox"
                            :value="2"
                            multiple
                            label="warning"
                            color="warning"
                            :hide-details="false"
                        ></lq-v-checkbox>
                    </v-flex>
                    <v-flex xs12 sm12 md12>
                        <lq-v-checkbox
                            id="checkbox"
                            :value="1"
                            multiple
                            label="warning 2"
                            color="primary"
                            hide-details
                        ></lq-v-checkbox>
                    </v-flex>
                    <v-flex xs12 sm12 md12>
                        <lq-v-checkbox
                            id="checkbox2"
                            value="Yes"
                            label="warning 3"
                            color="primary"
                            hide-details
                        ></lq-v-checkbox>
                    </v-flex>
                    <v-flex xs12 sm12 md12>
                        <lq-v-radio-group id="my_radio">
                            <v-radio id-index="1" value="Yes" label="Radio 1" :hide-details="true">
                                <template v-slot:label>
                                    <div>
                                        Definitely
                                        <strong class="primary--text">Duckduckgo</strong>
                                    </div>
                                </template>
                            </v-radio>
                            <v-radio id-index="2" value="No" label="Radio 2" :hide-details="true">
                                <template v-slot:label>
                                    <div>
                                        Definitely
                                        <strong class="primary--text">Duckduckgo 23</strong>
                                    </div>
                                </template>
                            </v-radio>
                        </lq-v-radio-group>
                    </v-flex>
                    <v-flex xs12 sm12 md12>
            <lq-v-radio id="my_radio" id-index="2" value="No" label="Radio 2"/>
                    </v-flex>
                    <v-flex xs12 sm12 md12>
                        <lq-v-switch
                            id="my_switch"
                            color="green"
                            value="On"
                            :true-value="true"
                            label="On"
                        />
                    </v-flex>
                    <v-flex xs3>
                        <lq-v-file
                            id="profile"
                            :aspect-ratio="0.75"
                            :thumb="{width: 600, height: 800}"
                            value-key="path"
                            :multiple="false"
                        />
                    </v-flex>-->
                    <v-layout row>
                        <v-flex xs12 sm12 md12>
                            <v-btn color="info" @click="init">Initialize Data</v-btn>
                            <v-btn color="info" @click="getFormData">Get Form Data</v-btn>
                            <v-btn color="primary" type="submit">Submit</v-btn>
                            <v-btn color="warning" @click="reset">Reset</v-btn>
                        </v-flex>
                    </v-layout>
                </lq-v-form>
            </v-layout>
        </v-container>
    </v-app>
</template>

<script>
import { users } from './dummyData';
import moment from 'moment';
import DatePicker from './DatePicker';
import LqVFile from './lq-file';
import Vue from 'vue';
export default {
    name: 'playgroud',
    components: {
        DatePicker,
        LqVFile
    },
    data: function( ) {
        return {
            checkbox: true,
            radioGroup: 1,
            switch1: true,
            show: true,
            items4: ['Foo', 'Bar', 'Fizz', 'Buzz'],
            rules: {
                name: {
                    presence: { allowEmpty: false }
                },
                mobile_no: { presence: { allowEmpty: false } },
                // date_of_birth: {presence: {allowEmpty: false}},
                date_of_birth2: { presence: { allowEmpty: false } },
                autocomplete: { presence: { allowEmpty: false } },
                checkbox: { presence: { allowEmpty: false } },
                my_radio: { presence: { allowEmpty: false } },
                my_switch: { presence: { allowEmpty: false } },
                textarea: { presence: { allowEmpty: false } },
                rating: { presence: { allowEmpty: false } },
                combobox: { presence: { allowEmpty: false } }
            },
            items: users.data,
            items2: users.data,
            menu: false,
            search: null,
            loading: false,
            fromData: {},
            states: [
                'Alabama',
                'Alaska',
                'American Samoa',
                'Arizona',
                'Arkansas',
                'California',
                'Colorado',
                'Connecticut',
                'Delaware',
                'District of Columbia',
                'Federated States of Micronesia',
                'Florida',
                'Georgia',
                'Guam',
                'Hawaii',
                'Idaho',
                'Illinois',
                'Indiana',
                'Iowa',
                'Kansas',
                'Kentucky',
                'Louisiana',
                'Maine',
                'Marshall Islands',
                'Maryland',
                'Massachusetts',
                'Michigan',
                'Minnesota',
                'Mississippi',
                'Missouri',
                'Montana',
                'Nebraska',
                'Nevada',
                'New Hampshire',
                'New Jersey',
                'New Mexico',
                'New York',
                'North Carolina',
                'North Dakota',
                'Northern Mariana Islands',
                'Ohio',
                'Oklahoma',
                'Oregon',
                'Palau',
                'Pennsylvania',
                'Puerto Rico',
                'Rhode Island',
                'South Carolina',
                'South Dakota',
                'Tennessee',
                'Texas',
                'Utah',
                'Vermont',
                'Virgin Island',
                'Virginia',
                'Washington',
                'West Virginia',
                'Wisconsin',
                'Wyoming'
            ]
        };
    },
    methods: {
        chala(w) {
            console.log('chala', w);
        },
        sendMessage: function() {
            console.log('tetsytgdfh');
        },
        SelectChange: function(data) {
            console.log('Select change', data);
        },
        getFormData: function() {
            this.fromData = this.$lqForm.formData('test_form');
        },
        reset: function() {
            this.$lqForm.resetForm('test_form');
        },
        init: function() {
            this.$lqForm.initializeValues('test_form', {
                name: '+91-8808824424',
                mobile_no: 23,
                date_of_birth: '2019-01-01',
                checkbox: [1],
                date_of_birth2: [
                    '2019-01-01',
                    '2019-01-02',
                    '2019-01-03',
                    '2019-01-04'
                ],
                my_switch: 'On',
                my_radio: 'Yes',
                profile: {
                    path: 'https://picsum.photos/500/300?image=100'
                },
                date_range: { start: '2019-01-01', end: '2019-03-02' },
                combobox: ['eeee', 'ee'],
                autocomplete: [
                    {
                        login: 'mojombo',
                        id: 1,
                        node_id: 'MDQ6VXNlcjE=',
                        avatar_url:
                            'https://avatars0.githubusercontent.com/u/1?v=4',
                        gravatar_id: '',
                        url: 'https://api.github.com/users/mojombo',
                        html_url: 'https://github.com/mojombo',
                        followers_url:
                            'https://api.github.com/users/mojombo/followers',
                        following_url:
                            'https://api.github.com/users/mojombo/following{/other_user}',
                        gists_url:
                            'https://api.github.com/users/mojombo/gists{/gist_id}',
                        starred_url:
                            'https://api.github.com/users/mojombo/starred{/owner}{/repo}',
                        subscriptions_url:
                            'https://api.github.com/users/mojombo/subscriptions',
                        organizations_url:
                            'https://api.github.com/users/mojombo/orgs',
                        repos_url: 'https://api.github.com/users/mojombo/repos',
                        events_url:
                            'https://api.github.com/users/mojombo/events{/privacy}',
                        received_events_url:
                            'https://api.github.com/users/mojombo/received_events',
                        type: 'User',
                        site_admin: false
                    }
                ],
                textarea: 'I am textarea.',
                rating: 3.5
            });
        }
    },
    created: function() {
        console.log('dummyData', users, this.items);
    },
    directives: {
        trap: {
            bind: function(el, binding, vnode) {
                console.log('I am intered', vnode);
                // Vue.set(vnode.data, 'model', {value: true})
                // el.dataset.model = JSON.stringify({
                //     value: true
                // })

                vnode.data.model = {
                    value: true,
                    expression: 'checkbox'
                }
                // vnode.componentInstance.$forceUpdate()

                // vnode.data.init(() => {
                //     console.log('sdsan')
                // })
                // console.log(model)
                //options.model
                // vnode.componentOptions()
                // var event = new Event("input", { bubbles: true });
                // el.value = true
                // el.dispatchEvent(event);
                // vnode.data.model = {
                //     value: true,
                //     callback: function() {
                //         console.log('KHksjahdjg')
                //     },
                //     expression: 'checkbox'
                // }
                // el.setAttribute('model', )
                // Vue.set(vnode.componentOptions.propsData, 'inputValue', true)
                // Vue.set(vnode.componentInstance._props, 'inputValue', true)

                // vnode.componentInstance.$forceUpdate()
            }
            // update: function(el, binding, vnode) {
            //     vnode.data.model = {
            //         value: true,
            //         callback: function() {
            //             console.log('KHksjahdjg')
            //         },
            //         expression: 'checkbox'
            //     }
            // }
        }
    }
};
</script>

<style>
</style>
