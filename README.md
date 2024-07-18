# senthilnathan.js.org
import { AbstractControl, ValidatorFn } from '@angular/forms';

export function combinedValidator(pattern: string | RegExp): ValidatorFn {
  return (control: AbstractControl): { [key: string]: any } | null => {
    const value = control.value;
    const errors: any = {};

    // Required validation
    if (!value) {
      errors.required = true;
    }

    // Pattern validation
    const regex = typeof pattern === 'string' ? new RegExp(pattern) : pattern;
    if (value && !regex.test(value)) {
      errors.pattern = true;
    }

    // Return null if no errors, otherwise return the errors object
    return Object.keys(errors).length ? errors : null;
  };
}
