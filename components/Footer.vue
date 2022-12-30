<template>
  <footer>
    <div class="first-container">
      <div class="netflix-logo">
        <img src="../assets/imgs/netflix.png" alt="">
      </div>
      <div class="first-column">
        <p>About</p>
        <p>Contacts</p>
        <p>Help</p>
        <p>Info</p>
      </div>
      <div class="second-column">
        <p>Privacy Policy</p> 
        <p>Terms & Conditions</p>
        <p>Feedback</p> 
      </div>
      <div class="third-column">
        <input type="email" name="" class="email" placeholder="E-mail Address">
        <button>Subscribe Now</button>
      </div>
    </div>
  </footer>
</template>

<script>
export default {

}
</script>

<style lang="scss" scoped>
  footer {
    background: #000000;
    color: red;
    display: flex;
    flex-direction: column;
    padding: 4rem 0;
    // padding-bottom: 0;
    font-size: 15px;
    margin-top: 5rem;

    .first-container {
      display: flex;
      justify-content: space-around;

      @media (max-width: 750px) {
        flex-direction: column;
        align-items: center;
      }

      p {
        margin-bottom: 15px;
        font-size: 1rem;
        cursor: pointer;
      }

      .netflix-logo {
        width: 10%;
        margin-top: -2rem;

        @media (max-width: 750px) {
          width: 20%;
          margin-bottom: 1.5rem;
        }

        img {
          width: 100%;
          height: 100%;
          object-fit: cover;
        }
      }

      .first-column {
        @media (max-width: 750px) {
          display: flex;
          justify-content: space-between;
          width: 50%;
        }

        @media (max-width: 500px) {
          width: 85%;
        }
      }

      .second-column {
        @media (max-width: 750px) {
          display: flex;
          justify-content: space-between;
          width: 75%;
          margin-top: 5px;
        }

        @media (max-width: 500px) {
          width: 85%;
        }
      }

      .third-column {
        display: flex;
        flex-direction: column;

        @media (max-width: 750px) {
          display: flex;
          flex-direction: row;
          justify-content: space-evenly;
          width: 75%;
          margin-top: 1.5rem;
        }

        @media (max-width: 500px) {
          flex-direction: column;
          width: 50%;
        }

        .email {
          background: transparent;
          color: red;
          border: 1px solid red;
          border-radius: 5px;
          padding: 10px;
          width: 15rem;
          margin-bottom: 3px;

          &:focus {
            outline: none;
          }

          @media (max-width: 500px) {
            width: 100%;
          }
        }

        button {
          background: red;
          color: black;
          border: 1px solid black;
          border-radius: 5px;
          padding: 7.5px;
          cursor: pointer;

          &:hover {
            background: transparent;
            color: red;
            border: 1px solid rgb(255, 0, 0);
          }
        }
      }
    }

    .second-container {
      text-align: center;
      margin-bottom: 1rem;
        margin-top: 3rem;
      
      @media (max-width: 750px) {
      }

      .icons {
        display: flex;
        justify-content: space-around;
        width: 20%;
        margin: 10px auto;
        color: black;
      }
    }
  }
</style>