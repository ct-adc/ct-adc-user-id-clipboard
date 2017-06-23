<template>
    <textarea @change="update"
              v-model="UserIds"></textarea>
</template>

<script type="text/ecmascript-6">
    export default {
        // 创建即格式化更新一次
        created() {
            this.update();
        },
        props: {
            // 分隔符，用于分割 id，默认逗号
            separator: {
                type: String,
                default: ','
            },

            // 用户 ID props
            userId: {
                type: String,
                default: ''
            }
        },
        data() {
            return {
                UserIds: this.userId
            };
        },
        methods: {
            // 更新数据
            update() {
                let sUserId = this.UserIds;

                // 首先，把分隔符替换成空格
                sUserId = sUserId.replace(this.separator.trim(), ' ');

                // 然后，删除非数字
                // 但是不删除: 数字、换行符
                sUserId = sUserId.replace(/[^\d\s]/g, ' ');

                // 然后，去除前后空白符
                // Q: 为什么不使用 v-model.trim
                // A: 因为上一步操作可能会带来前后空白
                sUserId = sUserId.trim();


                // 然后，合并分行
                sUserId = sUserId.replace(/\s+/g, this.separator);

                // 最后，去除重复项
                sUserId = this.unique(sUserId);

                // Q: 有 watch，为什么还需要再赋值一次？
                // A: 因为格式化之后，可能是空，导致 watch 不能 get
                this.UserIds = sUserId;

                this.emitChange();
            },

            emitChange() {
                this.$emit('change', this.UserIds);
            },

            // 去重
            unique(sUserId) {
                let userIdList = sUserId.split(this.separator);

                // 简单数组去重
                userIdList = Array.from(new Set(userIdList));

                return userIdList.join(this.separator);
            }
        },
        watch: {
            // 监听用户 ID 的改变
            userId(val) {
                this.UserIds = val;

                this.update();
            }
        }
    };
</script>

<style rel="stylesheet/scss" lang="scss" scoped>

</style>
