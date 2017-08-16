# TidyGherkin

Fork of [the Chrome extension](https://chrome.google.com/webstore/detail/tidy-gherkin/nobemmencanophcnicjhfhnjiimegjeo) 0.4.6. 
Adds support for generating JS definitions in the format for [nightwatch-cucumber](https://github.com/mucsi96/nightwatch-cucumber) using es6. 

Matches [examples](https://github.com/mucsi96/nightwatch-cucumber/tree/master/examples/babel-example).

```js
import { client } from 'nightwatch-cucumber'
import { defineSupportCode } from 'cucumber'

defineSupportCode(({ Given, Then, When }) => {
  Given(/^I open Google`s search page$/, async () => {
    await client.url('http://google.com')
    await client.waitForElementVisible('body', 1000)
  })

  Then(/^the title is "(.*?)"$/, async (text) => {
    await client.assert.title(text)
  })

  Then(/^the Google search form exists$/, async () => {
    await client.assert.visible('input[name="q"]')
  })

  Given(/^I open Yahoo`s search page$/, async () => {
    await client.url('http://yahoo.com')
    await client.waitForElementVisible('body', 1000)
  })

  Then(/^the Yahoo search form exists$/, async () => {
    await client.assert.visible('input[name="p"]')
  })
})
```
