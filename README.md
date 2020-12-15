
# Payments, Addess and Checkout flow best practices

have you ever gone to a website and found it surprisingly difficult to fill in address and payment forms to complete your purchase? Especially on mobile? Or maybe you actually work on a website that sells stuff. Do you worry that you lose customers between shopping trolley and checkout? Here i will talk about some successful patterns for payments and checkout that can increase your conversion rates. 

## Things we will be covering:

- The Checkout Journey
- Easy Address and Contact Forms
- Payments Form

Checkout and payment design can make or break a business. One small fix through a code can have massive impact on conversion rate. So even if you are an experienced developer, I hope you will find something userful here. 

Well formed HTML is the core of a good checkout experience and it gives you meaningful readable code. 
First thing, use the elements built for the job. Your old friends
- Form
- Label
- Input 
- Button

Use these elements as intended and that enables cross-platform built in browser functionality and improves accessibility. You can style these elements just as you want and still take advantage of their special super powers.

## Form
So you might be tempted to avoid using a form element, just like wrap the inputs in a div or something and handle form submission purely with JavaScript. **Well, don't do it.** A plain old form gives you access to a powerful set of built-in features across all modern browsers and can help make your webapp accessible to screen readers and other assistive devices. An HTML form also makes it simpler to build basic functionality for older browsers with limited JavaScript support and to enable form submission even if there is a glitch with your code and actually for the small number of users who disabled JavaScript.

## Input 
As well as using a form, you should take advantage of all the features that the HTML input element has to offer. Input attributes provide a whole stack of useful standardized features. Let's see them in action.


As well as using a form, you should take advantage of all the features that the HTML input element has to offer. Input attributes provide a whole stack of useful standardized features. Let's see them in action.

1. **type attribute** : Make sure to use the appropriate type attribute to provide the right keyboard on mobile and to enable basic built in validation by the browser. No JavaScript required. 

For Emails :
~~~~
<input type="email" ...>
~~~~

For Telephone Numbers : 
~~~~
<input type="tel" ...>
~~~~

But watch out, using type="number" adds an up/down arrow to increment numbers and that makes no sense at all for data like credit card numbers or pin numbers. So instead you should use inputmode in such cases.

For Credit Card/Pin Numbers : 
~~~~
<input inputmode="numeric" ...>
~~~~

This will enable a numeric keyboard on mobile.
Some sites even use input type tel for credit cards to get the right keyboard, inputmode is widely supported, so please don't do that. Just use the default input type value, which is text.

In the examples here, I've actually said it explicitly, just to be clear.

**Help users avoid re-entering data.**


2. **autocomplete attribute** : Using appropriate autocomplete values enables browsers to help your users by securly storing data and autofilling inputs. By default, if an approrpriate autocomplete value is available for an input, well you should add it to your code. The complete lift can be found [here.](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes/autocomplete)


3. **required attribute** : Make sure to add the required attribute to the required fields. Reason being the modern browsers automatically prompt and set focus on the missing data when a form is submitted.

Okay, that's a lot about inputs, what about inpur labels? Well, to label and input, we use a label element. Associate a label with an input by giving a label *for* attribute the same value as the input's ID. 

~~~~
<label for="email"> Email </label>
<input id="email" ...>
~~~~

On your address form, use a single label for a single input and don't try to lable multiple inputs. A tap or a click on a label moves the focus to the associated input. Screen readers announce label text when the label or label's input gets focused. 

Placeholders can be useful, but don't use them solely as inpur labels. It can be really hard to remember what the input was for once you have started entering text. 

Lastly, use buttons for buttons. Button elements provide accessibile behaviour and built-in functionality for form submission. And you can also use input type submit but there is no point in using a div or some other element acting as a button. 

You should consider disabling a submit button once the user has tapped or clicked it, especially when they are making a payment or placing an order. Many users click buttons multiple times even when they are working fine and this can really mess up your checkout flow and add to server load. 

Now, on the other hand don't disable your submit button waiting on complete and valid user input. FOr example, don't just leave a make payment button disabled or if something is missing or invalid in an address form. It just looks like it's not working. Instead explain to the user what they need to do and show them how to fix it if they attempt to submit the form with an invalid data. 


Enough of HTML. Now, let's take a high level look at the whole checkout journey. 

The guiding principle here is pretty obvious. You can think of your users as having a fatigue budget. Once you have consumed too much of it, your users will leave. So you need to reduce friction and maintain focus. How can you structure the checkout journey so that you don't lose customers along the way? 
Well, its worth thinking about where your customers start and end their shopping journey. Many sites get more traffic on mobile, but far more conversions on desktop. You need to minimize lost conversions on mobile and maximize conversion once customers are on desktop. 

The mobile commerce gap, as it's been called, is partly about customers choosing to convert on desktop. However, lower mobile conversion rates can also be a result of bad user experience. Research has shown that there's a huge opportunity to provide a better form experience on mobile.
Most of all, users are more likely to abandon forms that look long, complex and without a sense of direction. Especially on smaller screens and when users get distracted or if they are in a rush. 

