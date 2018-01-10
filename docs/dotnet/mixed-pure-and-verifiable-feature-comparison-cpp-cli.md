---
title: "Porównanie funkcji mieszanych, czystych i weryfikowalnych (C + +/ CLI) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- safe assemblies [C++], vs. pure
- mixed assemblies [C++], vs. pure
- safe assemblies [C++], vs. mixed
- pure MSIL [C++]
- verifiable assemblies [C++]
- pure MSIL [C++], vs. safe
- pure MSIL [C++], vs. mixed
- pure MSIL [C++], compared to mixed and safe
- verifiable assemblies [C++], vs. mixed
- mixed assemblies [C++], vs. safe
- verifiable assemblies [C++], vs. pure
- pure assemblies [C++]
- safe assemblies [C++]
- mixed assemblies [C++]
ms.assetid: 3f7a82ba-0e69-4927-ba0c-fbc3160e4394
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 3ee9fbed3fd82fd450fd179683fd119cb1630034
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="mixed-pure-and-verifiable-feature-comparison-ccli"></a>Porównanie funkcji mieszanych, czystych i weryfikowalnych (C++/CLI)
W tym temacie porównanie funkcji spośród różnych **/CLR** tryby kompilacji. Aby uzyskać więcej informacji, zobacz [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../build/reference/clr-common-language-runtime-compilation.md).  
  
 **/CLR: pure** i **/CLR: Safe** — opcje kompilatora zostały uznane za przestarzałe w programie Visual Studio 2015.  
  
## <a name="feature-comparison"></a>Porównanie funkcji  
  
|Funkcja|Mieszane (/ clr)|Czysty (/ clr: pure)|Bezpieczne (/ CLR: Safe)|Informacje pokrewne|  
|-------------|---------------------|-------------------------|-------------------------|-------------------------|  
|Biblioteka CRT|Obsługiwane|Obsługiwane||[Procedury czasu wykonywania według kategorii](../c-runtime-library/run-time-routines-by-category.md)|  
|MFC/ATL|Obsługiwane|||[Aplikacje dla pulpitu MFC](../mfc/mfc-desktop-applications.md) &#124; [Przegląd klas](../atl/atl-class-overview.md)|  
|Funkcje niezarządzane|Obsługiwane|||[Zestawy mieszane (natywne i zarządzane)](../dotnet/mixed-native-and-managed-assemblies.md)|  
|Niezarządzanych danych|Obsługiwane|Obsługiwane||[Kod czysty i weryfikowalny (C++/CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)|  
|Można wywołać z funkcjami niezarządzanymi|Obsługiwane|||[Porady: Migracja do/CLR: pure (C + +/ CLI)](../dotnet/how-to-migrate-to-clr-pure-cpp-cli.md)|  
|Obsługuje wywoływanie niezarządzanych funkcji|Obsługiwane|Tylko funkcje w stylu języka C|P/Invoke tylko|[Korzystanie z międzyoperacyjności języka C++ (niejawna funkcja PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)|  
|Obsługuje odbicia|Tylko biblioteki dll|Obsługiwane|Obsługiwane|[Odbicie (C++/CLI)](../dotnet/reflection-cpp-cli.md)|  
  
## <a name="see-also"></a>Zobacz też  
 [Kod czysty i weryfikowalny (C++/CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)