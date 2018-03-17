# CarND-Controls-PID
Self-Driving Car Engineer Nanodegree Program

---

## Dependencies

* cmake >= 3.5
 * All OSes: [click here for installation instructions](https://cmake.org/install/)
* make >= 4.1(mac, linux), 3.81(Windows)
  * Linux: make is installed by default on most Linux distros
  * Mac: [install Xcode command line tools to get make](https://developer.apple.com/xcode/features/)
  * Windows: [Click here for installation instructions](http://gnuwin32.sourceforge.net/packages/make.htm)
* gcc/g++ >= 5.4
  * Linux: gcc / g++ is installed by default on most Linux distros
  * Mac: same deal as make - [install Xcode command line tools]((https://developer.apple.com/xcode/features/)
  * Windows: recommend using [MinGW](http://www.mingw.org/)
* [uWebSockets](https://github.com/uWebSockets/uWebSockets)
  * Run either `./install-mac.sh` or `./install-ubuntu.sh`.
  * If you install from source, checkout to commit `e94b6e1`, i.e.
    ```
    git clone https://github.com/uWebSockets/uWebSockets 
    cd uWebSockets
    git checkout e94b6e1
    ```
    Some function signatures have changed in v0.14.x. See [this PR](https://github.com/udacity/CarND-MPC-Project/pull/3) for more details.
* Simulator. You can download these from the [project intro page](https://github.com/udacity/self-driving-car-sim/releases) in the classroom.

There's an experimental patch for windows in this [PR](https://github.com/udacity/CarND-PID-Control-Project/pull/3)

## Basic Build Instructions

1. Clone this repo.
2. Make a build directory: `mkdir build && cd build`
3. Compile: `cmake .. && make`
4. Run it: `./pid`. 

## Reflection

### Components Of PID

The PID controller is one of the simpler but efficient controllers. It is comprised of 3 parts:
* The steering is **P**roportional to the Crosstrack Error(CTE). The CTE is signalling how far off the middle of the track we are.
We are using a coefficient to know how much to steer. If this coefficient is too big the car will overshoot and oscillate.
If the coefficient is too small, the car will not be able to turn correctly.
* **I**ntegral sum of all the observed CTEs. 
If the absolute value of the sum becomes too big, it means that the car is only driving on one side of the track and maybe there is some bias. 
This helps is correct for that.
* **D**erivative of the CTE. This signals how fast and in what direction the CTE is changing.
With this term, the car can steer harder when it is off center and not steer much when it is closer to the center.

### Parameter Tuning

I used the parameters from the PID.
I found those to be sufficient for controlling both the steering and the speed of the car.