First of all, for an online store, you can reduce friction by making guest checkout the default. In other words, don't force to create an account before making a purchase. Not alloweing guest checkout is cited as a major reason for shopping cart abandonment. Let users select products and checkout with the minimun of data entry. You can offer account sign-up after checkout. At that point, you already have most if not all of the data you need to set up an account. 

So account creation should be quick and easy for the user.

**NOTE** : If you do offer sign-up after checkout, make sure that the purchase the user just made is linked to the newly created account. 

You can make your checkout process feel less complex, by clearly showing what needs to be done next. And by showing progress throughout the checkout flow, you need to maintain momentum. For each step towards checkout, use descriptive call to actions that make the next steps obvious. For example, you can label the submit button on your delivery address form as proceed to payment, rather than simply continue or save.

Limit potential exit points by removing visual clutter and distraction such as product promotions in the checkout step. Many successful retailers even remove navigation and such functionality at this step.

*Keep the Journey Focused*

This is not the time to tempt user to do something else.
For returning users, you can simplify the checkout flow even more by hiding data they don't need to see. 
For example, we can set the billing address to be same as the delivery address by default and then allow users to change it.

Cut down on visual clutter by displaying existing data as plain text rather than showing the data in a form. You should make it easy for the user to go back and forth, within the checkout flow particulary for adjusting their order when they are at the final payment step. The aim is to make life easier for users. And lastly, show full details of the order, before the final payment step. Some sites only show a limited summary, users should be able to quickly confirm that they havn't made any mistakes with the items or the quantity. Do make it POSSIBLE to edit item quantities from the payment page. 

Let's now dive into name and address forms. As I said before, the core princple is to **reduce form fatigue** especially on mobile, and for addresses that means minimizing the amount of typing.


### Ask for as little as possible

 Now first question, which is pretty obvious is, do you really need to get all the data you are asking for from the user? If you don't really need a name or a physical address don't ask for it.

### Avoid privacy 'data debt'

For example if you just want to show the nearest stor just ask for the zip or the postal code. 

- Use single input for name instead of multiple inputs like firstname and lastname. Doing so will reduce form size and make autofills and copy paste easier.

- Make sure you use right autocomplete values

- Use single address textarea for address field, as it will make copy and paste easier, but in case you decide to use seperate address fields make sure they are using correct autocomplete attributes and add labels to match.

- Wherever possible keep address form fields as flexible as possible, or else it will be hard for browsers to autofill address inputs.

- Use correct names for billing address and shipping address.

There is one trend these days to use a service to look up addresses based on postal code or zip. This might be sensible for some usecases, but you should be aware of the potential downsides. Postal code address suggestion doesn't work for all regions and in some regions postcodes can include a huge number of potential addresses. 

It can just be quicker and less error prone if we use let users take advantage of autofill. That way they can get complete address filled with a single tap or click. 

### Payment Forms

First up, once again is the autocomplete attribute helps the browser store and autofill data to users so that they don't have to type. This is particularly helpful for mobile where users may struggle to correctly enter their credit card number and other card details. 

You should add autocomplete values for credit card number, the name on the card, and for the expiry month and year. 

For dates as a general rule, avoid using custom select elements as they break the autofill experience if they are not implemented properly and they don't work on all the browsers.

You may also want to consider using a plain input element for data such as year, rather than a select. 
Using multiple inputs for credit card number and phone number. It's best not to do that. Use a single input instead.
It makes easier for user to enter the data and enables browser to autofill. 

You should add validation for data entry both in real-time and before submission. On way to do this is by adding pattern attribute to a credit card input. If the user attempts to submit the payment form with an invalid value, the browsers displays a warning message and also sets focus on the invalid field. NO JAVASCRIPT REQUIRED. But you should use JS for more robust validations. You can also use Constraint Validation API, which is widely supported to add custom validation using built in browser UI to det focus and display prompts. 

You may want to use One Time Passcode from user for address or payment verification. But just make sure that copy pasting is allowed in that field and that can be a source of friction. 

Now testing usability and performance locally, from your friends or colleagues can be helpful, but you need real-world data to properly understand how your users experience payments and address forms. And for that you need analytics and Real User Measurement(RUM). This means getting data for the experience of actual users, such as how long pages take to load, or **how long payment takes to complete.** For checkout forms use page analytics, for page views, bounce rate, exits and so on. 
Make sure to add interaction analytics, such as goal funnels, where users abandon your checkout flow and for events like what actions do users take when they are interacting with the forms. And lastly, track website performance for your users. 
Use wenb vitals to discover that. Now page analytics, interaction analytics along with real user performance  measurement  become especially valuable when combined with server logs, conversion data and AB testing. This helps to take decisions that whether a change in form layout improves conversions or not which gives a solid basis for priortizing effort and making changes. 


Special Thanks to 
1. Ali Sarraf (Product Manager on Chrome, works on password manager and autofill for payments and addresses)
2. Sam Dutton (Developer Advocate for the Chrome team)

