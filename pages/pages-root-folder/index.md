---
#
# Use the widgets beneath and the content will be
# inserted automagically in the webpage. To make
# this work, you have to use › layout: frontpage
#
layout: frontpage
header:
  image_fullwidth: https://raw.githubusercontent.com/eslam-mohamed-reda/HackingResources/master/images/header_homepage_131.jpg
widget1:
  title: "Sections"
  url: 'http://hacking-resources.com/sections.html'
  image: https://raw.githubusercontent.com/eslam-mohamed-reda/HackingResources/master/assets/img/apple-touch-icon-180x180-precomposed.png
  text: 'Hacking Resources Sections. Explore offensive and defensive content'
widget2:
  title: "<br>Practice Resources"
  url: 'http://phlow.github.io/feeling-responsive/info/'
  text: '<em>Practice</em> is key.<br/>Practice Resources to get you ready for real action.'
  video: '<img src="https://media.giphy.com/media/26BRzQS5HXcEWM7du/giphy.gif" width="302" height="182"/>'
widget3:
  title: "<br>Knowledge Base"
  url: 'http://phlow.github.io/feeling-responsive/info/'
  video: '<img src="https://media.giphy.com/media/10fAvEln0lB8Lm/giphy.gif" width="302" height="80"/>'
  text: '<em>Enjoy</em> reading variety of articles<br> to sharpen your skills'
#
# Use the call for action to show a button on the frontpage
#
# To make internal links, just use a permalink like this
# url: /getting-started/
#
# To style the button in different colors, use no value
# to use the main color or success, alert or secondary.
# To change colors see sass/_01_settings_colors.scss
#
callforaction:
  url: https://tinyletter.com/hacking-resources
  text: Inform me about new posts in hacking-resources ›
  style: alert
permalink: /index.html
#
# This is a nasty hack to make the navigation highlight
# this page as active in the topbar navigation
#
homepage: true
---

