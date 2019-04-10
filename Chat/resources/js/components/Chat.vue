<style scoped>
    .panel-block {
        flex-direction: column;
        border: none;
    }
    .chat {
        width: 100%;
        padding: 20px;
        box-shadow: inset 0 0 20px 0 grey;
        margin-bottom: 20px;
        border: 1px solid grey;
        max-height: 600px;
        overflow-x: auto;
    }
    .chat .chat-right, .chat .chat-left {
        border-radius: 10px;
        max-width: 70%;
        box-shadow: 0 0 8px 0px grey;
        padding: 8px;
        margin: 10px;
    }
    .chat-right {
        float: right;
        background-color: #3341e8;
        color: white;
    }
    .chat-left {
        float: left;
    }
    .no-message {
        height: 200px;
        display: flex;
        align-items: center;
    }
</style>

<template>
    <div class="panel-block">
    	<div class="chat" v-if="chats.length != 0">
    		<div v-for="chat in chats" style="overflow: auto">
    			<div class="chat-right" v-if="chat.user_id == userid">
    				{{ chat.chat }}
    			</div>
    			<div class="chat-left" v-else>
    				{{ chat.chat }}
    			</div>
    		</div>
    	</div>
    	<div v-else class="no-message">
    		There are no messages
    	</div>
    	<chat-composer v-bind:userid="userid" v-bind:chats="chats" v-bind:friendid="friendid"></chat-composer>
    </div>
</template>

<script>
    export default {
        props: ['chats' ,'userid', 'friendid'],
        mounted() {
			console.log('Chat mounted');
		}
    }
</script>
