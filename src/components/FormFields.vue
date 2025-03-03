<template>
    
    <div class="container">
    <div class="cta-form">
      <h2>Fill out the form!</h2> 
    <p>Check out the comments for line by line explanations. Form-related code starts on line 145.</p>
    </div>
    <form action="" class="form">
      
      <input type="text" placeholder="Name" class="form__input" id="name" />
      <label for="name" class="form__label">Name</label>

      <input type="email" placeholder="Email" class="form__input" id="email" />
      <label for="email" class="form__label">Email</label>

      <input type="text" placeholder="Subject" class="form__input" id="subject" />
      <label for="subject" class="form__label">Subject</label>
      
    </form>
  </div>
  <div class="explanation">
    <p>
      Before we get started, we have to understand how labels, placeholders, and input fields work and how they are used from a UX perspective.
    </p>
    <ul>
      <li>Input fields, by default, have outlines when they are in focus.*</li>
      <li>Placeholders are used to show users what information is needed in their respective fields.</li>
      <li>Placeholders are created using the <code>placeholder=""</code> attribute.</li>
      <li>Placeholders, by default, disappear when text fills the input field. This affects the <code>:placeholder-shown</code> pseudo-selector.*</li>
      <li>Labels are used for the same reason as placeholders, but don't disappear when text is in the input field. This is great because it allows users to always see what information is required.</li>
      <li>UX best practices tell us that labels should accompany items in forms (input fields, text areas, checkboxes, etc.).</li>
    </ul>
    <p>We'll be using several pseudo-selectors to create this effect.<br>This is the ONLY way to achieve this effect without any JavaScript.</p>
    <ul>
      <li><code><a href="https://developer.mozilla.org/en-US/docs/Web/CSS/:focus">:focus</a></code> — Represents an element (such as a form input) that has received focus.</li>
      <li><code><a href="https://developer.mozilla.org/en-US/docs/Web/CSS/:not">:not()</a></code> — Prevents the items passed into the argument from being selected.</li>
      <li><code><a href="https://developer.mozilla.org/en-US/docs/Web/CSS/::placeholder">:placeholder</a></code> — Represents the placeholder text of <code>input</code> and <code>textarea</code> elements.</li>
      <li><code><a href="https://developer.mozilla.org/en-US/docs/Web/CSS/:placeholder-shown">:placeholder-shown</a></code> — Represents any <code>input</code> or <code>textarea</code> element that is currently displaying placeholder text.</li>
    </ul>
    <p>A non-SCSS version can be found <a href="https://codepen.io/kvncnls/pen/eYzbJJL" target="_blank">here</a> for those that don't use SCSS. Note that this older CodePen has a ROOT font-size of 10px, so any 'rem' values are based on 10px.</p>
  </div>

</template>

<script>

    export default{
        name: 'FormFields',
        data(){
            return{}
        },

    }

</script>

<style>

    /* Inter / Sans-serif */
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@100;200;300;400;500;600;700;800;900&display=swap');

/* Global Styles */
*,
*::before,
*::after {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  text-decoration: none;
}

html {
  --black: #303030;
  --grey: #909090;
  --off-white: #EDEEE9;
  --code: #D8DBCE;
  --sans-serif: 'Inter', sans-serif;
  position: relative;
  overflow-x: hidden;
  scroll-behavior: smooth;
  background-color: var(--off-white);
}

body {
  background-color: var(--off-white);
  color: var(--black);
  font-family: var(--sans-serif);
  min-height: 100vh;
  width: 100%;
  padding: 2.5vh 10vw;
  
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: flex-start;
}

h1 {
  font-size: clamp(1rem, 6vw, 10rem);
  margin: 15vh 0 2rem;
}

a {
  text-decoration: underline;
  color: var(--black);
}

code {
  font-size: 1rem;
  padding: 0 0.5rem;
  background-color: var(--code);
}

.explanation {
  width: 100%;
  margin-bottom: 15vh;
}

.explanation p {
  font-size: 1rem;
  max-width: 75ch;
  margin: 2rem 0;
}

.explanation ul:last-child {
  margin-bottom: 2rem;
}

.explanation ul {
  display: flex;
  flex-direction: column;
}

