<template>
    <div class="chat">
        <div class="header">
            <div class="header-left">

            </div>
            <div class="header-right">
                {{username || "עודד"}}
            </div>
        </div>
        <div class="chat-box center">
            <div class="chat-header">
                <div class="title">מעונות - האקדמית תל אביב יפו</div>
            </div>
            <div class="chat-status center white rtl">
                <div class="flex status-details">
                    <img class="image" style="height: 30px; width: 30px; margin: 30px" src="../assets/completed.png"
                         alt="asasad">
                    <h2 class="status-text">טופל</h2>
                </div>
                <div class="issue relative">
                    <div class="rtl absolute"
                         style="overflow: auto;max-height: 120px; line-height: 1.5; right: 10px;top: 5px;">
                        <br/>
                        בקשת לינה
                        <br/>
                        מיקום: 819B
                        <br/>
                        מספר חדר: 819B


                    </div>
                </div>

            </div>
            <div style="width: 100%" class="white">
                <div class="chat-text">
                    <div style="display: flex; width: 98%;margin: 10px">
                        <div class="send-button-container">
                            <button style="" class="send-button" @click="onMessageSent">
                                שלח
                            </button>
                        </div>

                        <input type="text" v-model="currentMessage" dir="auto" placeholder="כתוב עדכון"
                               class="update-textarea">
                    </div>
                    <div class="chat-area">
                        <div v-for="item in reverseMessage" :key="item.message"
                             :class="'message-'+item.direction">
                            <div class="issue-update-text-item">
                                <div class="author" v-if="item.direction === 'left'">
                                    <img class="icon"
                                         src="../assets/icon-144x144.png"
                                         alt="visitt"><span><b>אלון זיבצנר</b></span>
                                </div>
                                <div v-if="item.direction === 'right'" class="time">{{new Date().getHours() +":"+ new
                                    Date().getMinutes()}}
                                </div>
                                <div class="message">{{ item.message }}</div>
                                <div v-if="item.direction === 'left'" style="display: block" class="time">{{new
                                    Date().getHours() +":"+ new Date().getMinutes()}}
                                </div>

                            </div>

                        </div>
                    </div>
                </div>
            </div>
        </div>
        <div class="visit-io-link flex"><a href="https://www.visitt.io">Powered by</a><a
                href="https://www.visitt.io"><img
                class="image" src="https://portal.visitt.co.il/portal-logo-main.svg" alt="visitt"></a></div>
    </div>
</template>

<script>
    export default {
        name: 'Chat',
        methods: {
            onMessageSent() {
                const message = this.currentMessage;
                if (message) {
                    const date = new Date(Date.now() - 1.44e+7);
                    this.messages.push({
                        message,
                        direction: "right",
                        date: `${date.getHours()}:${date.getMinutes()}`
                    });
                    setTimeout(() => {
                        const date1 = new Date(Date.now() - 1.44e+7 / 2);
                        this.messages.push({
                            message: "מאשר",
                            direction: "left",
                            date: `${date1.getHours()}:${date1.getMinutes()}`
                        })
                    }, 2000)
                }
            }
        },
        computed: {
            reverseMessage() {
                return this.messages.slice().reverse()
            }
        },
        data() {
            return {
                currentMessage: '',
                messages: [
                    // {
                    //     message: "asdasda",
                    //     direction: "right"
                    // },
                    // {
                    //     message: "asdasda",
                    //     direction: "left"
                    // },
                ]
            }
        }
    }
</script>

<style scoped src="./style.css">

</style>
