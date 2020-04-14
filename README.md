# WiringPi
WiringPi is an implementation of most of the Arduino Wiring functions for the Raspberry Pi, this gem is a wrapper for the main wiringpi library and provides a nice OO interface with a few other handy helpers.

This branch of this fork has been updated to work on the Raspberry Pi 4.  This branch is specifically tied to WiringPi binary version 2.50 [here](https://github.com/WiringPi/WiringPi/releases/tag/final_official_2.50).  That is the maintenance repo for Wiring Pi now that Gordon Henderson (who long gave us all his great work) has deprecated his repo.

## Installation

The offical rubygems version does not support Raspberry Pi 4, this branch of this fork will work with the Raspberry Pi 4.

```
gem install specific_install
sudo gem specific_install -l https://github.com/davidgyoung/WiringPi-Ruby.git -b wiringpi250
```

## Example
```
#!/usr/bin/env ruby

require 'bundler'
Bundler.setup
Bundler.require

io = WiringPi::GPIO.new do |gpio|
  gpio.pin_mode(0, WiringPi::OUTPUT)
  gpio.pin_mode(1, WiringPi::INPUT)
end

pin_state = io.digital_read(1) # Read from pin 1
puts pin_state

io.digital_write(0, WiringPi::HIGH) # Turn pin 0 on
io.delay(100)                       # Wait
io.digital_write(0, WiringPi::LOW)  # Turn pin 0 off
```
You will need to run your scripts as root because WiringPi accesses `/dev/mem`

## Reference

### Pins
For a complete run-down see the [pins page](http://wiringpi.com/pins/) of the [wiringpi website](http://wiringpi.com/).
![alt text](http://wiringpi.com/wp-content/uploads/2013/03/gpio1.png "The main GPIO connector")
![alt text](http://wiringpi.com/wp-content/uploads/2013/03/gpio21.png "The secondary GPIO connector")

### More
Full details on the [wiringpi website](http://wiringpi.com/).
