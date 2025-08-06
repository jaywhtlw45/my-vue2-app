<template>
    <container class="conatiner">
        <header class="header">
            <h1>Vue 2 Smart Clipboard handler</h1>
            <h2>Try pasting text or images using <strong>Ctrl + V</strong></h2>
        </header>

        <body class="body">
            <input type="textbox" class="emailInput" @focus="focusTextBox" @blur="unfocusTextBox">

            <div v-if="isSelected">Text Box Selected</div>
        </body>
        <footer class="footer">
            <div class="fileAttachmentText">
                Attached Files:
            </div>
            <ul>
                <li v-for="(file, index) in attachedFiles" :key="index">
                    {{ file }}
                </li>
            </ul>

        </footer>
    </container>
</template>

<script>
export default {
    name: 'EmailBox',
    data() {
        return {
            attachedFiles: ['file1.txt', 'file2.txt', 'file3.txt'],
            isSelected: false,
        }
    },
    methods: {
        focusTextBox() {
            this.isSelected = true;
        },
        unfocusTextBox() {
            this.isSelected = false;
        }
    }
}
</script>


<style>
.container {
    max-width: 500px;
    min-width: 200px;
}

ul {
    list-style: none;
}

.emailInput {
    width: 500px;
    height: 300px;
    padding: 12px;
    border: 2px solid #ccc;
    border-radius: 8px;
}

.fileAttachmentText {}
</style>