# TG-Plus for JP_109a<BR>
![](logo90.png) <BR>
This is a tutorial to install and use the enhanced MOD for javplayer_109a,enhance the effect after removing mosaic.<BR>
This MOD was created by the Discord community kmkii#8701.<BR>
Just for learning and communication purposes only,Do not use it for any commercial purposes.<BR>
If you can run the original javplayer, the mod should be easy to run as well.<BR>


## Featrue:<BR>
1.Add TopazVideoEnhanceAI enhancement function.<BR>
2.Support TecoGAN 2X 8X models and Secondary-enhancement model SE-2X,SE-4X (insufficient training).<BR>
3.Support Denosie Anti-flicker, but time-consuming and will reduce sharpness.<BR>
4.Support patch_tools for remove the original watermark.<BR>
5.Support safe mode picture quality enhancement.<BR>
6.Support esrgan model.<BR>
7.Support mPlus custom command mode.<BR>
8.Support 3000 series card (Requires cuda11, cudnn8.0.5 environment)<BR>
9.python script extensions are supported<BR>

## Note:<BR>
  This Mod base on TG-models, No matter SE-mode or TVE-mode, improved few. <BR>
  Basically, the good will be better, the bad will be worse.<BR>

## Config file: 
mod.ini    #TG-PLUS mplus command line config file.<BR>
veai.ini    #veai custom dictionary file.<BR>
(located in javplayer_109a/TG directory)

## Usage:
  Function:scale:model-name.<BR>
## Function:
  a. tecogan esrgan tve. e.g., m1:tecogan:4:TG-AF1 , m2:esrgan:2:esrgan-2x_SHARP . <BR>
  (The scale should be consistent with the model e.g., tecogan:2:SE-2X,TVE model can set to 2,3,4,6 e.g., tve:6:ahq)<BR>
  b. denoise, no parameters.  e.g., m2:denoise .   <BR>
  (Processing image noise, occupy cpu memory) <BR>
  c. downscale. e.g.,downscale:3.5 .<BR>
  (you can choose to reduce the ratio, speedup and Avoid OOM.)<BR>
  d.res. e.g., res:1280 .<BR>
  (images will be reduced first, Limit maximum output to 1280.)<BR>

## Others:<BR>
  1.use v1.9 parameters, to adapt the version of tve.<BR>
  Default support for v1.5 1.7 1.8 1.9 veai cmd, use e.g. v1.9 in mod.ini to specify the tve version.<BR>
  And generate veai.ini file in tg/ directory when tve is first called. for future updates of tve version, <BR>
  use custom dictionary e.g. "ahq": "ahq-11"...,and delete v1.9 flag or modify it to v2.x.<BR>
  ! tve 1.7 1.8 does not support tiny images well and cannot be used for first step.(dont use for m1).<BR>
  ! tve 1.7 has many issues, not recommended.<BR>
  2. esrgan model<BR>
  ! Use esrgan-ncnn-vulkan.exe to execute the standard model, You can use pth2ncnn.exe xxx.pth to convert the model.<BR>
  put into TGMAIN\mplus\esrgan\models\ .<BR>
  Note: If you are interested ,you can training standard model or secondary enhancement model.<BR>
  3. mPlus custom command mode.<BR>
  You can use mplus mode to custom execution.<BR>
  ! can be customized to order and model.<BR>
  ! model-name must be case sensitive.<BR>
  #### Example of mod.ini<BR>
  ! #The first line TG-PLUS is the enhanced mode flag, modify it to TG to turn off and ignore all command lines.<BR>
```
  TG-PLUS
  # This is a standard profile
  # Note the TG-PLUS line cannot be removed.
  M1:tecogan:4:TG-STD         # Use tecogan TG-STD model
  M2:denoise                  # denoise
  M3:tecogan:4:SE-4X          # Use SE-4X model for SE-enhance.  
  M4:denoise                  # denoise  
  M5:tve:4:ahq                # tve enhanced, 4x, use ahq model.

  res:1920                    # Limit max resolution to 1920.  
  v1.9                        # Use the command line of tve 1.9
```
```
  TG-PLUS
  # This is an example of functional demo that just show the custom command line usage.
  # Note the TG-PLUS line cannot be removed.
  m1:esrgan:2:esrgan-2x_SHARP   # esrgan-2x_SHARP is a pth2ncnn.exe conversion model, model name case consistency.
  m2:denoise                    # denoise
  m3:tecogan::TG-AF1            # scale_factor is empty, :: scale is null use default 4, and TG-AF1 is used in se-mode.
  m4:denoise
  m5:denoise                    # m4,m5 If the noise is too serious, you can reduce the noise several times like this.
  m6:esrgan:2:                  # esrgan model name is empty, model name is null,so 2x model will be used
  m7:downscale:1.5              # Reduce the images in the input directory by 1.5 times.
  m8:tve:2:thd                  # tve enhanced, 2x,use thd model, and affected by res:960 will downscale first
  res:960                       # Limit max output resolution to 960.
  v1.9                          # Use the command line of tve 1.9
```
  4. python script extensions are supported, will be useful. Extend your own functionality and implement your own ideas.<BR>
    You can call python script. e.g., m1:mPlus\call-realsr.py. (checkin TGMAIN\mplus)  . <BR>
    the pass the arguments: -i inputdir -o ouputdir -m model -s sacle -se_mode se_mode<BR>

## Packs: (unrar password: km)<BR>
1.TG-Plus for 3000 series.<BR>
https://thuploader.orz.hm/uploader/?mode=dl&id=24596&original=1<BR>
https://thuploader.orz.hm/uploader/?mode=dl&id=24597&original=1<BR>
2.runGan_veai_custom_patch<BR>
https://thuploader.orz.hm/uploader/?mode=dl&id=24710&original=1<BR>
Overwrite the source files in the tgmain directory, backup first.<BR>
3.download TG-MODEL<BR>
https://thup.work/uploader/?mode=dl&id=25181&original=1<BR>
4.Video Quality patch for 1.08 safe mode.<BR>
https://thup.work/uploader/?mode=dl&id=25758&original=1<BR>
5.Javplayer_watermark_patch 102 - 109a<BR>
https://thuploader.orz.hm/uploader/?mode=dl&id=22129<BR>

## Installation Instructions: <BR>
1.install Topaz Video Enhance AI,copy "X:\Program Files\Topaz Labs LLC\Topaz Video Enhance AI" <BR>
  to Javplyer_109a main folder. rename the folder to TVE.<BR>
2.backup you TG folder,rename it to TG.BAK .<BR>
3.download TG-Plus_3000.rar(2 packs) , unzip the file to javplayer_109a TG folder.<BR>
4.copy the backup TG-AF1 TG-AF2 . to TG/TG-MODEL .<BR>
5.download TG-MODEL.rar(SE-2X,SE-4X..), unzip the file to TG/TG-MODEL.<BR>
6.download Javplayer_watermark_patch,copy xxx\level0 to JavPlayer_Data.<BR>
7.download runGan_veai_custom_patch,Overwrite the source files in the tgmain directory, backup first.<BR>
8.put mod.ini into  javplayer_109a TG folder.<BR>

![](directory.png)

#### I state this mod is completely free , do not use it for any commercial purposes, pretend to be an author for sale more shameful.<BR>
![visitor badge](https://visitor-badge.glitch.me/badge?page_id=github.com/km2ii/JP109A_TG-PLUS)
