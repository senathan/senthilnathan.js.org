# senthilnathan.js.org

import styled from 'styled-components';

export const NavButtonSvg = styled.svg`
  fill: var(--clr-primary);
  position: fixed;
  top: 5%;
  left: 5%;
  cursor: pointer;
  z-index: 1;
`;

export const Navbar = styled.div`
  position: fixed;
  background-color: rgba(0, 0, 0, 0.9);
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  transition: var(--transition);
  transform: translateX(-100%);
  z-index: 3;

  @media screen and (min-width: 768px) {
    width: 35%;
    max-width: 25rem;
  }
`;

export const NavbarHeader = styled.div`
  position: relative;
`;

export const NavbarHeaderImg = styled.img`
  width: 100px;
  margin: 0 auto;
`;

export const NavClose = styled.div`
  position: absolute;
  right: 0;
  top: 5px;

  svg {
    cursor: pointer;
    fill: var(--clr-dark);
    transition: var(--transition);

    &:hover {
      fill: var(--clr-white);
    }
  }
`;

export const NavItems = styled.ul`
  list-style: none;
`;

export const NavLink = styled.a`
  display: block;
  text-transform: uppercase;
  color: var(--clr-white);
  font-size: 1.2rem;
  transition: var(--transition);
  letter-spacing: 0.5px;
  padding: 0.75rem 1rem;

  &:hover {
    background-color: var(--clr-primary-light);
    padding: 1.5rem;
    border-left: 0.5rem solid var(--clr-secondary);
  }
`;

export const NavCheck = styled.input.attrs({ type: 'checkbox' })`
  display: none;

  &:checked ~ ${Navbar} {
    transform: translateX(0);
  }

  &:checked ~ .overlay {
    display: block;
  }
`;

export const Overlay = styled.div`
  position: fixed;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
  z-index: 2;
  display: none;
`;

export const NavbarTitle = styled.h3`
  padding: 1rem;
  color: transparent;
  font-size: 1.5rem;
  text-align: center;
  text-transform: uppercase;
  font-weight: 700;
  background-image: linear-gradient(180deg, var(--clr-primary) 25%, var(--clr-secondary));
  background-clip: text;
  margin-bottom: -1rem;
`;

