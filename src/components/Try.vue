<template>
    <div>
        <b-alert :show="dismissCountDown"
                 dismissible
                 variant="warning"
                 @dismissed="dismissCountDown=0"
                 @dismiss-count-down="countDownChanged">
            <p>This alert will dismiss after {{dismissCountDown}} seconds...</p>
            <b-progress variant="warning"
                        :max="dismissSecs"
                        :value="dismissCountDown"
                        height="4px">
            </b-progress>
        </b-alert>
        <b-btn @click="showAlert" variant="info" class="m-1">
            Show alert with count-down timer
        </b-btn>
    </div>
</template>
<script>
    export default {
        name: 'alerts',
        data () {
            return {
                dismissSecs: 10,
                dismissCountDown: 0,
                showDismissibleAlert: false
            }
        },
        methods: {
            countDownChanged (dismissCountDown) {
                this.dismissCountDown = dismissCountDown
            },
            showAlert () {
                this.dismissCountDown = this.dismissSecs
            }
        }
    }
</script>