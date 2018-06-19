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
ms.openlocfilehash: 2894c503dde89668bfb90b615c7b0966fe5fe2e5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32360978"
---
# <a name="building-cc-programs"></a>Kompilowanie programów C/C++

Można tworzyć projektów Visual C++ w programie Visual Studio lub w wierszu polecenia. Korzysta z programu Visual Studio IDE [MSBuild](../build/msbuild-visual-cpp.md) do tworzenia projektów i rozwiązań. W wierszu polecenia można użyć do tworzenia projektów proste kompilatora C/C++ (cl.exe) i konsolidatora (link.exe). Aby tworzyć bardziej złożone projekty w wierszu polecenia, można użyć programu MSBuild lub [NMAKE](../build/nmake-reference.md). Aby uzyskać ogólne informacje o sposobie używania [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] do tworzenia projektów i rozwiązań, zobacz [kompilowania i tworzenia](/visualstudio/ide/compiling-and-building-in-visual-studio).  
  
## <a name="in-this-section"></a>W tej sekcji  

[Kompilowanie projektów C++ w Visual Studio](../ide/building-cpp-projects-in-visual-studio.md)  
W tym artykule omówiono sposób używania środowiska IDE programu Visual Studio, aby skompilować projekt C/C++.  
  
[Kompilowanie kodu C/C++ w wierszu polecenia](../build/building-on-the-command-line.md)  
W tym artykule omówiono sposób używania kompilatora wiersza polecenia języka C/C++ i kompilacji narzędzia, które są uwzględniane w programie Visual Studio.  
  
[Kompilowanie aplikacji izolowanych C/C++ oraz aplikacji wykonywanych równocześnie](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)  
W tym artykule opisano model wdrożenia dla aplikacji Windows Desktop w pomysł izolowanych aplikacji i zestawy side-by-side.  
  
[Dokumentacja kompilacji w języku C/C++](../build/reference/c-cpp-building-reference.md)  
Zawiera łącza do artykułów odwołanie o programie kompilacji w C++ kompilatorze i konsolidatorze i opcje różnych narzędzi kompilacji.  
  
[Konfigurowanie Visual C++ dla wersji 64-bitowych, platformy docelowe x64](../build/configuring-programs-for-64-bit-visual-cpp.md)  
Opisuje do skonfigurowania programu Visual Studio i wiersza polecenia służące do 64-bitowego zestawu narzędzi oraz pod kątem architektur 64-bitowych i omówiono typowe problemy przy migracji, gdy kod zostanie przeniesiony do architektury 64-bitowych.  
  
[Konfigurowanie Visual C++ dla procesorów ARM](../build/configuring-programs-for-arm-processors-visual-cpp.md)  
W tym artykule opisano konwencje używane przez procesory ARM i omówiono typowe problemy przy migracji, gdy kod zostanie przeniesiony do architektury ARM.  
  
[Konfigurowanie programów pod kątem systemu Windows XP](../build/configuring-programs-for-windows-xp.md)  
Opisuje sposób ustawiania zestaw narzędzi platformy docelowej rozwoju systemu Windows XP.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Kompilowanie i tworzenie](/visualstudio/ide/compiling-and-building-in-visual-studio)  
 Opisuje system kompilacji programu Visual Studio i narzędzi.