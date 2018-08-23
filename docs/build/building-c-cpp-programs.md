---
title: Kompilowanie programów C/C++ | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- vcbuilding
- buildingaprogramVC
dev_langs:
- C++
helpviewer_keywords:
- builds [C++]
- Visual C++ projects, building
- projects [C++], building
- builds [C++], options
- Visual C++, build options
ms.assetid: fa6ed4ff-334a-4d99-b5e2-a1f83d2b3008
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2fa07308d04d14395b0ca9773e2a0c81ed0c2bc2
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2018
ms.locfileid: "42465139"
---
# <a name="building-cc-programs"></a>Kompilowanie programów C/C++

Można tworzyć projektów Visual C++ w programie Visual Studio lub w wierszu polecenia. Korzysta z programu Visual Studio IDE [MSBuild](../build/msbuild-visual-cpp.md) do tworzenia projektów i rozwiązań. W wierszu polecenia można użyć do tworzenia projektów proste kompilator C/C++ (cl.exe) i program łączący (link.exe). Aby utworzyć bardziej złożone projekty w wierszu polecenia, można użyć programu MSBuild lub [NMAKE](../build/nmake-reference.md). Aby uzyskać ogólne informacje o tym, jak używać programu Visual Studio do tworzenia projektów i rozwiązań, zobacz [kompilowanie i tworzenie](/visualstudio/ide/compiling-and-building-in-visual-studio).  
  
## <a name="in-this-section"></a>W tej sekcji  

[Kompilowanie projektów C++ w Visual Studio](../ide/building-cpp-projects-in-visual-studio.md)  
W tym artykule omówiono sposób używania środowiska IDE programu Visual Studio do kompilowania projektu języka C/C++.  
  
[Kompilowanie kodu C/C++ w wierszu polecenia](../build/building-on-the-command-line.md)  
W tym artykule omówiono sposób używania kompilatora wiersza polecenia języka C/C++ i narzędzia, które znajdują się w programie Visual Studio do kompilacji.  
  
[Kompilowanie aplikacji izolowanych C/C++ oraz aplikacji wykonywanych równocześnie](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)  
W tym artykule opisano model wdrażania dla aplikacji Windows Desktop z koncepcję izolowanymi oraz aplikacjami wykonywanymi side-by-side.  
  
[Dokumentacja kompilacji w języku C/C++](../build/reference/c-cpp-building-reference.md)  
Zawiera łącza do gama artykułów dotyczących programu, tworzenia w języku C++, opcje kompilatora i konsolidatora i różnych narzędzi do kompilacji.  
  
[Konfigurowanie Visual C++ dla wersji 64-bitowych, platformy docelowe x64](../build/configuring-programs-for-64-bit-visual-cpp.md)  
Opisano sposób konfigurowania zarówno Visual Studio i w wierszu polecenia, aby użyć narzędzi 64-bitowym i pod kątem 64-bitowych architekturach, a w tym artykule omówiono typowe problemy przy migracji, gdy kod jest przenoszony do 64-bitowych architekturach.  
  
[Konfigurowanie Visual C++ dla procesorów ARM](../build/configuring-programs-for-arm-processors-visual-cpp.md)  
W tym artykule opisano konwencje używane przez procesory ARM i omówiono typowe problemy przy migracji, gdy kod jest przenoszony do architektury ARM.  
  
[Konfigurowanie programów pod kątem systemu Windows XP](../build/configuring-programs-for-windows-xp.md)  
Zawiera opis sposobu ustawiania zestawu narzędzi platformy docelowej Windows XP programowania.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Kompilowanie i tworzenie](/visualstudio/ide/compiling-and-building-in-visual-studio)  
 W tym artykule opisano system kompilacji programu Visual Studio i narzędzi.