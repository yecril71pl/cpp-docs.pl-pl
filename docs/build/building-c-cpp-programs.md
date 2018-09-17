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
ms.openlocfilehash: 2792b49d7d3d3f107e39931ff62e6c4137c9c5ca
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45723271"
---
# <a name="building-cc-programs"></a>Kompilowanie programów C/C++

Można tworzyć projektów Visual C++ w programie Visual Studio lub w wierszu polecenia. Korzysta z programu Visual Studio IDE [MSBuild](../build/msbuild-visual-cpp.md) do tworzenia projektów i rozwiązań. W wierszu polecenia można użyć do tworzenia projektów proste kompilator C/C++ (cl.exe) i program łączący (link.exe). Aby utworzyć bardziej złożone projekty w wierszu polecenia, można użyć programu MSBuild lub [NMAKE](../build/nmake-reference.md). Aby uzyskać ogólne informacje o tym, jak używać programu Visual Studio do tworzenia projektów i rozwiązań, zobacz [kompilowanie i tworzenie](/visualstudio/ide/compiling-and-building-in-visual-studio).

## <a name="in-this-section"></a>W tej sekcji

[Kompilowanie projektów C++ w programie Visual Studio](../ide/building-cpp-projects-in-visual-studio.md) w tym artykule omówiono sposób używania środowiska IDE programu Visual Studio do kompilowania projektu języka C/C++.

[Kompilowanie kodu C/C++ w wierszu polecenia](../build/building-on-the-command-line.md) w tym artykule omówiono sposób używania kompilatora wiersza polecenia języka C/C++ i narzędzia, które znajdują się w programie Visual Studio do kompilacji.

[Kompilowanie aplikacji izolowanych C/C++ i zestawów Side-by-side](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md) w tym artykule opisano model wdrażania dla aplikacji Windows Desktop z koncepcję izolowanymi oraz aplikacjami wykonywanymi side-by-side.

[Odniesienie budowanie C/C++](../build/reference/c-cpp-building-reference.md) udostępnia linki do gama artykułów dotyczących programu, tworzenia w języku C++, kompilatora i opcje konsolidatora i różnych narzędzi do kompilacji.

[Konfigurowanie Visual C++ x64 64-bitowy, obiekty docelowe](../build/configuring-programs-for-64-bit-visual-cpp.md) opisano sposób konfigurowania zarówno Visual Studio i w wierszu polecenia, aby użyć narzędzi 64-bitowym i pod kątem 64-bitowych architekturach i omówiono typowe problemy przy migracji, gdy kod jest przenoszony do 64-bitowych architektury.

[Konfigurowanie Visual C++ dla procesorów ARM](../build/configuring-programs-for-arm-processors-visual-cpp.md) opisano konwencje używane przez procesory ARM i omówiono typowe problemy przy migracji, gdy kod jest przenoszony do architektury ARM.

[Konfigurowanie programów systemu Windows XP](../build/configuring-programs-for-windows-xp.md) opisano, jak ustawić zestaw narzędzi platformy docelowej Windows XP rozwoju.

## <a name="related-sections"></a>Sekcje pokrewne

[Kompilowanie i tworzenie](/visualstudio/ide/compiling-and-building-in-visual-studio) system i narzędzia kompilacji programu Visual Studio w tym artykule opisano.