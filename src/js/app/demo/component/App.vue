<template>
    <div id="demo" class="container">
        <div class="col-md-8 col-md-offset-2 mt-50">
            <user-id-textarea class="form-control" :placeholder="'批量输入用户ID请用英文逗号隔开，最多 ' + max + ' 个用户'" rows="18"
                              :separator="setting.separator"
                              :userId="setting.userId"
                              @change="updateUserId"></user-id-textarea>

            <hr>

            <pre>{{ setting.userId }}</pre>
        </div>
    </div>
</template>

<script type="text/ecmascript-6">
    import UserIdTextarea from '../../../../component/ct-adc-user-id-textarea.vue';

    export default {
        components: {
            UserIdTextarea
        },
        data() {
            return {
                setting: {
                    separator: ', ',
                    userId: '123,223'
                },
                max: 5
            };
        },
        methods: {
            updateUserId(val) {
                const currentLen = val.split(this.setting.separator).length;

                this.setting.userId = val;

                if (currentLen > this.max) {
                    this.showOutOfRangeError(currentLen, this.max);
                }
            },
            showOutOfRangeError(currentLen, max) {
                const miniMsg = new MiniMsg({
                    content: `当前 UserId 数为 ${ currentLen }，超过最大值 ${ max }`,
                    duration: 3,
                    container: $('body'),
                    type: 'error'
                });

                miniMsg.animation();
            }
        }
    };
</script>

<style rel="stylesheet/scss" lang="scss">
    .mt-50 {
        margin-top: 50px;
    }
</style>
