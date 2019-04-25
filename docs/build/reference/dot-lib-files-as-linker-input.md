---
title: Pliki .Lib — Wejście konsolidatora
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.AdditionalDependencies
helpviewer_keywords:
- OMF libraries
- linking [C++], OMF libraries
- import libraries, linker files
- libraries [C++], .lib files as linker input
- COFF files, import libraries
- default libraries [C++], linker output
- default libraries [C++]
- defaults [C++], libraries
- .lib files
ms.assetid: dc5d2b1c-2487-41fa-aa71-ad1e0647958b
ms.openlocfilehash: 02f719b3101b04ad6b219bf882a50a994061af0c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62293644"
---
# <a name="lib-files-as-linker-input"></a>Pliki .Lib — Wejście konsolidatora

LINK akceptuje COFF standardowych bibliotek i COFF importowania bibliotek, które zwykle z rozszerzeniem. lib. Standardowe biblioteki zawiera obiektów i są tworzone za pomocą narzędzia LIB. Bibliotek importu zawierają informacje dotyczące eksportu w innych programach i są tworzone przez łącze, opiera się program, który zawiera eksporty albo za pomocą narzędzia LIB. Aby uzyskać informacji na temat używania biblioteki do tworzenia standardowych lub Importuj biblioteki, zobacz [odwołanie do biblioteki LIB](lib-reference.md). Szczegółowe informacje na temat przy użyciu LINKU, aby utworzyć bibliotekę importu, [/dll](dll-build-a-dll.md) opcji.

Biblioteka określono LINK jako argument nazwy pliku lub domyślna biblioteka. LINK rozpoznawania odwołań zewnętrznych, wyszukując najpierw w bibliotekach określone w wierszu polecenia, a następnie w domyślnych bibliotek określony za pomocą [/DEFAULTLIB](defaultlib-specify-default-library.md) opcji, a następnie w domyślnych bibliotek nazwę w plikach .obj. Jeśli ścieżka jest określona za pomocą nazwy biblioteki, łącze szuka biblioteki, w tym katalogu. Jeśli ścieżka nie zostanie określona, łączy wygląda pierwszy w katalogu, który łączy jest uruchamiana z, a następnie w dowolnym katalogi określone w zmiennej środowiskowej LIB.

## <a name="to-add-lib-files-as-linker-input-in-the-development-environment"></a>Aby dodać pliki .lib — wejście konsolidatora w środowisku programistycznym

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **dane wejściowe** — strona właściwości w **konsolidatora** folderu.

1. Modyfikowanie **dodatkowe zależności** właściwości, aby dodać pliki lib.

## <a name="to-programmatically-add-lib-files-as-linker-input"></a>Aby programowo dodać pliki .lib — wejście konsolidatora

- Zobacz [AdditionalDependencies](/dotnet/api/microsoft.visualstudio.vcprojectengine.vclinkertool.additionaldependencies).

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak tworzenie i używanie pliku. lib. Najpierw należy utworzyć plik .lib:

```cpp
// lib_link_input_1.cpp
// compile by using: cl /LD lib_link_input_1.cpp
__declspec(dllexport) int Test() {
   return 213;
}
```

A następnie skompilować ten przykład za pomocą pliku .lib, który został utworzony:

```cpp
// lib_link_input_2.cpp
// compile by using: cl /EHsc lib_link_input_1.lib lib_link_input_2.cpp
__declspec(dllimport) int Test();
#include <iostream>
int main() {
   std::cout << Test() << std::endl;
}
```

```Output
213
```

## <a name="see-also"></a>Zobacz także

[Pliki wejściowe LINK](link-input-files.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
