<template>
	<div>
		<main class="todo">
        <div class="container">
            <h1>To - Do List</h1>

            <!-- ul.list_add -->
            <ul class="list_add">
                <li class="list_add_tit"><p>등록 하기</p></li>
                <li><p><input type="text" v-model="todo" @keyup.enter = 'addTodo' placeholder="여기에 할일을 적으세요"><button @click="listUp">등 록</button></p></li>
            </ul>
            <!--// ul.list_add -->

            <!-- ul.todo_list -->
            <ul class="todo_list">
                <li class="todo_list_tit"><p>할 일</p></li>
                <li class="del_btn" v-for="(item, index) in todo" :key="index">
                    <p>
                        <input type="checkbox" name="check1" value=""> {{ item }} 
                    </p>
										<ul class="todo_list_btn">
                        <li><button @click="moveClick">이 동</button></li>
                        <li><button @click="finishClick">완 료</button></li>
                    </ul>										
                </li>
            </ul>
            <!--// ul.todo_list -->
						<div class="form_btn">
                <button>삭제</button>
                <button>저장</button>
            </div>

        </div>
    </main>	
	</div>

</template>

<script>
import { reactive, toRefs, inject, ref } from 'vue'
	
export default {
	name: 'todolist',
	data: function() {
		return {
			todo: '',
			todos: [],
		}
	},
	methods: {
		addTodo() {
			if (this.todo) {
				var todolist = {
					completed: false,
					item: this.todo
				}
				localStorage.setItem(this.todo, JSON.stringify(todolist))
				this.clearInput()
			}
		},
		clearInput() {
			this.todo = '';
		},
		moveClick() {
			console.log("move");
		},
		finishClick() {
			console.log("finished");
		},		
	},
}
</script>

<style>
.form_btn button {
  width: 120px;
	height: 35px;
  padding: 4px 10px 2px 10px;
  color: #45B649;
  background-color: #fff;
  border: solid 1px #45B649;
  border-radius: 4px;
  font-size: 14px;
	margin: 2px;
}
.form_btn button:hover {
  color: #fff;
  background-color: #45B649;
  border: solid 1px #fff;
}
</style>