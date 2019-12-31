---
#
# Use the widgets beneath and the content will be
# inserted automagically in the webpage. To make
# this work, you have to use › layout: frontpage
#
layout: frontpage
header:
  image_fullwidth: "pattern_concrete.jpg"
widget1:
  title: "Sections"
  url: 'http://hacking-resources.com/sections'
  text: 'Hacking Resources Sections. Explore offensive and defensive content'
widget2:
  title: "Practice Resources"
  url: 'https://hacking-resources.com/practice-resources.html'
  text: '<em>Practice</em> is key.<br/>Practice Resources to get you ready for real action.'
widget3:
  title: "Blog"
  url: 'https://hacking-resources.com/blog/'
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
  url: http://hacking-resources.com/subscribe
  text: Inform me about new posts in hacking-resources ›
  style: alert
permalink: /index.html
#
# This is a nasty hack to make the navigation highlight
# this page as active in the topbar navigation
#
homepage: true
---

