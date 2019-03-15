---
title: 'Instrukcje: Osadzanie manifestu w aplikacji C/C++'
ms.date: 11/04/2016
helpviewer_keywords:
- manifests [C++]
- embedding manifests
- makefiles, updating to embed manifest
ms.assetid: ec0bac69-2fdc-466c-ab0d-710a22974e5d
ms.openlocfilehash: 332d6d75080be3fdde6b8238ab79b8e5b1d1121e
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57809785"
---
# <a name="how-to-embed-a-manifest-inside-a-cc-application"></a>Instrukcje: Osadzanie manifestu w aplikacji C/C++

Zaleca się, że aplikacji C/C++ (lub biblioteki) ma osadzony w końcowym pliku binarnym, ponieważ gwarantuje to poprawne zachowanie w większości przypadków manifest. Domyślnie program Visual Studio podejmie do osadzania manifestu, podczas tworzenia projektu z plików źródłowych. zobacz [Manifest Generation w programie Visual Studio](manifest-generation-in-visual-studio.md) Aby uzyskać więcej informacji. Jednak jeśli wniosek został utworzony przy użyciu nmake, konieczne są pewne zmiany do istniejącego pliku reguł programu make. W tej sekcji pokazano, jak zmienić istniejące pliki reguł programu make automatycznie osadzanie manifestu w końcowym pliku binarnym.

## <a name="two-approaches"></a>Dwie metody

Istnieją dwa sposoby do osadzania manifestu w aplikacji lub biblioteki.

- Jeśli nie wykonujesz kompilacji przyrostowej można osadzić bezpośrednio manifest jako krok po kompilacji przy użyciu wiersza polecenia podobnego do następującego:

   **MT.exe-manifest MyApp.exe.manifest-outputresource:MyApp.exe;1**

   lub

   **mt.exe -manifest MyLibrary.dll.manifest -outputresource:MyLibrary.dll;2**

   (1 dla pliku EXE, 2 dla biblioteki DLL).

- Jeśli przeprowadzasz kompilacji przyrostowej bezpośrednią edycję zasobu, jak pokazano poniżej spowoduje wyłączyć przyrostowe kompilowanie i spowodować ponownej pełnej kompilacji; w związku z tym należy podjąć inne podejście:

   - Połącz dane binarne, aby wygenerować plik MyApp.exe.manifest.

   - Konwertuj manifest do pliku zasobów.

   - Ponowne łączenie (przyrostowo) do osadzania manifestu zasobu w pliku binarnego.

Poniższe przykłady pokazują jak zmienić pliki reguł programu make, aby włączyć obu tych technik.

## <a name="makefiles-before"></a>Pliki reguł programu make (przed)

Należy wziąć pod uwagę skryptu nmake MyApp.exe, prostej aplikacji, skompilowane z jednego pliku:

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

Jeżeli ten skrypt jest uruchamiany bez zmian w języku Visual C++, pomyślnie tworzy MyApp.exe. Tworzy również zewnętrznego pliku manifestu MyApp.exe.manifest, do użytku przez system operacyjny, który można załadować zestawów zależnych w czasie wykonywania.

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

Tworzenie z usługą osadzony manifestów, które należy podjąć cztery niewielkie zmiany na oryginalne pliki reguł programu make. Aby uzyskać MyApp.exe pliku reguł programu make:

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

Aby uzyskać MyLibrary.dll pliku reguł programu make:

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

Pliki reguł programu make obejmują teraz dwa pliki, które wykonują rzeczywistą pracę i makefile.inc makefile.targ.inc.

Utwórz makefile.inc i skopiuj następujące tę sytuację:

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

Teraz Utwórz makefile.targ.inc i skopiuj następujące tę sytuację:

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

## <a name="see-also"></a>Zobacz także

[Ogólne informacje o tworzeniu manifestu dla programów C/C++](understanding-manifest-generation-for-c-cpp-programs.md)
