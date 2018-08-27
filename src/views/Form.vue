<!--  -->
<template>
  <div>
      <!-- 要使用 Radio 组件，只需要设置v-model绑定变量，选中意味着变量的值为相应 Radio label属性的值，label可以是String、Number或Boolean。 -->
      <el-radio v-model="radio" label="1" disabled>备选项</el-radio>
      <el-radio v-model="radio" label="2">备选项</el-radio>

      <div id="radioGroup">
        <el-radio-group v-model="radio2">
            <el-radio :label="3">备选项</el-radio>
            <el-radio :label="6">备选项</el-radio>
            <el-radio :label="9">备选项</el-radio>
        </el-radio-group>
      </div>

      <div style="margin-top: 20px">
          <el-checkbox v-model="checked" disabled>备选项</el-checkbox>
          <div style="margin-top: 20px">
              <el-checkbox-group v-model="checkList">
                <el-checkbox label="复选框 A"></el-checkbox>
                <el-checkbox label="复选框 B"></el-checkbox>
                <el-checkbox label="复选框 C"></el-checkbox>
                <el-checkbox label="禁用" disabled></el-checkbox>
                <el-checkbox label="选中且禁用" disabled></el-checkbox>
             </el-checkbox-group>
          </div>
      </div>
      
      <div>
          <el-checkbox :indeterminate="isIndeterminate" v-model="checkAll" @change="handleCheckAllChange">全选</el-checkbox>
          <div style="margin: 15px 0;"></div>
          <el-checkbox-group v-model="checkedCities" @change="handleCheckedCitiesChange">
              <el-checkbox v-for="city in cities" :label="city" :key="city">{{city}}</el-checkbox>
          </el-checkbox-group>
      </div>

      <el-input v-model="input" 
                :disabled="false" 
                clearable
                placeholder="请输入内容" 
                prefix-icon="el-icon-search"
                style="width: 300px; margin-top: 20px;">
      </el-input>
      <div>
      <el-input
        type="textarea"
        autosize
        placeholder="请输入内容"
        v-model="textarea2"
        style="width: 300px;margin: 20px 0;margin: 20px 0;">
      </el-input>
      <div style="margin: 20px 0;"></div>
      <el-input
        type="textarea"
        :autosize="{ minRows: 2, maxRows: 4}"
        placeholder="请输入内容"
        v-model="textarea3"
        style="width: 300px;">
      </el-input>
      </div>

      <el-select v-model="value" placeholder="请选择" style="margin-top: 20px">
            <el-option
            v-for="item in options"
            :key="item.value"
            :label="item.label"
            :value="item.value">
            </el-option>
        </el-select>
  </div>
</template>

<script>
const cityOptions = ['上海', '北京', '广州', '深圳'];
export default {
  data () {
    return {
        radio: '2',
        radio2: 3,
        checked: true,
        checkList: ['选中且禁用','复选框 A'],
        checkAll: false,
        checkedCities: ['上海', '北京'],
        cities: cityOptions,
        isIndeterminate: true,
        input: '',
        textarea2: '',
        textarea3: '',
        options: [{
          value: '选项1',
          label: '黄金糕'
        }, {
          value: '选项2',
          label: '双皮奶'
        }, {
          value: '选项3',
          label: '蚵仔煎'
        }, {
          value: '选项4',
          label: '龙须面'
        }, {
          value: '选项5',
          label: '北京烤鸭'
        }],
        value: ''
    };
  },

  components: {},

  computed: {},

  created(){},

  mounted(){},

  methods: {
      handleCheckAllChange(val) {
        this.checkedCities = val ? cityOptions : [];
        this.isIndeterminate = false;
      },
      handleCheckedCitiesChange(value) {
        let checkedCount = value.length;
        this.checkAll = checkedCount === this.cities.length;
        this.isIndeterminate = checkedCount > 0 && checkedCount < this.cities.length;
      }
  }
}

</script>
<style scoped>
    #radioGroup {
        margin-top: 20px;
    }
</style>