<template>
    <div>
        <div 
            class="todo-item"
            :class="{ complete: todo_item.checked }">
            <div class="container-check">
                <input 
                    class="checkbox" 
                    type="checkbox" 
                    v-on:change="$emit(`checkedItem`, todo_item.id)"
                    :checked= "todo_item.checked">
            </div>
            <div class="header-item">
                <h3>
                    {{ todo_item.todo }}
                </h3>
            </div>
            <div class="button-item">
                <button 
                    v-if="!todo_item.checked"
                    class="btn-pen"
                    @click="$emit(`editItem`, todo_item.id)">
                    Edit   <i class="fas fa-pen"></i>
                </button>
                <button 
                    class="btn-trash" :class="{ full: todo_item.checked }"
                    @click="$emit(`deleteItem`, todo_item.id)">
                    <i class="fas fa-trash"></i>   Delete
                </button>
            </div>
        </div>
        <div class="footer-item">
            <p>created on: <i>
                {{ todo_item.createdOn }}</i>
            </p>
            <p
                v-if="todo_item.updatedOn && !todo_item.checked">
                updated on: 
                <i>
                    {{ todo_item.updatedOn }}
                </i>
            </p>
            <p
                v-if="todo_item.checked">
                completed on: <i> {{ todo_item.completedOn }}
                </i>
            </p>
        </div>
    </div>
</template>

<script>
    export default {
        name: "TodoItem",
        props: ["todo_item"]
    }
</script>

<style>
    .todo-item {
        border-bottom: 1.5px solid #081c15;
        width: 80%;
        margin: auto;
        padding: 25px 15px 10px 15px;
        display: flex;
        margin-top: 20px;
        margin-bottom: 10px;
    }

    .todo-item h3 {
        margin: 0;
    }

    .complete {
        background-color: #fefae0;
    }

    .header-item {
        width: 60%;
        margin: auto;
    }

    .container-check {
        display: block;
        width: 5%;
    }

    .button-item {
        display: flex;
        white-space: nowrap;
    }

    .btn-pen {
        background-color: DodgerBlue;
        color: white;
        border: none;
        padding: 10px 12px; 
        font-size: 12px; 
        cursor: pointer;
        border-radius: 10px 0 0 10px;
        display: inline-block;
    }
    
    .btn-pen:hover {
        background-color: RoyalBlue;
    }

    .btn-trash {
        background-color: #f24957;
        color: white;
        border: none;
        padding: 10px 12px; 
        font-size: 12px; 
        cursor: pointer;
        border-radius: 0 10px 10px 0;
        display: inline-block;
    }
    
    .btn-trash:hover {
        background-color: #cc1111;
    }

    .fa-pen {
        margin-left: 7px;
    }

    .fa-trash {
        margin-right: 7px;
    }

    .full {
        border-radius: 10px;
    }
    
    .footer-item {
        margin: auto;
        margin-left: 10%;
        display: flex;
        width: 80%;
    }

    .footer-item p {
        width: 50%;
        margin-top: 0;
    }

    .footer-item p i{
        font-size: 0.8em;
    }

    * {
        box-sizing: border-box;
    }

    @media screen and (max-width: 660px) {
        .header-item {
            width: 100%;
            margin-bottom: 10px;
        }

        .button-item {
            width: 50%;
            margin: auto;
        }

        .todo-item {
            display: block;
        }

        .btn-trash, .btn-pen {
            display: block;
            width: 45%;
        }

        .btn-trash {
            width: 55%;
        }

        .full {
            width: 30%;
            display: block;
            margin: auto;
        }
    }

    @media screen and (max-width: 500px) {
        .button-item {
            width: 100%;
        }
    }
</style>