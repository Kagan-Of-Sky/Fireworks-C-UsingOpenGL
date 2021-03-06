# Fireworks-C-UsingOpenGL
Second assignment for our C programming course, I chose to create some fireworks. Uses the glut OpenGL framework.

## Compilation Instructions:
First, install the OpenGL Utility Toolkit (GLUT) using the following commands (Thanks to http://kiwwito.com/installing-opengl-glut-libraries-in-ubuntu/ for providing these):
+ sudo apt-get install freeglut3 freeglut3-dev
+ sudo apt-get install binutils-gold

Then compile the files using:
+ make -f Kaganovsky-Makefile

Then run using:
+ ./fireworks

Please run from the command line as the controls for spawning/deleting particles are shown on the standard output.

Below is the readme file (Kaganovsky_particles.txt):

<pre>
Author: Mark Kaganovsky

+-----------------------------------------------------------------------------------------------------------------+
| Description of This Particle System:                                                                            |
+-----------------------------------------------------------------------------------------------------------------+
|	
|	+ This particle system simulates fireworks being launched into the air and exploding.
|	
|	+ The size of the explosion depends upon the size of the firework (a large firework
|	  will spawn more particles than a small firework).
|	
|	+ You can click using the left and right mouse buttons to cause an explosion where
|	  your cursor is.
|	
|	+ The window starts up at 400x400 pixels but is best viewed at a larger resolution.
|	
+-----------------------------------------------------------------------------------------------------------------+




+-----------------------------------------------------------------------------------------------------------------+
| How this particle system works                                                                                  |
+-----------------------------------------------------------------------------------------------------------------+
|	
|	Pressing Spacebar:
|		1. When the spacebar is pressed, a sphere is spawned randomly at the bottom of the window.
|		   The sphere is spawned closer to the middle of the bottom so that more fireworks explode
|		   on the viewable portion of the screen.
|		
|		2. This particle (simulating a firework) keeps moving upwards and gradually slows down over
|		   time until its lifespan runs out.
|		
|		3. When the particles lifespan runs out, particle_explode() is called from the 
|		   particle_update() function and the firework generates a number of explosion particles
|		   which are small spheres, have a very short lifespan, a high speed, and fly in all
|		   directions.
|		
|	Pressing Left or Right Mouse Buttons:
|		1. When one of the mouse buttons is pressed, particle_explode_click() is called with the
|		   coordinates of the cursor passed to it and one of the macros XXXXXX_CLICK_PARTICLE_COUNT.
|		
|		2. particle_explode_click() does a similiar job as particle_explode(), except it generates
|		   the particles at the (x,y) coordinates passed to it instead of the coordinates of another
|		   firework, and it generates (int count) number of particles instead of creating the explosion
|		   based on the size of a firework.
|	
|	Both of these functions add these new explosion particles to the head of the list.
|	
+-----------------------------------------------------------------------------------------------------------------+




+-----------------------------------------------------------------------------------------------------------------+
| Hotkeys                                                                                                         |
+-----------------------------------------------------------------------------------------------------------------+
|	
|	Application Control:
|		q:              Quit the application.
|		Q:              Quit the application.
|		Middle Click:   Quit application.
|	
|	Particle Spawning
|		Space:          Spawn a firework
|		Left Click:     Explode a small cluster of particles where you click.
|		Right Click:    Explode a large cluster of particles where you click.
|	
|	Particle Deleting:
|		d:              Delete all particles.
|	
|	Lighting:
|		l:              Disable lighting.
|		L:              Enable lighting.
|	
|		s:              Disable material coloring.
|		S:              Enable material coloring.
|	
|		c:              Flat shader mode.
|		C:              Smooth shader mode.
|	
+-----------------------------------------------------------------------------------------------------------------+




+-----------------------------------------------------------------------------------------------------------------+
| Timing (Benchmarked on Ubuntu 14.04 32bit, running in VMware, with an i7 3770 CPU @ 1.7 Ghz):                   |
+-----------------------------------------------------------------------------------------------------------------+
|	
|	Each firework in my particle system can explode into hundreds of particles, because of this, performance 
|	takes a big hit when there are more than 50 or so fireworks exploding at once. Also, since the lifespan
|	of the firework depends on the window size, the smaller the window the better the performance because fireworks
|	spawn and explode quicker, thus there is less of a chance for many fireworks to explode at once.
|	
|	There is a macro called "PRINT_PARTICLE_UPDATE_RENDER_TIME", in the file "Kaganovsky_particles.h". If set to a
|	non zero value then the number of milliseconds that the update and rendering of particles takes will be printed.
|	
|	Basically, if the fireworks explode into an average cluster of 50 particles, then the value of
|	DFLT_INIT_NUM_PARTICLES (the initial number of fireworks) should be:
|	
|	10 for 500 Particles:     0.00005 milliseconds to update,
|	                          0.01 milliseconds to render with lighting on.
|	                          
|	40 for 2000  Particles:   0.0001 milliseconds to update,
|	                          0.03 milliseconds to render with lighting on.
|	                          
|	200 for 10000 Particles:  0.0005 milliseconds to update,
|	                          0.1 milliseconds to render with lighting on.
|	
+-----------------------------------------------------------------------------------------------------------------+
</pre>
