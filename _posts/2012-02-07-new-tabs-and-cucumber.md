---
layout: post
title: New Tabs and Cucumber
---

While working on an internal app at [GitHub](http://github.com) I had to
write a [cucumber](http://cukes.info/) scenario that ran expectations
against a new tab that was opened. Here is how I did it.

### The Code

Searching around the internet, I finally found a tip on
[StackOverflow](http://stackoverflow.com/questions/3104348/ruby-on-rails-cucumber-how-do-i-follow-a-link-that-opens-a-new-window)
that got me moving in the right direction. In this context tabs are
referred to as windows.

```ruby
page.driver.browser.switch_to.window(page.driver.browser.window_handles.last)
```

This code grabs the browser object and calls switch\_to window on it and
passes in the last opened window.

Now all we need to do is wrap this in a step so we can use it in our
scenarios.

```ruby`
When /^I access the new tab$/ do
  page.driver.browser.switch_to.window(page.driver.browser.window_handles.last)
end
```

### The Caveat

This will only work if you are using
[selenium-webdriver](http://seleniumhq.org/docs/). It will [not work
with
capybara-webkit](https://github.com/thoughtbot/capybara-webkit/issues/47)
unfortunately. So I switched to selenium, but I told it to use chrome
instead of the default firefox and it still works great!

```ruby
Capybara.javascript_driver = :selenium
Capybara.register_driver :selenium do |app|
  Capybara::Selenium::Driver.new(app, :browser => :chrome)
end
```

### The Finale

Now its time to see the step in action. Notice I had to tag the feature
with @javascript so that it uses the selenium webdriver.

```ruby
@javascript
Feature: Open a discussion

  Scenario: staff opens a discussion with the mouse
    Given the following users exist:
      | username  | email                |
      | test-user | integration@test.com |
    And I am on the triage page
    When I follow "Can't get git running on my mac"
    And I access the new tab
    Then I should be on the discussion page for "5786909"
    And I should see "Can't get git running on my mac"
```

The link that I follow opens the new page in a new tab, I select the new
tab, then run my expectations against it.
