---
layout: default
title: Support
---

# Support ZeroBrane Studio. Pay what you want. Download and run in 30 seconds.

<img style="float: right; padding: 10px 40px 10px 0px" src="images/lua-ide-benefits-screenshot.png" />

<form action="#" id="PayForm" name="PayForm">
 <table class="payment" id="payment-options">
  <tr><td class="amount">  $5</td><td class="description"><input name="payment" id="amount5" value="5" type="radio" /><label for="amount5">This is better than chocolate Mocha</label></td></tr>
  <tr><td class="amount"> $10</td><td class="description"><input name="payment" id="amount10" value="10" type="radio" /><label for="amount10">I will pay more when my game sells</label></td></tr>
  <tr><td class="amount"> $24</td><td class="description"><input name="payment" id="amount24" checked="checked" value="24" type="radio" /><label for="amount24"><strong>Exactly what I was looking for</strong></label></td></tr>
  <tr><td class="amount"> $50</td><td class="description"><input name="payment" id="amount50" value="50" type="radio" /><label for="amount50">I feel lucky and generous today</label></td></tr>
  <tr><td class="amount">$100</td><td class="description"><input name="payment" id="amount100" value="100" type="radio" /><label for="amount100">Take my money; just keep working on it</label></td></tr>
  <tr><td class="amount">$<input disabled="disabled" type="text" value="other" id="amountValue" /></td><td class="description"><input name="payment" id="amountOther" value="" type="radio" /><label for="amountOther">I have something else on my mind</label></td></tr>
 </table>

 <div id="next-step">
  <span class="gh-btn"><a class="button" id="pay-with-card-button" href="#">Pay with Card</a></span>
  <a href="download.html?not-this-time" id="no-payment-text">Take me to the download page this time &#187;</a>
 </div>
</form>

<script>
$(document).ready(function(){
  $("input[name=payment]").click(function() {
    var amount = $("#amountValue")
    amount.attr("disabled", true);
    if ($(this).attr('id') == 'amountOther') {
      amount.attr("disabled", false);
      amount.select();
      amount.focus();
    }
  });
  $('a#pay-with-card-button').click(function(e){
    var selected = $('input[name=payment]:checked');
    var amount = selected.attr('id') == 'amountOther' ? $('#amountValue').val() : selected.val();
    if (!isNaN(parseFloat(amount))) if (amount >= 1) {
      var url = 'https://zerobrane.com/pay/zbs?amount=' + amount;
      modal.open({content: "<iframe src='"+url+"' style='width: 430px; height: 350px' frameborder='0' scrolling='no'></iframe>"});
    }
    e.preventDefault();
  });
});
</script>

<div class="separator">&nbsp;</div>

## What do I get?
You get packages for three platforms:
**Windows** XP or later (zip or self-extracting archive), **Mac OS X** 10.6.8+ (dmg file), or **Linux** (shell archive for Debian, Ubuntu, Xubuntu, Mint, ArchLinux, Fedora, Gentoo and other distributions).

## How much do I pay?
This is completely up to you. How much do you value being able to find
an issue with your code in 5 minutes instead of 15? Get your mobile 
application out faster? Have fun helping your kids or friends learn
programming using Lua and examples included with the IDE?

## Isn't this an open source project?
Yes and we make it easy for you to get code from GitHub and
run it from a cloned copy or an archive. We would still **appreciate your 
payment in support of this project.** If you decide not to provide financial
support this time, please consider spreading the word, contributing code,
helping with [fixes](https://github.com/pkulchenko/ZeroBraneStudio/issues)
or [documentation](documentation.html),
and answering questions other users may have.
