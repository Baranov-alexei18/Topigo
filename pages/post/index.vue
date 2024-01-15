<template>
  <div class="container flex pt-5 bg-gray-200">
    <div class="flex w-20 justify-items-start items-start">
      <button
        type="button"
        class="mx-auto flex-shrink-0 rounded-full p-1 text-gray-400 focus:outline-none focus:ring-white focus:ring-offset-2 focus:ring-offset-gray-800"
        @click="toHomePage"
      >
        <svg
          width="48"
          height="48"
          viewBox="0 0 24 24"
          fill="none"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            d="M12 22C10.0222 22 8.08879 21.4135 6.4443 20.3147C4.79981 19.2159 3.51809 17.6541 2.76121 15.8268C2.00433 13.9996 1.8063 11.9889 2.19215 10.0491C2.578 8.10929 3.53041 6.32746 4.92894 4.92894C6.32746 3.53041 8.10929 2.578 10.0491 2.19215C11.9889 1.8063 13.9996 2.00433 15.8268 2.76121C17.6541 3.51809 19.2159 4.79981 20.3147 6.4443C21.4135 8.08879 22 10.0222 22 12C21.9971 14.6513 20.9426 17.1931 19.0679 19.0679C17.1931 20.9426 14.6513 21.9971 12 22V22ZM11 8C10.8685 7.9999 10.7383 8.02573 10.6168 8.076C10.4953 8.12628 10.385 8.20002 10.292 8.293L7.292 11.293C7.19907 11.3865 7.12535 11.4972 7.075 11.619C7.02473 11.7394 6.99884 11.8685 6.99884 11.999C6.99884 12.1295 7.02473 12.2586 7.075 12.379C7.09376 12.4196 7.11725 12.4579 7.145 12.493L7.179 12.541C7.19 12.558 7.2 12.576 7.209 12.593C7.22663 12.629 7.24881 12.6626 7.275 12.693L10.137 15.693C10.3201 15.8849 10.572 15.9962 10.8372 16.0024C11.1023 16.0085 11.3591 15.9091 11.551 15.726C11.7429 15.5429 11.8542 15.291 11.8604 15.0258C11.8665 14.7607 11.7671 14.5039 11.584 14.312L10.337 13H16C16.2652 13 16.5196 12.8946 16.7071 12.7071C16.8946 12.5196 17 12.2652 17 12C17 11.7348 16.8946 11.4804 16.7071 11.2929C16.5196 11.1054 16.2652 11 16 11H10.414L11.707 9.707C11.8468 9.56715 11.942 9.38899 11.9806 9.19504C12.0192 9.00108 11.9994 8.80005 11.9237 8.61735C11.848 8.43465 11.7199 8.27849 11.5555 8.1686C11.3911 8.05872 11.1978 8.00005 11 8V8Z"
            fill="black"
          ></path>
        </svg>
      </button>
    </div>
    <div class="max-w-6xl mx-auto sm:px-6 lg:px-8">
      <p class="relative flex items-top justify-center text-5xl mb-4">TITLE</p>
      <div class="flex min-w-44 w-2/3 mx-auto">
        <img
          class="min-h-40 mx-auto"
          src="https://media.4-paws.org/5/b/4/b/5b4b5a91dd9443fa1785ee7fca66850e06dcc7f9/VIER%20PFOTEN_2019-12-13_209-2890x2000-1920x1329.jpg"
          alt="Cats"
        />
      </div>
      <div class="relative flex items-top text-xl mt-4">asdfasdfklj</div>

      <div class="flex items-center my-3">
        <div class="text-2xl mr-2">Дата публикации: </div>
        <pre></pre>
        <div class="text-2xl">  asd fasdfklj</div>
      </div>

      <div class="border-t-4 border-black">

      </div>
    </div>
  </div>
</template>
  
  <script>
export default {
  name: "postPage",
  methods:{
    toHomePage(){
      this.$router.push("/")
    }
  }
};
</script>
  