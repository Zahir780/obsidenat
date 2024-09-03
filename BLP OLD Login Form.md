44@page
@model LoginModel

@{
    Layout = "/Views/Shared/_Login.cshtml";
    ViewData["Title"] = "Log in";
}
<style>
    .hidden {
        display: none;
    }

</style>

@*<section id="cover" class="min-vh-100">
    <div id="cover-caption">
        <div class="container">
            <div class="row">
                <div class="col-xl-5 col-lg-6 col-md-8 col-sm-10 mx-auto text-center form" style="padding-right: 0px; padding-left: 0px;">
                    <div class="p-5" style="color: white;">
                        <div class="text-center">
                            <img asp-append-version="true" src="/images/logo.png" style="width: 90px;" alt="BLP" />
                            <h1 class="mt-2 mb-4 pb-1">BLP</h1>
                        </div>

                        <div class="px-4">
                            <form form id="account" method="post" class="justify-content-center">
                                <p>Please login to your account</p>
                                <div class="form-group">
                                    <label style="float: left;" asp-for="Input.Email"></label>
                                    <input type="text" asp-for="Input.Email" class="form-control" placeholder="your user name or email" style="border-top:0px">
                                    <span asp-validation-for="Input.Email" class="text-danger"></span>
                                </div>
                                <div class="form-group" style="margin-bottom: 30px;">
                                    <label style="float: left;" asp-for="Input.Password"></label>
                                    <input type="password" asp-for="Input.Password" class="form-control" placeholder="your password" style="border-top:0px">
                                    <span asp-validation-for="Input.Password" class="text-danger"></span>
                                </div>
                                <button type="submit" class="btn btn-primary btn-lg" style="width: 100% !important;background-color: #dc3545;border-color: #dc3545;">Log in</button>
                            </form>
                            <div style="text-align: right;"><a style="color: white;width: 100%;" asp-area="Identity" asp-page="/Account/ForgotPassword">Forget Password</a></div>
                        </div>
                    </div>
                    <div class="gradient-custom-2">
                      <img src="/images/esl_logo1.png" height="28" alt="Evision Software Ltd." style="margin-right: 10px;" />
                      <span style="margin-right:5px;">&copy; Powered by: </span><a style="color: #fff;" target="_blank" href="http://www.eslctg.com">Evision Software Ltd.</a> 
                    </div>
                </div>
            </div>
         </div>
        </div>
    </section>*@


<div class="ftco-section">
    <div class="container">

        <div class="row justify-content-center" style="height: 100%;margin: auto;">
            <div class="col-md-12 col-lg-10" style="padding:0px !important;">
                <div class="wrap d-md-flex">
                   @*  <div class="text-wrap p-4 p-lg-5 text-center d-flex align-items-center order-md-last">
                        <div class="text w-100">
                            <h2>Welcome to BLP</h2>
                            <p>Garments Industry</p>
                            <img class="banner-img1" src="~/images/garments.jpg" />
                            <img class="banner-img1" src="~/images/garments2.jpg" />
                          
                        </div>
                    </div> *@
                    <div class="text-wrap p-4 p-lg-5 text-center d-flex align-items-center order-md-last" style="width: 100%;">
                        <div class="text w-100">
                            <h2>Welcome to BLP</h2>
                            <p>Garments Industry</p>
                            <img class="banner-img1" src="~/images/garments3.jpg" id="garments3-image" />
                            <img class="banner-img1" src="~/images/garments2.jpg" id="garments2-image" />
                        </div>
                     </div>


                        <div class="login-wrap" style="width: 100%;">
                        <div class="d-flex header-logo">
                          @*  <img asp-append-version="true" src="/images/BLP.png" style="width: 15rem" alt="BLP" />*@
                           @* <div class="w-100" style="font-style: italic;font-size: 20px;">
                                <h3 class="mb-4">SHAJINAZ EXIM PACK LTD</h3>
                            </div>*@

                        </div>
                        <div class="p-4 p-lg-5">
                            <div class="d-flex">
                                <div class="w-100">
                                    <p class="mb-4">Login to your account</p>
                                </div>
                                <div class="w-100">
                                    <p class="social-media d-flex justify-content-end">
                                        <a href="#" class="social-icon d-flex align-items-center justify-content-center"><span class="fa fa-facebook"></span></a>
                                        <a href="#" class="social-icon d-flex align-items-center justify-content-center"><span class="fa fa-twitter"></span></a>
                                    </p>
                                </div>
                            </div>
                            <form form id="account" method="post" class="signin-form">
                                <div class="form-group mb-3">
                                    <label class="label" for="name">Email</label>
                                    <input type="text" asp-for="Input.Email" class="form-control" placeholder="Email" required="">
                                    <span asp-validation-for="Input.Email" class="text-danger"></span>
                                </div>
                                <div class="form-group mb-3">
                                    <label class="label" for="password">Password</label>
                                    <input type="password" asp-for="Input.Password" class="form-control" placeholder="Password" required="">
                                    <span asp-validation-for="Input.Password" class="text-danger"></span>
                                </div>
                                <div class="form-group">
                                    <button type="submit" class="form-control btn btn-primary submit px-3">Sign In</button>
                                </div>
                                <div class="form-group d-flex">
                                    <div class="w-100 text-left">
                                        <label class="checkbox-wrap checkbox-primary mb-0">
                                            Remember Me
                                            <input type="checkbox" checked="">
                                            <span class="checkmark"></span>
                                        </label>
                                    </div>
                                    <div class="w-100 text-md-right" style="font-size: 14px;">
                                        <a asp-area="Identity" asp-page="/Account/ForgotPassword">Forgot Password</a>
                                    </div>
                                </div>
                            </form>
                            <div>
                                <div class="w-100" style="text-align:right;">
                                    <span style="margin-right:5px;font-size: 12px;">&copy; Powered by: </span>
                                    <a target="_blank" href="http://www.eslctg.com"><img src="/images/esl-LOGO.png" height="40" width="100" alt="Evision Software Ltd."  /></a>
                                </div>
                            </div>
                        </div>
                       
                        
                    </div>
                </div>
            </div>
        </div>
    </div>
</div>



    @section Scripts
    {
        <partial name="_ValidationScriptsPartial" />
    }
44

  

