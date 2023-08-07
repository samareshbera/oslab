# This page describes how to install and setup PintOS

## Virtual Machine Setup

-- Create a Linux virtual machine (VM) using [Virtual Box](https://www.virtualbox.org/)

-- Check whether the installation is successful

## PintOS installation and Setup

### Download and Install
   
a) Download the PintOS source files using:
   
`wget https://samareshbera.github.io/files/pintos-src.tgz`

Note: `wget` will store the file in the same directory from which you run `wget`. Let's consider the directory as `PINTOS_DOWNLOAD_PATH`.

   b) Extract the PinOS source file using:

   `tar xvzf PINTOS_DOWNLOAD_PATH/pintos-src.tgz`

   c) Adding PintOS programs to `PATH`:

   * `sudo .bashrc` and add `$PINTOS_HOME/pintos/src/utils`

   * Note: `PINTOS_HOME = /home/` in this case

   * For example, `PATH=/usr/local/bin:$PATH:/home/pintos/src/utils`

   d) Configure `gdb` macros to use `gdb` with PintOS. The macros are stored in `$PINTOS_HOME/pintos/src/utils/pintos-gdb`

   * Go to `$PINTOS_HOME/pintos/src/utils/`

   * Open `pintos-gdb` using `gedit pintos-gdb`

   * Change `GDBMACROS` as follows: `GDBMACROS=$PINTOS_HOME/pintos/src/misc/gdb-macros`

   e) Go to `$PINTOS_HOME/pintos/src/utils` and build PintOS using `make`

   f) We will use `qemu` emulator in this course. To do so, change the following:

   * Go to `$PINTOS_HOME/pintos/src/threads`
   
   * Open `Make.vars` using `gedit Make.vars`
   
   * Change `SIMULATOR = --bochs` to `SIMULATOR = --qemu`
      
   
   ## Running PintOS Test-Cases

   Each project contains its own `tests` folder that contains individual tests. Some of the tests are the same across projects, and some vary. The tests are in your `build` folder under `tests/<project_name>/<test_name>`.

   The execution of a test generates three files in the same folder as the test’s source. The files have the same name as the test but have a different extension.

   * `output` - a text file with all of the console output created during the run of this test

   * `errors` - a text file with all of the error output created during the run of this test

   * `result` - a text file with the outcome of the test’s run should be one of two words `PASS` if the test succeeded and `FAIL` if the test failed.

   ### Running a Single Test

   a) Go to the project folder `$PINTOS_HOME/pintos/src/threads`

   b) Build the threads using `make`

   c) The `make` command will generate a new folder called `build`

   d) Tests for each project are located in the folder `$PINTOS_HOME/pintos/src/tests/`
      
   * Each project has a sub-folder that contains all its tests, 
      for example, `$PINTOS_HOME/pintos/src/tests/threads` contains all the tests for the `threads` project

   e) Go to `threads/build` folder

   f) Run `make tests/threads/alarm-single.result`

   The command will run the tests `alarm-single` and will generate the following files:

   * `$PINTOS_HOME/pintos/src/threads/build/tests/threads/alarm-single.output` contains anything that the test outputs during its run

   * `$PINTOS_HOME/pintos/src/threads/build/tests/threads/alarm-single.errors` contains any errors that occurred during the tests' run

   * `$PINTOS_HOME/pintos/src/threads/build/tests/threads/alarm-single.result` contains the test’s result, typically the word FAIL or PASS

   Note: If you would like to run the tests and see the output on your terminal, as well as store it in the `.output` file run your tests by passing `VERBOSE=1`, e.g.,

   `make VERBOSE=1 tests/threads/alarm-single.result`


   ### Running all the Test-Cases

   a) Go to folder `$PINTOS_HOME/pintos/src/threads`

   b) Build using `make`

   c) Go to `build` folder

   d) Build all the test with the target `check`: `make check`

   Note: To see output on terminal, use `make VERBOSE=1 check`


   Acknowledgement: This page is created based on https://www.ccs.neu.edu/home/skotthe/classes/cs5600/fall/2016/labs/pintos-setup.html
