---
title: 'Porady: osadzanie manifestu w aplikacji C/C++ | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- manifests [C++]
- embedding manifests
- makefiles, updating to embed manifest
ms.assetid: ec0bac69-2fdc-466c-ab0d-710a22974e5d
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3bc7646dab51b9a1fdd73b23d1f58c7b474c363e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-embed-a-manifest-inside-a-cc-application"></a>Porady: osadzanie manifestu w aplikacji C/C++
Jest zalecane aplikacji C/C++ (lub biblioteka) swoim manifeście osadzony w ostatnim pliku binarnego, ponieważ gwarantuje to poprawne zachowanie w większości przypadków. Domyślnie [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] próbuje osadzania manifestu podczas tworzenia projektu przy użyciu plików źródłowych; zobacz [Generowanie manifestu w Visual Studio](../build/manifest-generation-in-visual-studio.md) Aby uzyskać więcej informacji. Jednak jeśli aplikacja jest zbudowany przy użyciu nmake, konieczne są pewne zmiany do istniejącego pliku reguł programu make. W tej sekcji przedstawiono, jak zmienić istniejące pliki reguł programu make automatycznie osadzanie manifestu w ostatnim pliku binarnego.  
  
## <a name="two-approaches"></a>Dwa podejścia  
 Istnieją dwa sposoby do osadzania manifestu w aplikacji lub biblioteki.  
  
-   Jeśli nie przeprowadzasz wzrostowe można bezpośrednio Osadź manifest przy użyciu wiersza polecenia podobny do następującego krokiem po kompilacji:  
  
     **MT.exe-manifest MyApp.exe.manifest-outputresource:MyApp.exe;1**  
  
     lub  
  
     **MT.exe-manifest MyLibrary.dll.manifest-outputresource:MyLibrary.dll;2**  
  
     (1 w przypadku pliku EXE, 2 dla biblioteki DLL).  
  
-   Jeśli przeprowadzasz wzrostowe bezpośrednio edytować zasobów, jak pokazano poniżej spowoduje wyłączenie kompilowanie przyrostowej i spowodować ponownej pełnej kompilacji; Dlatego należy podjąć różne podejścia:  
  
    -   Połącz plik binarny, aby wygenerować plik MyApp.exe.manifest.  
  
    -   Konwertuj manifestu do pliku zasobów.  
  
    -   Ponowne łączenie (przyrostowo) do osadzania zasobu manifestu w danych binarnych.  
  
 Poniższe przykłady pokazują, jak zmienić pliki reguł programu make w celu uwzględnienia obie techniki.  
  
## <a name="makefiles-before"></a>Pliki reguł programu make (przed)  
 Należy wziąć pod uwagę skryptu nmake MyApp.exe, prostą aplikację skompilowane z jednego pliku:  
  
```  
# build MyApp.exe  
!if "$(DEBUG)" == "1"  
CPPFLAGS=$(CPPFLAGS) /MDd  
LFLAGS=$(LFLAGS) /INCREMENTAL  
!else  
CPPFLAGS=$(CPPFLAGS) /MD  
!endif  
  
MyApp.exe : MyApp.obj  
    link $** /out:$@ $(LFLAGS)  
  
MyApp.obj : MyApp.cpp  
  
clean :   
    del MyApp.obj MyApp.exe  
```  
  
 Jeśli ten skrypt jest uruchamiany bez zmian z programem Visual C++, tworzy pomyślnie MyApp.exe. Tworzy również zewnętrznego pliku manifestu MyApp.exe.manifest, do użycia przez system operacyjny, aby załadować zestawów zależnych w czasie wykonywania.  
  
 Skrypt nmake MyLibrary.dll wygląda bardzo podobnie:  
  
```  
# build MyLibrary.dll  
!if "$(DEBUG)" == "1"  
CPPFLAGS=$(CPPFLAGS) /MDd  
LFLAGS=$(LFLAGS) /DLL /INCREMENTAL  
  
!else  
CPPFLAGS=$(CPPFLAGS) /MD  
LFLAGS=$(LFLAGS) /DLL  
  
!endif  
  
MyLibrary.dll : MyLibrary.obj  
    link $** /out:$@ $(LFLAGS)  
  
MyLibrary.obj : MyLibrary.cpp  
  
clean :   
    del MyLibrary.obj MyLibrary.dll  
```  
  
## <a name="makefiles-after"></a>Pliki reguł programu make (po)  
 Kompilować z osadzonych manifestach, konieczne będzie wprowadzenie czterech drobnych zmian do oryginalnego pliki reguł programu make. Dla pliku reguł programu make MyApp.exe:  
  
```  
# build MyApp.exe  
!include makefile.inc  
#^^^^^^^^^^^^^^^^^^^^ Change #1. (Add full path if necessary.)  
  
!if "$(DEBUG)" == "1"  
CPPFLAGS=$(CPPFLAGS) /MDd  
LFLAGS=$(LFLAGS) /INCREMENTAL  
!else  
CPPFLAGS=$(CPPFLAGS) /MD  
!endif  
  
MyApp.exe : MyApp.obj  
    link $** /out:$@ $(LFLAGS)  
    $(_VC_MANIFEST_EMBED_EXE)  
#^^^^^^^^^^^^^^^^^^^^^^^^^^^^ Change #2  
  
MyApp.obj : MyApp.cpp  
  
clean :   
    del MyApp.obj MyApp.exe  
    $(_VC_MANIFEST_CLEAN)  
#^^^^^^^^^^^^^^^^^^^^^^^^ Change #3  
  
!include makefile.targ.inc  
#^^^^^^^^^^^^^^^^^^^^^^^^^ Change #4. (Add full path if necessary.)  
```  
  
 Dla pliku reguł programu make MyLibrary.dll:  
  
