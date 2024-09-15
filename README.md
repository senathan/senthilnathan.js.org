# senthilnathan.js.org

import React, { useState } from 'react';
import styled from 'styled-components';

// Styled components
const NavButtonSvg = styled.svg`
  fill: var(--clr-primary);
  position: fixed;
  top: 5%;
  left: 5%;
  cursor: pointer;
  z-index: 1;
`;

const Navbar = styled.nav<{ isOpen: boolean }>`
  position: fixed;
  background-color: rgba(0, 0, 0, 0.9);
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  transition: var(--transition);
  transform: ${({ isOpen }) => (isOpen ? 'translateX(0)' : 'translateX(-100%)')};
  z-index: 3;

  @media screen and (min-width: 768px) {
    width: 35%;
    max-width: 25rem;
  }
`;

const NavbarHeader = styled.div`
  position: relative;
`;

const NavbarTitle = styled.h3`
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

const NavbarHeaderImg = styled.img`
  width: 100px;
  margin: 0 auto;
`;

const NavClose = styled.span`
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

const NavItems = styled.ul`
  list-style: none;
`;

const NavLink = styled.a`
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

const Overlay = styled.div<{ isOpen: boolean }>`
  position: fixed;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
  background: rgba(0, 0, 0, 0.5);
  z-index: 2;
  display: ${({ isOpen }) => (isOpen ? 'block' : 'none')};
`;

// Main Component
const NavbarComponent: React.FC = () => {
  // Manage the state of the navbar (open/closed)
  const [isOpen, setIsOpen] = useState(false);

  // Toggle function
  const toggleNavbar = () => {
    setIsOpen(!isOpen);
  };

  return (
    <>
      {/* Nav button */}
      <div className="nav-btn" onClick={toggleNavbar}>
        <NavButtonSvg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960" width="24px" fill="#5f6368">
          <path d="M120-240v-80h720v80H120Zm0-200v-80h720v80H120Zm0-200v-80h720v80H120Z" />
        </NavButtonSvg>
      </div>

      {/* Overlay */}
      <Overlay isOpen={isOpen} onClick={toggleNavbar} />

      {/* Navbar */}
      <Navbar isOpen={isOpen}>
        <NavbarHeader>
          <NavbarTitle>TFC NATION</NavbarTitle>
          <NavbarHeaderImg src="images/chicken.png" alt="TFC" />
          <NavClose onClick={toggleNavbar}>
            <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960" width="24px" fill="#5f6368">
              <path d="m336-280 144-144 144 144 56-56-144-144 144-144-56-56-144 144-144-144-56 56 144 144-144 144 56 56ZM480-80q-83 0-156-31.5T197-197q-54-54-85.5-127T80-480q0-83 31.5-156T197-763q54-54 127-85.5T480-880q83 0 156 31.5T763-763q54 54 85.5 127T880-480q0 83-31.5 156T763-197q-54 54-127 85.5T480-80Zm0-80q134 0 227-93t93-227q0-134-93-227t-227-93q-134 0-227 93t-93 227q0 134 93 227t227 93Zm0-320Z" />
            </svg>
          </NavClose>
        </NavbarHeader>

        <NavItems>
          <li><NavLink href="#header">Home</NavLink></li>
          <li><NavLink href="#features">Features</NavLink></li>
          <li><NavLink href="#about">About</NavLink></li>
          <li><NavLink href="#products">Product</NavLink></li>
          <li><NavLink href="#contact">Contact</NavLink></li>
        </NavItems>
      </Navbar>
    </>
  );
};

export default NavbarComponent;
