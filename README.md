# senthilnathan.js.org

import { Directive, EventEmitter, Input, Output, HostListener } from '@angular/core';

export type SortDirection = 'asc' | 'desc' | '';
const rotate: { [key: string]: SortDirection } = { 'asc': 'desc', 'desc': '', '': 'asc' };

@Directive({
  selector: '[appSortable]'
})
export class SortableDirective {

  @Input() appSortable: string = '';
  @Input() direction: SortDirection = '';
  @Output() sort = new EventEmitter<{ column: string, direction: SortDirection }>();

  @HostListener('click')
  rotate() {
    this.direction = rotate[this.direction];
    this.sort.emit({ column: this.appSortable, direction: this.direction });
  }
}
