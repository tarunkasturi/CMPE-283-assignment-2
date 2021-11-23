# CMPE-283-assignment-2

Team Members:
Harshit bhoraskar (015218606) 
Tarun Pradeep Kasturi (015349685)

Contribution:


 Harshit bhoraskar:
 Build the Kernal.
 Gone thoroughly about the atomic varialbles and CPUID insruction.
 Made changes and modified the code in the vmx_handler_exit in the vmx.c file and cpuid.c file.
 We created a test file and compiled it. in the nested VM.
 
 Tarun Pradeep Kasturi:
 Build the kernal.
 Understood the requirments of the leaf function.
 We created a CPUID leaf function in kvm_emulate_cpuid when %eax=0*4ffffffff function inthe cpuid.c.
 
 Process for the environment setup:
 1.Forked and cloned the linux repository with the following command
 $git clone https://github.com/torvalds/linux.git
 
 2. Now we have to enter the sudo mode
 $ sudo bash
 
 3.Install all the packages required to complie the files using followig command:
 sudo apt install qemu-kvm libvirt-daemon-system libvirt-clients bridge-utils
  sudo systemctl status libvirtd
  sudo systemctl enable --now libvirtd
  
 4.Setup the confg file
 $ make menuconfig
 
 
 5. Select the vm support option from the prompt and increase the number of processors


 6. Compile and build the kernal
 $ make -j8 &&  make modules -j8 && make install -j8 && make modules_install -j8
 
 7. Reboot the system
 8. $ reboot


Modification in the kernal code:
1. vmx_handle_exit caluclates the total numberof exits using inc function and total time using rdtsc function
2. In cpuid.c file create a new leaf in kvm_emulate_cpuid which reads no of exits int %eax
3. kvm_emulate_cpuid excutes the default code.
4. Complie the code using the following  function 
    $ sudo  make -j modules =arch/x86/kvm
6. To execute the load and unload of the kvm kernal modules and kvm intel modules
   $ sudo rmmod arch/x86/kvm/kvm-intel.ko
   $ sudo rmmod arch/x86/kvm/kvm.ko
   $ sudo insmod arch/x86/kvm/kvm.ko
   $ sudo insmod arch/x86/kvm/kvm-intel.ko
   
   
Building the Nested VM:
1. Install virt manager
$ sudo apt-get install virt-manager
$ sudo apt-get install libvirt-bin libvirt-doc
S sudo apt-get install qemu-system
S sudo virt-manage

2.Download the ubuntu iso image.

3.Finish all the installation steps.

4. Build the test code inside the inner VM to know the changes made in the outer VM.


