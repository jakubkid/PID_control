# CarND-Controls-PID
Self-Driving Car Engineer Nanodegree Program
## Intro
Solution based on template From [repository] (https://github.com/udacity/CarND-PID-Control-Project)
The solution utilizes PID controller to control car steering and speed to complete the track. 

The desired track and error from it are generated with [Simulator](https://github.com/udacity/self-driving-car-sim/releases)

Communication with simulator is done with [uWebSocketIO](https://github.com/uWebSockets/uWebSockets) which can be installed on [Linux](install-ubuntu.sh) and [Mac](install-mac.sh). 
Development on Windows is possible in Visual Studio using [vcpkg](https://github.com/fkeidel/CarND-Term2-ide-profile-VisualStudio/tree/master/VisualStudio). You can also use emulator like Docker, VMware, or [Windows 10 Bash on Ubuntu](https://www.howtogeek.com/249966/how-to-install-and-use-the-linux-bash-shell-on-windows-10/).

Once the install for uWebSocketIO is complete, the main program can be built and run by doing the following from the project top directory. 
Visual studio was used to compile the code.

## Reflection

In the implementation 2 controllers were used. 1st is PD controlled which regulates steer value based on cte error received from simulator. PD controller was selected because when driving the car desired position changes and it is not so important to cancel out the error.
Second controller is responsible for tuning speed based on current steering angle. It only uses P component because its set point is changed very rapidly and would cause D component to over react likewise steer value controller it doesn't need to cancel out the error completely.

Hyperparameter selection was done manually. First only steer value controller was used with P value until the car was able to complete some turns but was oscillating a lot, next D term was added which helped a lot with oscillations. P term of speed controller was added to increase the speed on straight and was selected to be quite gentle. 
Describe the effect each of the P, I, D components had in your implementation. For results either run the code or check this [video](https://github.com/jakubkid/PID_control/blob/master/video/fullRun.wmv)

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

