# automatewhatsappmessaging



This repository is to automate whatsapp messaging using gems in ruby !!

I have used gems watir,httparty and pry...

require 'watir-webdriver'
require 'rubygems'
require 'httparty'
require 'pry'



b = Watir::Browser.new :chrome
b.goto("https://web.whatsapp.com/")
sleep 10
b.text_field(title: "Search or start new chat").set 'whom you want to send the message'

b.send_keys :enter 
element=b.div(:class => "input") #THIS IS THE WAY OF WRITTING CLASS IN TEXT_FIELD

script = "return arguments[0].innerHTML = 'type your message here'" #returns us the HTML code of the webelement
19.times do
b.execute_script(script, element)
sleep 3
b.send_keys :enter
b.send_keys [:command, "a"] # in case of ubuntu/windows use control in place of command
b.send_keys :delete #in case of ubuntu/windows use backspace in place of delete
sleep 1
b.send_keys [:command, "z"] # in case of ubuntu/windows use control in place of command
sleep 1
b.send_keys :enter
end    #delete,command are for mac
