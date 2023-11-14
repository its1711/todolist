# todolist
#html code
<div class="container mt-3 col-4 flex">
    <div class="d-flex">
        <input type="text" class="form-control mx-2" #input placeholder="Task">
        <button type="submit" class="btn btn-primary w-75" (click)="getInputText(input.value)">
            Add to list
        </button>
    </div>
</div>

<div class="container d-flex col-4">
    <table class="table table-borderless">
        <thead>
            <tr>
                <th>Details</th>
                <th>Action</th>
            </tr>
        </thead>
        <tbody>
            <tr scope="row" *ngFor="let t of task">
                <td>{{t.name}}</td>
                <td><button (click)="removeTask(t.id)" class="btn btn-danger">Remove</button></td>
            </tr>
        </tbody>
    </table>
</div>

#ts code
import { Component, ViewChild } from '@angular/core';

@Component({
  selector: 'app-to-do',
  templateUrl: './to-do.component.html',
  styleUrls: ['./to-do.component.css']
})
export class ToDoComponent {
  task:any[]=[]
  @ViewChild('input') inputText:any;
  getInputText(val:String){
    this.task.push({id:this.task.length,name:val});
    this.inputText.nativeElement.value='';
  }
    removeTask(id:number){
      console.warn(id);
      this.task=this.task.filter(item=>item.id!=id);
    }
  }


