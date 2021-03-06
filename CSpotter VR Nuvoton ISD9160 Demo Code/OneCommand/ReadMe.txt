/*---------------------------------------------------------------------------------------------------------*/
/*                                                                                                         */
/* Copyright(c) Nuvoton Technology Corp. All rights reserved.                                              */
/*                                                                                                         */
/*---------------------------------------------------------------------------------------------------------*/
---------------------------------------------------------------------------------------------------------
Purpose:
---------------------------------------------------------------------------------------------------------
	1. 	Recognize one command and play response with different group commands .


---------------------------------------------------------------------------------------------------------
Operation:
---------------------------------------------------------------------------------------------------------
	



---------------------------------------------------------------------------------------------------------
Note:
---------------------------------------------------------------------------------------------------------
	1. 	Before recognizing, there must be written the "OneCommandAllMerged.bin" file into SPI flash.
	   	This file contain VR model and audio response bin files.
	2.	User must enable date flash area of chip and estimate size. This area saves VR model loaded
		from SPIFLah.
	3. 	The encoded data can be generated by "WindowsPlatform\Tool\AudioTool\AudioTool.exe".
	   	There is an audio tool project "AudioRes.wba" located in ".\AudioRes".
	   	The "AudioRes_AudioInfoMerge.ROM" file is created by this project.
	4. 	The playback sampling rate is read from audio file or equation
	5. 	Playback can be with/without N-times up-sampling to reduce "metal sound"
	   	which is controlled by "APU_UPSAMPLE" defined in "ConfigApp.h"


---------------------------------------------------------------------------------------------------------
Must Know:
---------------------------------------------------------------------------------------------------------
	1.	The stack size is defined by "Stack_Size" in "startup_N575_Keil.s". Can change the stack size
		by modifing the content of "Stack_Size".
	2.	The chip ROM size and SRAM size is specified by "ROM_SIZE" and "SRAM_SIZE"in  linker settings
		Open the linker setting and find the --pd="-DSRAM_SIZE=0xNNNN" --pd="-DROM_SIZE=0xMMMMM" in "misc controls" 
	3.	When the error happen:
			"L6388E: ScatterAssert expression (ImageLimit(_SRAM) < (0xNNNNNNNN + 0xMMMM)) failed on line xx" 
		It means the size of variables+stack is over chip SRAM size.
		Please open map file to see the overed SRAM size and reduce variables or stack size to fit chip SRAM size.
	4.	When the error happen:
			"L6220E: Load region _ROM size (NNNNN bytes) exceeds limit (MMM bytes)."
		It means the size of programs is over chip ROM size.
		Please open map file to see the overed programs size and reduce programs size to fit chip ROM size.
