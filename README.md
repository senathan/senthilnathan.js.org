# senthilnathan.js.org

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
