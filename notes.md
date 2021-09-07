### Modifications to make cuda executables

- nvcc --gpu-architecture=???
Use `nvcc -help` to find out available structures (e.g. sm-20 is not available on our gpu)

- fix Makefile
  - %.o : %.[ch] -> %.o : %.[c] for **kmeans** and **leukocyte**
  - make DIRT (bin/linux/cuda, omp, ocl). Otherwise, `make clean` will delete all things.

- fix executable
  - `include <unistd.h>` for **cuda,openomp/mummergpu/src/suffix-tree.cpp**

- Check **/usr/include/GL/** to see what packages are missing for openCL
  - In my case, I installed freeglut-devel (for **particlefilter**): 
  `wget https://centos.pkgs.org/7/centos-x86_64/freeglut-devel-3.0.0-8.el7.x86_64.rpm.html`
  `yum install freeglut-devel`
  - Also glew (for **mummergpu**):
  `yum install glew-devel`

I haven't fixed all opencl/openmp directories. Not neccessary at this moment.