```  
# build MyLibrary.dll  
!include makefile.inc  
#^^^^^^^^^^^^^^^^^^^^ Change #1. (Add full path if necessary.)  
  
!if "$(DEBUG)" == "1"  
CPPFLAGS=$(CPPFLAGS) /MDd  
LFLAGS=$(LFLAGS) /DLL /INCREMENTAL  
  
!else  
CPPFLAGS=$(CPPFLAGS) /MD  
LFLAGS=$(LFLAGS) /DLL  
  
!endif  
  
MyLibrary.dll : MyLibrary.obj  
    link $** /out:$@ $(LFLAGS)  
    $(_VC_MANIFEST_EMBED_DLL)  
#^^^^^^^^^^^^^^^^^^^^^^^^^^^^ Change #2.  
  
MyLibrary.obj : MyLibrary.cpp  
  
clean :   
    del MyLibrary.obj MyLibrary.dll  
    $(_VC_MANIFEST_CLEAN)  
#^^^^^^^^^^^^^^^^^^^^^^^^ Change #3.  
  
!include makefile.targ.inc  
#^^^^^^^^^^^^^^^^^^^^^^^^^ Change #4. (Add full path if necessary.)  
```  
  
 Pliki reguł programu make zawierają teraz dwa pliki, które wykonują rzeczywistą pracę, makefile.inc i makefile.targ.inc.  
  
 Utwórz makefile.inc i skopiuj do niego następujące:  
  
```  
# makefile.inc -- Include this file into existing makefile at the very top.  
  
# _VC_MANIFEST_INC specifies whether build is incremental (1 - incremental).  
# _VC_MANIFEST_BASENAME specifies name of a temporary resource file.  
  
!if "$(DEBUG)" == "1"  
CPPFLAGS=$(CPPFLAGS) /MDd  
LFLAGS=$(LFLAGS) /INCREMENTAL  
_VC_MANIFEST_INC=1  
_VC_MANIFEST_BASENAME=__VC90.Debug  
  
!else  
CPPFLAGS=$(CPPFLAGS) /MD  
_VC_MANIFEST_INC=0  
_VC_MANIFEST_BASENAME=__VC90  
  
!endif  
  
####################################################  
# Specifying name of temporary resource file used only in incremental builds:  
  
!if "$(_VC_MANIFEST_INC)" == "1"  
_VC_MANIFEST_AUTO_RES=$(_VC_MANIFEST_BASENAME).auto.res  
!else  
_VC_MANIFEST_AUTO_RES=  
!endif  
  
####################################################  
# _VC_MANIFEST_EMBED_EXE - command to embed manifest in EXE:  
  
!if "$(_VC_MANIFEST_INC)" == "1"  
  
#MT_SPECIAL_RETURN=1090650113  
#MT_SPECIAL_SWITCH=-notify_resource_update  
MT_SPECIAL_RETURN=0  
MT_SPECIAL_SWITCH=  
_VC_MANIFEST_EMBED_EXE= \  
if exist $@.manifest mt.exe -manifest $@.manifest -out:$(_VC_MANIFEST_BASENAME).auto.manifest $(MT_SPECIAL_SWITCH) & \  
if "%ERRORLEVEL%" == "$(MT_SPECIAL_RETURN)" \  
rc /r $(_VC_MANIFEST_BASENAME).auto.rc & \  
link $** /out:$@ $(LFLAGS)  
  
!else  
  
_VC_MANIFEST_EMBED_EXE= \  
if exist $@.manifest mt.exe -manifest $@.manifest -outputresource:$@;1  
  
!endif  
  
####################################################  
# _VC_MANIFEST_CLEAN - command to clean resources files generated temporarily:  
  
!if "$(_VC_MANIFEST_INC)" == "1"  
  
_VC_MANIFEST_CLEAN=-del $(_VC_MANIFEST_BASENAME).auto.res \  
    $(_VC_MANIFEST_BASENAME).auto.rc \  
    $(_VC_MANIFEST_BASENAME).auto.manifest  
  
!else  
  
_VC_MANIFEST_CLEAN=  
  
!endif  
  
# End of makefile.inc   
####################################################  
```  
  
 Teraz Utwórz makefile.targ.inc i skopiuj do niego następujące:  
  
```  
# makefile.targ.inc - include this at the very bottom of the existing makefile  
  
####################################################  
# Commands to generate initial empty manifest file and the RC file  
# that references it, and for generating the .res file:  
  
$(_VC_MANIFEST_BASENAME).auto.res : $(_VC_MANIFEST_BASENAME).auto.rc  
  
$(_VC_MANIFEST_BASENAME).auto.rc : $(_VC_MANIFEST_BASENAME).auto.manifest  
    type <<$@  
#include <winuser.h>  
1RT_MANIFEST"$(_VC_MANIFEST_BASENAME).auto.manifest"  
<< KEEP  
  
$(_VC_MANIFEST_BASENAME).auto.manifest :  
    type <<$@  
<?xml version='1.0' encoding='UTF-8' standalone='yes'?>  
<assembly xmlns='urn:schemas-microsoft-com:asm.v1' manifestVersion='1.0'>  
</assembly>  
<< KEEP  
  
# end of makefile.targ.inc  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Opis Generowanie manifestu dla programów C/C++](../build/understanding-manifest-generation-for-c-cpp-programs.md)