vue 的六位密码输入组件

使用示例:

```
</template>
    <div>
    	<vue-pay-password ref="pay-password" @change="onChange"></vue-pay-password>
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
    		return this.$refs['pay-password'].getPassword()
    	},
        onChange(val) {
            console.log(val)
        }
    },
}
</script>

<style scoped>
</style>
```