.explanation ul li {
  list-style: none;
  position: relative;
  margin: 0.5rem 0;
}

.explanation ul li::before {
  content: '👉';
  position: absolute;
  top: -0.25rem;
  left: -2rem;
}

.container {
  width: 100%;
  max-width: 768px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding: 2rem 2rem 1.5rem;
  background-color: var(--code);
}

@media (min-width: 768px) {
  .container {
    flex-direction: row;
    align-items: center;
  }
}

.cta-form {
  margin-bottom: 2rem;
  text-align: center;
}

@media (min-width: 768px) {
  .cta-form {
    margin-bottom: 0;
    margin-right: 2rem;
    text-align: left;
  }
}

.cta-form h2 {
  font-size: 1.5rem;
  width: 100%;
  max-width: 25ch;
  margin: 0 auto;
  text-align: center;
}

@media (min-width: 768px) {
  .cta-form h2 {
    text-align: left;
    margin: 0;
  }
}

.cta-form p {
  margin-top: 1rem;
  font-size: 1rem;
  width: 100%;
  max-width: 24ch;
}

/* Before someone yells at me for my improper use of SCSS— I know— 
   This isn't using SCSS's 'cascading' methodology. The form's styling is outside of the body tag.
   I'm just doing it this way so I can minimize non-relevant code. 😁 */
/* #################### ########################### #################### */
/* #################### All form-related CSS below. #################### */
/* #################### ########################### #################### */

.form {
  align-self: center;
}

/* I would use the BEM method here for declaring styles,
   but for the sake of clarity, I decided not to. */

/* Just some basic input field styling. */
.form__input {
  width: clamp(120px, 50vw, 420px);
  height: 2.5rem;
  padding: 0 1.25rem;
  border: 1px solid var(--black);
  border-radius: 2px;
  margin: 0.625rem auto;
  transition: all 250ms;
}

@media (min-width: 768px) {
  .form__input {
    width: clamp(120px, 35vw, 420px);
  }
}

/* This is basically saying when the form__input class is in focus */
.form__input:focus {
  outline: none;
  border-top-color: rgba(0,0,0,0.1);
}

/* When the input field (.form__input) is in focus, 
   transform the .form__label and change colors
   ALSO, if the input field's placeholder is NOT shown (when the input field has content),
   transform the .form__label and change colors. */
.form__input:focus + .form__label, .form__input:not(:placeholder-shown) + .form__label {
  transform: translateY(-4.50rem) scale(1);
  color: var(--black);
}

/* THIS PART IS IMPORTANT!!
   The block below hides the placeholder entirely.
   For all intents and purposes, the placeholder no longer exists.
   What shows on the input field is only the label.
   HOWEVER, the input fields still recognizes that the placeholder exists!
   The placeholder is just invisible. We need the placeholder to exist for
   some weird CSS stuff. If we skip this, we can't make it CSS-only. */
.form__input::placeholder {
  display: none;
  color: transparent;
  
  /* Prevents users from highlighting the placeholder. */
  -webkit-user-select: none; /* Safari */
  -ms-user-select: none; /* IE 10 and IE 11 */
  user-select: none; /* Standard syntax */
}

/* When the placeholder is NOT shown,
   style the top border.
   This makes the top border fade-out when the placeholder disappears. */
.form__input:not(:placeholder-shown) {
  border-top-color: rgba(0, 0, 0, 0.5);
}

.form__label {
  font-size: 1rem;
  color: var(--grey);
  display: block;
  
  /* Moves the label on TOP of the placeholder */
  /* You'll need to change this as needed */
  transform: translate(1.25rem,-2.5rem);
  transform-origin: 0 0; /* Used later for transitions */
  transition: all 500ms;
  
  /* Prevents users from highlighting the label. */
  -webkit-user-select: none; /* Safari */
  -ms-user-select: none; /* IE 10 and IE 11 */
  user-select: none; /* Standard syntax */
  
  /* THIS PART IS IMPORTANT!
     This line prevents the label from being selected.
     This is crucial because if this line doesn't exist, users can
     click on the label, instead of the input field. That's bad UX! */
  pointer-events: none; 
}    

</style>