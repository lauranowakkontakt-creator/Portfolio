<template>
  <!-- Logo: wizjer kamery z trójkątem play w środku -->
  <svg
    width="34"
    height="34"
    viewBox="0 0 34 34"
    fill="none"
    xmlns="http://www.w3.org/2000/svg"
    aria-label="Laura Nowak logo"
  >
    <!-- Zewnętrzna ramka (wizjer) -->
    <rect x="1" y="1" width="32" height="32" stroke="var(--accent)" stroke-width="1.5"/>

    <!-- Narożniki wizjera – lewy górny -->
    <path d="M1 8 L1 1 L8 1" stroke="var(--accent)" stroke-width="2.5" stroke-linecap="square"/>
    <!-- prawy górny -->
    <path d="M26 1 L33 1 L33 8" stroke="var(--accent)" stroke-width="2.5" stroke-linecap="square"/>
    <!-- prawy dolny -->
    <path d="M33 26 L33 33 L26 33" stroke="var(--accent)" stroke-width="2.5" stroke-linecap="square"/>
    <!-- lewy dolny -->
    <path d="M8 33 L1 33 L1 26" stroke="var(--accent)" stroke-width="2.5" stroke-linecap="square"/>

    <!-- Trójkąt play -->
    <polygon points="12,10 12,24 25,17" fill="var(--accent)"/>
  </svg>
</template>
