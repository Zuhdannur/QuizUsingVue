<template>
    <div>
        <b-container>
            <p>Skor Kamu = {{ score * 20 }}</p>
            <div role="tablist">
                <b-card v-for="(item,index) in items" no-body class="mb-1" :key="item.soal">
                    <b-card-header header-tag="header" class="p-1" role="tab">
                        <b-btn block  type="button" v-b-toggle="'accordion-'+ index" variant="info" v-on:click="setPosition(index)">{{ 'Soal Nomor ' + (index+1) }}</b-btn>
                    </b-card-header>
                    <b-collapse v-bind:id="'accordion-'+index" visible accordion="my-accordion" role="tabpanel">
                        <b-card-body>
                            <p class="card-text">{{ item.soal }}</p>
                            <div v-if="item.btn_click">
                                <b-form-group>
                                    <b-form-radio-group v-model="item.clicked"
                                                        :options="item.pilihan"
                                                        name="radioInline">
                                    </b-form-radio-group>
                                </b-form-group>
                                <b-button variant="success" v-on:click="checkingAnswer">Yakin</b-button>
                            </div>

                        </b-card-body>
                    </b-collapse>
                </b-card>
            </div>
        </b-container>
    </div>
</template>
<script>
    export default {
        name : 'CardQuestion',
        data : function () {
            return {
                score:0,
                position:0,
                items: [{
                    soal : 'Apa yang Harus Dilakukan Jika sedang lapar?',
                    btn_click : true,
                    clicked:String,
                    pilihan:[
                        { text:'Minum',value:'minum'},
                        { text:'Makan',value:'makan'},
                        { text: 'Ngoding',value:'ngoding'}],
                    jawaban:'makan'
                },{
                    soal : '1 + 1 = ',
                    btn_click : true,
                    clicked:String,
                    pilihan:[
                        { text:'1,905',value:'1,905'},
                        { text:'2,905',value:'2,905'},
                        { text: '900',value:'900'},
                        { text: '2',value:'2'}],
                    jawaban:'2'
                },{
                    soal : 'Berapakah Luas Negara Indonesia?',
                    btn_click : true,
                    clicked:String,
                    pilihan:[
                        { text:'1,905 juta km²',value:'1,905'},
                        { text:'2,905 juta km²',value:'2,905'},
                        { text: '900 juta km²',value:'900'},
                        { text: '100 km²',value:'100'}],
                    jawaban:'1,905'
                },{
                    soal : 'Siapakah KM Kelas RPL 1 ?',
                    btn_click : true,
                    clicked:String,
                    pilihan:[
                        { text:'Rafli Rafiky',value:'rafli'},
                        { text:'Syifa A',value:'syifa'},
                        { text: 'Raihan',value:'raihan'},
                        { text: 'Belva',value:'belva'}],
                    jawaban:'rafli'
                },{
                    soal : 'Gubernur Jawa Barat ?',
                    btn_click : true,
                    clicked:String,
                    pilihan:[
                        { text:'Ridwan Kamil',value:'kamil'},
                        { text:'Ikan Tongkol',value:'tongkol'},
                        { text: 'SBY',value:'sby'},
                        { text: 'Ahok',value:'ahok'}],
                    jawaban:'kamil'
                }],
            }
        },
        methods:{
            setPosition(i){
               this.position = i;
            },
            checkingAnswer(){
                this.items[this.position].btn_click = false;
                if(this.items[this.position].jawaban === this.items[this.position].clicked){this.score++;}
            },
        }
    }
</script>