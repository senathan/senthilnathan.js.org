# senthilnathan.js.org

import styled from 'styled-components';

export const Contact = styled.div`
  background-color: var(--clr-grey-3);
`;

export const ContactInfo = styled.div`
  margin: 1rem 0;

  @media screen and (min-width: 992px) {
    width: 50%;
    float: left;
  }
`;

export const ContactForm = styled.div`
  background-color: var(--clr-white);
  padding: 1.3rem;
  max-width: 35rem;
  border-radius: 5px;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
  margin: 1rem 0;

  @media screen and (min-width: 992px) {
    width: 50%;
    float: left;
  }

  h3 {
    font-family: var(--ff-design);
    color: var(--clr-primary);
    font-size: 1.75rem;
    text-align: center;
  }
`;

export const ContactTitle = styled.div`
  display: flex;
  align-items: center;
  gap: 5px;
  font-weight: 500;
  margin-bottom: -0.05rem;
  
  svg {
    fill: var(--clr-grey-2);
  }
`;

export const ContactText = styled.p`
  color: var(--clr-grey-2);
`;

export const ContactItem = styled.div`
  margin-bottom: 1.25rem;
`;

export const FormGroup = styled.div`
  height: 35px;
  margin-bottom: 20px;
  position: relative;
`;

export const FormControl = styled.input`
  width: 100%;
  height: 100%;
  background: none;
  border: 1px solid var(--clr-grey-2);
  outline: none;
  padding: 1rem;
  border-radius: 3px;
  resize: none;
  font-family: var(--ff-secondary);
  position: absolute;
  top: 0;
  left: 0;
  z-index: 1;

  &:focus {
    border: 1px solid var(--clr-primary);
  }

  &:focus + label {
    top: -10px;
    z-index: 10;
  }

  &:not(:focus):valid + label {
    top: -10px;
    z-index: 5;
  }
`;

export const FormLabel = styled.label`
  position: absolute;
  left: 7px;
  top: 7px;
  color: var(--clr-grey-2);
  background-color: var(--clr-white);
  padding: 0 6px;
  font-size: 14px;
  transition: var(--transition);
`;

export const TextAreaFormControl = styled(FormControl).attrs({ as: 'textarea' })`
  height: 7rem;
`;

export const SubmitButton = styled.button`
  padding: 0.7rem 1rem;
  margin-top: 4.5rem;
`;
