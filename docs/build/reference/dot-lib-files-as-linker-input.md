---
title: ". Lib pliki jako dane wejściowe konsolidatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.AdditionalDependencies
dev_langs:
- C++
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 181c8c3e5e762f2f20d99ca2acadaf285e717b6c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="lib-files-as-linker-input"></a>Pliki .Lib — Wejście konsolidatora
ŁĄCZE akceptuje COFF standardowych bibliotek i COFF Importuj biblioteki, które zwykle mają rozszerzenie. lib. Biblioteki standardowe zawierają obiekty i są tworzone przez narzędzie LIB. Import biblioteki zawierają informacje o eksportu w inne programy i są tworzone przez łącze podczas tworzenia programu, który zawiera eksportu lub przez narzędzie LIB. Uzyskać informacji na temat używania LIB można utworzyć standardowy lub Importuj biblioteki, zobacz [odwołanie do biblioteki LIB](../../build/reference/lib-reference.md). Aby uzyskać więcej informacji dotyczących używania łącze do tworzenia biblioteki importowanej, zobacz [/dll](../../build/reference/dll-build-a-dll.md) opcji.  
  
Biblioteki jest określona do łącza jako argument nazwy pliku lub domyślna biblioteka. ŁĄCZE rozpoznawania odwołań zewnętrznych, wyszukując najpierw w bibliotekach określona w wierszu polecenia, a następnie w domyślnej biblioteki określony za pomocą [/DEFAULTLIB](../../build/reference/defaultlib-specify-default-library.md) opcji, a następnie w domyślnym bibliotek w plikach .obj. Jeśli ścieżka jest określona o nazwie biblioteki, LINK szuka biblioteki w tym katalogu. Jeśli ścieżka nie zostanie określona, LINK otwierana jako pierwsza, w katalogu, do którego łącze działa z, a następnie w dowolnym katalogach określonych w zmiennej środowiskowej LIB.  
  
## <a name="to-add-lib-files-as-linker-input-in-the-development-environment"></a>Aby dodać pliki .lib — wejście konsolidatora w środowisku programistycznym  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Wybierz **dane wejściowe** stronę właściwości w **konsolidatora** folderu.  
  
3.  Modyfikowanie **dodatkowe zależności** właściwości, aby dodać pliki .lib.  
  
## <a name="to-programmatically-add-lib-files-as-linker-input"></a>Aby programowo doda pliki .lib — wejście konsolidatora  
  
-   Zobacz [AdditionalDependencies](https://msdn.microsoft.com/library/microsoft.visualstudio.vcprojectengine.vclinkertool.additionaldependencies.aspx).  
  
## <a name="example"></a>Przykład  
Poniższy przykład przedstawia sposób kompilacji i użycia pliku lib. Najpierw należy utworzyć plików lib:  
  
```cpp  
// lib_link_input_1.cpp  
// compile by using: cl /LD lib_link_input_1.cpp  
__declspec(dllexport) int Test() {  
   return 213;  
}  
```  
  
A następnie skompilować przy użyciu utworzonego pliku lib w tym przykładzie:  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Pliki wyjściowe LINK](../../build/reference/link-input-files.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)