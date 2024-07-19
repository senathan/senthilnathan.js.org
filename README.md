# senthilnathan.js.org
^[a-zA-Z0-9_]+(\.[a-zA-Z0-9_]+)*\.privare\.snowflake\.com$



ng generate directive sortable

import { Directive, EventEmitter, Input, Output, HostListener } from '@angular/core';

export type SortDirection = 'asc' | 'desc' | '';
const rotate: { [key: string]: SortDirection } = { 'asc': 'desc', 'desc': '', '': 'asc' };

@Directive({
  selector: 'th[sortable]'
})
export class SortableDirective {

  @Input() sortable: string = '';
  @Input() direction: SortDirection = '';
  @Output() sort = new EventEmitter<{ column: string, direction: SortDirection }>();

  @HostListener('click')
  rotate() {
    this.direction = rotate[this.direction];
    this.sort.emit({ column: this.sortable, direction: this.direction });
  }
}


ng generate component sortable-header


import { Component, Input, OnInit } from '@angular/core';

@Component({
  selector: 'app-sortable-header',
  template: `
    <ng-content></ng-content>
  `,
  styleUrls: ['./sortable-header.component.css']
})
export class SortableHeaderComponent implements OnInit {
  @Input() data: any[] = [];
  @Input() headers: string[] = [];

  sortedData: any[] = [];
  sortColumn: string = '';
  sortDirection: 'asc' | 'desc' | '' = '';

  ngOnInit() {
    this.sortedData = [...this.data];
  }

  onSort({ column, direction }: { column: string, direction: 'asc' | 'desc' | '' }) {
    this.sortColumn = column;
    this.sortDirection = direction;
    this.sortedData = this.sort([...this.data], column, direction);
  }

  sort(data: any[], column: string, direction: 'asc' | 'desc' | ''): any[] {
    if (direction === '') {
      return data;
    } else {
      return [...data].sort((a, b) => {
        const res = a[column] > b[column] ? 1 : a[column] < b[column] ? -1 : 0;
        return direction === 'asc' ? res : -res;
      });
    }
  }
}


<app-sortable-header [data]="data" [headers]="headers" (sort)="onSort($event)">
  <table>
    <thead>
      <tr>
        <th *ngFor="let header of headers" [sortable]="header" (sort)="onSort($event)">
          {{ header | titlecase }}
          <span *ngIf="sortColumn === header">
            {{ sortDirection === 'asc' ? '▲' : '▼' }}
          </span>
        </th>
      </tr>
    </thead>
    <tbody>
      <tr *ngFor="let item of sortedData">
        <td *ngFor="let header of headers">
          {{ item[header] }}
        </td>
      </tr>
    </tbody>
  </table>
</app-sortable-header>


import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  template: `
    <app-sortable-header [data]="data" [headers]="headers" (sort)="onSort($event)">
    </app-sortable-header>
  `,
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  headers = ['host', 'step', 'action', 'status'];
  data = [
    { host: 'host1', step: 'firewall', action: 'enable allow all', status: 'done' },
    { host: 'host1', step: 'firewall', action: 'enable deny all', status: 'done' },
    { host: 'host1', step: 'firewall', action: 'verify', status: 'in-progress' }
  ];

  sortColumn: string = '';
  sortDirection: 'asc' | 'desc' | '' = '';
  sortedData = [...this.data];

  onSort({ column, direction }: { column: string, direction: 'asc' | 'desc' | '' }) {
    this.sortColumn = column;
    this.sortDirection = direction;
    this.sortedData = this.sort([...this.data], column, direction);
  }

  sort(data: any[], column: string, direction: 'asc' | 'desc' | ''): any[] {
    if (direction === '') {
      return data;
    } else {
      return [...data].sort((a, b) => {
        const res = a[column] > b[column] ? 1 : a[column] < b[column] ? -1 : 0;
        return direction === 'asc' ? res : -res;
      });
    }
  }
}

