<script>
  import Logo from "../components/Icon.svelte";
  import Input from "../components/input/Text.svelte";
  import googleLogo from "../assets/icon/google_logo.png";
  import naverLogo from "../assets/icon/naver_logo.png";
  import kakaoLogo from "../assets/icon/kakao_logo.png";
  import appleLogo from "../assets/icon/apple_logo.png";

  // login
  let email = "",
    password = "";

  $: submit = async () => {
    console.log(email, password);
    await axios.post("http://13.209.44.41:8080/user/login", {
      email,
      password,
    });
    await push("/");
  };
</script>

<section class="bg-gray-50">
  <div
    class="flex flex-col items-center justify-center px-6 py-8 mx-auto md:h-screen lg:py-0"
  >
    <a
      href="/"
      class="flex items-center mb-6 text-2xl font-semibold text-gray-900"
    >
      <Logo />
    </a>
    <div class="w-full bg-white rounded-lg shadow md:mt-0 sm:max-w-md xl:p-0">
      <div class="p-6 space-y-4 md:space-y-6 sm:p-8">
        <h1
          class="text-xl font-bold leading-tight tracking-tight text-gray-900 md:text-2xl"
        >
          로그인
        </h1>
        <!-- Login with another account -->
        <!-- <div class="items-center grid grid-cols-2 gap-2">
          <button
            class="flex items-center justify-center bg-white-50 border border-gray-300 rounded-lg hover:bg-gray-100 font-medium p-2"
          >
            <img class="w-4 h-4 mr-2" src={googleLogo} alt="googleLogo" />
            Log in with Google
          </button>
          <button
            class="flex items-center justify-center bg-white-50 border border-gray-300 rounded-lg hover:bg-gray-100 font-medium p-2"
          >
            <img class="w-5 h-5 mr-2" src={naverLogo} alt="naverLogo" />
            Log in with Naver
          </button>

          <button
            class="flex items-center justify-center bg-white-50 border border-gray-300 rounded-lg hover:bg-gray-100 font-medium p-2"
          >
            <img class="w-5 h-5 mr-2" src={kakaoLogo} alt="kakaoLogo" />
            Log in with Kakao</button
          >
          <button
            class="flex items-center justify-center bg-white-50 border border-gray-300 rounded-lg hover:bg-gray-100 font-medium p-2"
          >
            <img class="w-5 h-5 mr-2" src={appleLogo} alt="appleLogo" />
            Log in with Apple</button
          >
        </div>  <hr />-->
        <div>
          <label
            for="email"
            class="block mb-2 text-sm font-medium text-gray-900">이메일</label
          >
          <Input type="email" placeholder="name@company.com" />
        </div>
        <div>
          <label
            for="password"
            class="block mb-2 text-sm font-medium text-gray-900">비밀번호</label
          >
          <Input type="password" placeholder="••••••••" />
        </div>
        <div class="pt-2">
          <button
            type="submit"
            class="w-full text-white bg-blue-600 hover:bg-blue-700 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center"
            >로그인</button
          >
        </div>
      </div>
    </div>
    <div class="flex items-center justify-between gap-3 mt-4">
      <a href="/" class="text-sm font-medium text-gray-600 hover:underline"
        >비밀번호 찾기</a
      ><span class="font-light text-sm text-gray-300">|</span><a
        href="/signup"
        class="text-sm font-medium text-gray-600 hover:underline">회원가입</a
      >
    </div>
  </div>
</section>
