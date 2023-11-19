#### 🐈 ♡.°୭̥ ୨୧ ♡⃛⋆⁺॰｡ཻ˚♡ ˗ˋˏ❤︎ˎˊ˗  -ˋˏ ♡ ˎˊ-  ♡✧。♡*.˖◛⁺⑅♡♡ ⋆⁺₊⋆ ☾⋆⁺

[![Velog's GitHub stats](https://velog-readme-stats.vercel.app/api?name=haansohee)](https://velog.io/@haansohee)

#### 🐈‍⬛ ♡ ₊⋆ ☾⋆⁺₊⋆ ♡̷̷̷ ⋆⁺₊⋆ ☾⋆⁺₊⋆ฅʕ•ﻌ•ʔฅ ੈ✩‧₊˚ * ੈ♡‧☾⋆⁺₊⋆ ♡̷̷̷₊⋆ ♡‧₊˚*

<br>
<br>


 sudo apt install build-essential cmake libavcodec-dev libavformat-dev libswscale-dev libxvidcore-dev libx264-dev libxine2-dev libv4l-dev v4l-utils  libgstreamer1.0-dev libgstreamer-plugins-base1.0-dev gstreamer1.0-plugins-good gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly install libgtk-3-dev  libatlas-base-dev gfortran libeigen3-dev python3-dev python3-numpy

4-1. 소스 코드를 저장할 임시 디렉토리를 생성하여 이동 후.. 진행합니다

pi@raspberrypi:~ $ mkdir opencv

pi@raspberrypi:~ $ cd opencv

pi@raspberrypi:~/opencv $

4-2. OpenCV 4.8.1 소스코드를 다운로드 받아 압축을 풀어줍니다. 

$ wget -O opencv.zip https://github.com/opencv/opencv/archive/4.8.1.zip

$ unzip opencv.zip

4-3. opencv_contrib(extra modules) 소스코드를 다운로드 받아 압축을 풀어줍니다.

SURF 등을 사용하기 위해 필요합니다. 

$ wget -O opencv_contrib.zip https://github.com/opencv/opencv_contrib/archive/4.8.1.zip

$ unzip opencv_contrib.zip



4-4. 다음처럼 두 개의 디렉토리가 생성됩니다. 

pi@raspberrypi:~/opencv $  ls -d */

opencv-4.8.1  opencv_contrib-4.8.1

 

opencv-4.8.1 디렉토리로 이동하여 build 디렉토리를 생성하고 build 디렉토리로 이동합니다.

컴파일은 build 디렉토리에서 이루어집니다.

pi@raspberrypi:~/opencv $  cd opencv-4.8.1

pi@raspberrypi:~/opencv/opencv-4.8.1 $  mkdir build

pi@raspberrypi:~/opencv/opencv-4.8.1 $  cd build

pi@raspberrypi:~/opencv/opencv-4.8.1/build $  

 

4-5. Python이 라이브러리를 인식하는 위치를 확인합니다. 여기에선 보라색으로 표시한 경로입니다. 

$ python3 -m site

sys.path = [

    '/home/pi/opencv/opencv-4.8.1/build',

    '/usr/lib/python311.zip',

    '/usr/lib/python3.11',

    '/usr/lib/python3.11/lib-dynload',

    '/usr/lib/python3/dist-packages',

    '/usr/lib/python3.11/dist-packages',

]

USER_BASE: '/home/pi/.local' (exists)

USER_SITE: '/home/pi/.local/lib/python3.11/site-packages' (doesn't exist)

ENABLE_USER_SITE: True




4-6. cmake를 사용하여 OpenCV 컴파일 설정을 해줍니다.  복사해서 터미널에 붙여넣기 해주면 됩니다. 

 

다음 옵션은 빌드할 OpenCV 버전에 맞추어 아래 경로중 빨간색 부분을 변경하세요. 

-D OPENCV_EXTRA_MODULES_PATH=../../opencv_contrib-4.8.1/modules 

 

보라색으로 표시한 부분은 Python의 라이브러리 찾는 경로로 4-5번에서 확인한 경로로 변경해야 합니다. 

 

cmake -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=/usr/local -D WITH_TBB=OFF -DWITH_LIBV4L=ON -D WITH_IPP=OFF -D WITH_1394=OFF -D BUILD_WITH_DEBUG_INFO=OFF -D BUILD_DOCS=OFF -D INSTALL_C_EXAMPLES=ON -D INSTALL_PYTHON_EXAMPLES=ON -D BUILD_EXAMPLES=OFF -D BUILD_TESTS=OFF -D BUILD_PERF_TESTS=OFF -D ENABLE_NEON=ON -D WITH_QT=OFF -D WITH_GTK=ON -D WITH_OPENGL=ON -D OPENCV_ENABLE_NONFREE=ON -D OPENCV_EXTRA_MODULES_PATH=../../opencv_contrib-4.8.1/modules -D WITH_V4L=ON -D WITH_FFMPEG=ON -D WITH_XINE=ON -D ENABLE_PRECOMPILED_HEADERS=OFF -D BUILD_NEW_PYTHON_SUPPORT=ON -D OPENCV_GENERATE_PKGCONFIG=ON -D PYTHON3_PACKAGES_PATH=/usr/lib/python3.11/dist-packages ../

 

4-7. 다음처럼 cmake 실행 중에  추가적인 다운로드가  있습니다.  

라즈베리파이에 인터넷이 연결된 상태에서 진행하세요..

-- xfeatures2d/boostdesc: Download: boostdesc_bgm.i

-- xfeatures2d/boostdesc: Download: boostdesc_bgm_bi.i

-- xfeatures2d/boostdesc: Download: boostdesc_bgm_hd.i

-- xfeatures2d/boostdesc: Download: boostdesc_binboost_064.i

-- xfeatures2d/boostdesc: Download: boostdesc_binboost_128.i

-- xfeatures2d/boostdesc: Download: boostdesc_binboost_256.i

-- xfeatures2d/boostdesc: Download: boostdesc_lbgm.i

-- xfeatures2d/vgg: Download: vgg_generated_48.i

-- xfeatures2d/vgg: Download: vgg_generated_64.i

-- xfeatures2d/vgg: Download: vgg_generated_80.i

-- xfeatures2d/vgg: Download: vgg_generated_120.i

-- data: Download: face_landmark_model.dat

 

4-8. 다음과 같은 메시지가 보이면 정상적으로 된 것입니다.

-- Configuring done

-- Generating done

-- Build files have been written to: /home/pi/opencv/opencv-4.8.1/build

<!-- [![Anurag's GitHub stats](https://github-readme-stats.vercel.app/api?username=haansohee)](https://github.com/haansohee/github-readme-stats)  -->

<!-- ### Hi there 👋 -->

<!--
**haansohee/haansohee** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->
