orion-mod
=========

Personal test field on tweaking Orion Viewer (mainly for Nook Simple Touch)

This project is a tweak on the Orion Viewer by  Michael Bogdanov:

http://code.google.com/p/orion-viewer/

Currently it is based on Orion-viewer 0.38.5

Current tweaks
--------------

* Pdf reflow using k2pdfopt at:

  http://www.willus.com/k2pdfopt/

  and its mod from kindlepdfviewer at:

  https://github.com/hwhw/kindlepdfviewer

* Minor fixes in key binding activity and light themes on Nook Simple Touch

* Adapt k2pdfopt to orion-viewer's cropping capability, now able to crop pages before
  reflow, thanks to libk2pdfopt, a refinement to the original k2pdfopt:

  https://github.com/chrox/libk2pdfopt

* Able to select words(using OCR). With k2pdfopt's builtin support for tesseract:

  https://code.google.com/p/tesseract-ocr/


Notes
-------------
* Make sure the page settings(zoom etc) are reset to default and the screen is
  in portrait mode before you start the reflow. Possibly landscape mode will be support
  in the future.

* The reflow will destory part of orion-viewer's  functionality:
  - FIXED:
    Text selection: Orion Viewer will auto-matically draw the next page when the last
    patch of bitmap is reached and thus, it will override the current bitmap and the last
    part cannot make words selection. This is rather strange behavior as k2pdfopt uses
    one single "Masterinfo" to collect the data, which should be modified in the future.

    This issue is fixed by adding a native LRU cache based on pages intead of bitmaps. It
    seems to work



Build and Usage
------------
* User can download prebuilt version from release directory. In order to use OCR for
  words selection in reflow mode, please download the tesseract-eng-chn.tar.gz, unpack it
  and copy the tesseract directory to /sdcard/data/

* Build the mupdf library
  cd mupdf-1.1-source/android
  ndk-build

* copy libmupdf.so lto orion-viewer/orion_viewer/libs/armeabi/

* In orion-viewer/orion_viewer, configure your sdk_dir and run ant debug

Screenshots
-----------
## Reflow: ##
### Chinese reflow over scanned PDF ###

  ![Before Reflow](https://github.com/kkspeed/orion-mod/raw/master/img/chn_1.png) \
  ![After Reflow](https://github.com/kkspeed/orion-mod/raw/master/img/chn_2.png)

### English reflow over text PDF ###

  ![Before Reflow](https://github.com/kkspeed/orion-mod/raw/master/img/eng_1.png)

  ![After Reflow](https://github.com/kkspeed/orion-mod/raw/master/img/eng_2.png)

### OCR Words Extraction ###
  ![Scanned PDF](https://github.com/kkspeed/orion-mod/raw/master/img/ocr-1.png)

  ![Scanned PDF OCR Words](https://github.com/kkspeed/orion-mod/raw/master/img/ocr-2.png)
