<template>
    <div class="convert">
        <h1>{{ msg }}</h1>
        <hr>
        <div class="row align-items-center">
            <div class="col-md-12">
                <h2><i class="fa fa-star-o"></i> Đổi chiều dài </h2>
            </div>
            <div class="col-md-12">
                <div class="form-group row">
                    <label for="input_length" class="col-4 col-form-label"><strong>Nhập số lượng:</strong></label>
                    <div class="col-4">
                        <input v-model="input_length" class="form-control" type="text" placeholder="Nhập số lượng cần chuyển đổi. Ví dụ: 100...." id="input_length">
                    </div>
                </div>
                <div class="row">
                    <div class="col-md-4">
                        <div class="form-group">
                            <label for="from_unit">Chuyển từ đơn vi</label>
                            <select class="form-control" id="from_unit" v-model="from_unit">
                                <option v-for="item in length_unit" :value="item.value">{{ item.value }}</option>
                            </select>
                        </div>
                    </div>
                    <div class="col-md-4 offset-md-4">
                        <div class="form-group">
                            <label for="to_unit">Sang đơn vi</label>
                            <select class="form-control" id="to_unit" v-model="to_unit">
                                <option v-for="item in length_unit" :value="item.value">{{ item.value }}</option>
                            </select>
                        </div>
                    </div>
                </div>
                <div class="form-group row">
                    <label for="output_length" class="col-4"><strong class="text-lg-left text-danger">Kết quả:</strong></label>
                    <div class="col-4">
                        <strong class="text-primary" v-if="input_length !== ''">{{ input_length + ' ' + from_unit + ' = ' + output_length + ' ' + to_unit }}</strong>
                    </div>
                </div>
            </div>
        </div>
        <hr>
        <div class="row align-items-center">
            <div class="col-md-12">
                <h2><i class="fa fa-star-o"></i> Đổi khối lượng</h2>
                <div class="col-md-12">
                    <div class="form-group row">
                        <label for="input_weight" class="col-4 col-form-label"><strong>Nhập số lượng:</strong></label>
                        <div class="col-4">
                            <input v-model="input_weight" class="form-control" type="text" placeholder="Nhập số lượng cần chuyển đổi. Ví dụ: 100...." id="input_weight">
                        </div>
                    </div>
                    <div class="row">
                        <div class="col-md-4">
                            <div class="form-group">
                                <label for="from_unit">Chuyển từ đơn vi</label>
                                <select class="form-control" id="from_unit" v-model="from_weight">
                                    <option v-for="item in weight_unit" :value="item.value">{{ item.value }}</option>
                                </select>
                            </div>
                        </div>
                        <div class="col-md-4 offset-md-4">
                            <div class="form-group">
                                <label for="to_unit">Sang đơn vi</label>
                                <select class="form-control" id="to_unit" v-model="to_weight">
                                    <option v-for="item in weight_unit" :value="item.value">{{ item.value }}</option>
                                </select>
                            </div>
                        </div>
                    </div>
                    <div class="form-group row">
                        <label for="output_length" class="col-4"><strong class="text-lg-left text-danger">Kết quả:</strong></label>
                        <div class="col-4">
                            <strong class="text-primary" v-if="input_weight !== ''">{{ input_weight + ' ' + from_weight + ' = ' + output_weight + ' ' + to_weight }}</strong>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
var math = require('mathjs');

export default {
    data () {
        return {
            msg: 'Welcome to Converter App',
            input_length: 0,
            from_unit: 'millimeter',
            to_unit: 'centimeter',
            length_unit: [
                {value: 'millimeter'},
                {value: 'centimeter'},
                {value: 'decimeter'},
                {value: 'meter'},
                {value: 'kilometer'},
                {value: 'inch'},
                {value: 'foot'},
                {value: 'yard'},
                {value: 'mile'},
                {value: 'link'},
            ],
            weight_unit: [
                {value: 'gram'},
                {value: 'kilogram'},
                {value: 'tonne'},
                {value: 'ounce'},
            ],
            input_weight: 0,
            from_weight: 'kilogram',
            to_weight: 'gram',
        }
    },
    computed: {
        output_length: function(){
            let output_length = math.unit(this.input_length, this.from_unit).toNumber(this.to_unit);
            return output_length;
        },
        output_weight: function(){
            let output_weight = math.unit(this.input_weight, this.from_weight).toNumber(this.to_weight);
            return output_weight;
        }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
    font-weight: normal;
}

ul {
    list-style-type: none;
    padding: 0;
}

li {
    display: inline-block;
    margin: 0 10px;
}

a {
    color: #42b983;
}
.converter{
    margin: 0 auto;
}
</style>
