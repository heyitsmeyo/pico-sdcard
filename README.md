# This is a pico sdk project to create a txt file on a sd card using a sd card module 

![20241215_133826](https://github.com/user-attachments/assets/d01231cd-3e6f-4d06-9664-5b6aeea214a9)

Schematic : 

![image](https://github.com/user-attachments/assets/8aae93e6-ff1f-4803-bc42-c5c46121709a)

We used the spi1 

Miso = 12
Mosi = 11 
SCK = 10 
CS = 13 


First of all , create a folder for the project 

Navigate to that folder and import the fatfs library by cloning the project : 

    https://github.com/carlk3/no-OS-FatFS-SD-SPI-RPi-Pico

Add the "hw_config.c" file with the main.c file  

Add a folder name "build" 

Navigate to that folder and export pico sdk path : 

    export PICO_SDK_PATH=/picosdkpath

then : 

    Cmake ..

then : 

    Make 

# debug : 

For debugging , use Putty , serial communiction with a baud rate of 115200 


# Key change : 

we had an error when compiling the project : undefined reference to spi_irq_handler .... 

To solve this , we made a slight change in the hw_config.c : 

void spi0_dma_isr() { spi_irq_handler(&spis[0]); } changed to : void spi0_dma_isr() { irq_handler_t(spis[0]); }


# if you like the project , you can donate us for more : 

    https://ko-fi.com/heyitsmeyo










