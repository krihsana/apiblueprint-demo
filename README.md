# apiblueprint-demo

## ปัญหาการใช้ aglio บน windows

จุดเริ่มต้นของบทความนี้เกิดจาก ผมไม่สามารถใช้งาน api blueprint ได้ เนื่องจากไม่สามารถติดตั้ง aglio ได้ จึงอยากจะทำ วิธีการเก็บไว้เพื่อเตื่อนตัวเองหากอยากจะใช้งาน จะต้องติดตั้งอย่างไร

ปล OS ที่เกิดปัญหาคือ windows

เริ่มต้น เราต้องติดตั้ง node ก่อน 
ต้อง version node-v8.17.0-win-x64

--ต่อมา

ติดตั้ง window-build-tools 
npm install --global --production windows-build-tools@4.0.0

และ set
npm config set msvs_version 2015 --global

ปัญหาเริ่่มต้นที่เจอ คือ หลังจาก run
npm install -g aglio --python=2.7 (ต้อง version 2.7 เพราะ build tools window เป็น version นี้)

ก็พบเจอสิ่งนี้   Microsoft.Cpp.Default.props was not found 
โดยจัดการกับปัญหานี้ โดยการ

** optional อาจจะไม่ต้อง set ก็ได้ แต่ทำเพื่อไว้ **
Set Environment Variable 
VCTargetsPath = C:\Program Files (x86)\Microsoft Visual Studio\2017\BuildTools\Common7\IDE\VC\VCTargets\
*******************************************

--ต่อมา เจอปัญหา
MSbuild Error: The builds tools for v140 (Platform Toolset = 'v140') cannot be found

จัดการโดยการ 
ติดตั้ง VC++ 2015.3 v140 toolset (x86,x64) ผ่านทาง (visual studio install หรือ ทางอื่นก็ได้)

--ต่อมา เจอปัญหา
Windows SDK version 8.1 was not found?

จัดการโดย
ติดตั้ง Windows 8.1 SDK และ (ควรติดตั้ง Windows 10 SDK C++ ให้ครบด้วย เพื่อไว้ อาจต้องใช้)

--ต่อมา เจอปัญหา
Cannot find corecrt.h

จัดการโดย
ติดตั้ง Windows Universal CRT SDK

--ต่อมา เจอปัญหา
'Handle': is not a member of 'v8'

จัดการโดย





