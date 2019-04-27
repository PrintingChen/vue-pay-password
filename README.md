vue 的六位密码输入组件

使用示例:

```
</template>
    <div>
    	<vue-pay-password ref="pay-password"></vue-pay-password>
    </div>
</template>

<script>
import VuePayPassword from 'vue-pay-password'
export default {
    components: { vue-pay-password },
    data() {
        return {}
    },
    methods: {
    	getPassword() {
    		return this.$refs['pay-password'].getPassword() // 返回字符串，业务中校验字符串是否够六位数字，以及密码加密
    	}
    },
}
</script>

<style scoped>
</style>
```
