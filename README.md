# SignUpTests
politrip
using System;
using Microsoft.VisualStudio.TestTools.UnitTesting;
using OpenQA.Selenium;
using OpenQA.Selenium.Chrome;

namespace SignUpTests
{   
        [TestClass]
        public class SignUpTests1
        {

            [TestMethod]

            public void SignUpWithFacebook()
            {

                IWebDriver driver = new ChromeDriver();
                driver.Url = "https://politrip.com/account/sign-up";
                IWebElement signUpFacebook = driver.FindElement(By.XPath("//*[@class='social-label']"));
                signUpFacebook.Click();
                driver.Quit();
            }

            [TestMethod]

            public void SignUpWithGoogle()

            {

                IWebDriver driver = new ChromeDriver();
                driver.Url = "https://politrip.com/account/sign-up";
                IWebElement signUpGoogle = driver.FindElement(By.XPath("//*[@class='social-label']"));
                signUpGoogle.Click();
                driver.Quit();
            }




            [TestMethod]

            public void SignUpWithInstagram()
            {

                IWebDriver driver = new ChromeDriver();
                driver.Url = "https://politrip.com/account/sign-up";
                IWebElement signUpInstagram = driver.FindElement(By.XPath("//*[@id='socialmedia-account-instagram-button']/div/span"));
                signUpInstagram.Click();
                driver.Quit();
            }




            [TestMethod]

            public void SignUpVK()
            {

                IWebDriver driver = new ChromeDriver();
                driver.Url = "https://politrip.com/account/sign-up";
                IWebElement acceptAllButton = driver.FindElement(By.CssSelector("div#cookiescript_accept"));
                acceptAllButton.Click();
                IWebElement signUpVK = driver.FindElement(By.CssSelector("span.social-label"));
                signUpVK.Click();
                driver.Quit();
            }



            [TestMethod]

            public void SignUpInvalidPasswords()
            {

                IWebDriver driver = new ChromeDriver();
                driver.Url = "https://politrip.com/account/sign-up";
                IWebElement password = driver.FindElement(By.XPath("//*[@id='sign-up-password-input']"));
                password.SendKeys("Pinguin12345");
                IWebElement confirmpassword = driver.FindElement(By.XPath("//*[@id='sign-up-confirm-password-input']"));
                password.SendKeys("Pngu");
                driver.Quit();
            }


            [TestMethod]


            public void SignUpInvalidPasswordEmail()
            {
                IWebDriver driver = new ChromeDriver();
                driver.Url = "https://politrip.com/account/sign-up";
                IWebElement email = driver.FindElement(By.XPath("//*[@id='email']"));
                email.SendKeys("vers@yahoo.com");
                IWebElement password = driver.FindElement(By.XPath("//*[@id='sign-up-password-input']"));
                password.SendKeys("Pngu");
                IWebElement confirmpassword = driver.FindElement(By.XPath("//*[@id='sign-up-confirm-password-input']"));
                password.SendKeys("Pngu");
                driver.Quit();
            }



            [TestMethod]

            public void SignUpValidEmailandPassword()
            {
                IWebDriver driver = new ChromeDriver(Environment.CurrentDirectory);
                driver.Url = "https://politrip.com/";
                IWebElement acceptAllButton = driver.FindElement(By.CssSelector("div#cookiescript_accept"));
                acceptAllButton.Click();
                IWebElement signUpLink = driver.FindElement(By.CssSelector("a#qa_header-signup.auth-button.signup-button"));
                signUpLink.Click();
                driver.Manage().Timeouts().ImplicitWait = TimeSpan.FromSeconds(5);
                IWebElement firstNameField = driver.FindElement(By.XPath("//*[@id='first-name']"));
                firstNameField.SendKeys("Alex");
                IWebElement lastNameField = driver.FindElement(By.XPath("//*[@id='last-name']"));
                lastNameField.SendKeys("Pancu");
                IWebElement email = driver.FindElement(By.XPath("//*[@id='email']"));
                email.SendKeys("alexpancu19@yahoo.com");
                IWebElement password1 = driver.FindElement(By.XPath("//*[@id='sign-up-password-input']"));
                password1.SendKeys("Pinguin123");
                IWebElement password2 = driver.FindElement(By.XPath("//*[@id='sign-up-confirm-password-input']"));
                password2.SendKeys("Pinguin123");
                IWebElement signUpButton = driver.FindElement(By.XPath("//*[@id='#qa_loader-button > span']span"));
                signUpButton.Click();
                var strUrl = driver.Url;
                string expectedUrl = "https://politrip.com/account/sign-up/type-select";
                var isEqual = expectedUrl.Equals(strUrl);
                Assert.IsTrue(isEqual);
                driver.Quit();
            }
        }
    }
