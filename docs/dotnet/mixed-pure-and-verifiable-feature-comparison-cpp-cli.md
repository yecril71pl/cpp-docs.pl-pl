---
title: Porównanie funkcji mieszanych, czystych i weryfikowalnych (C + +/ CLI)
ms.date: 11/04/2016
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
ms.openlocfilehash: 81fcf986ee68f5f8f64c8070bb992fa1cda1683b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50482081"
---
# <a name="mixed-pure-and-verifiable-feature-comparison-ccli"></a>Porównanie funkcji mieszanych, czystych i weryfikowalnych (C + +/ CLI)

W tym temacie porównano funkcje wśród różnych **/CLR** trybów kompilacji. Aby uzyskać więcej informacji, zobacz [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../build/reference/clr-common-language-runtime-compilation.md).

> [!IMPORTANT]
> **/CLR: pure** i **/CLR: Safe** opcje kompilatora są przestarzałe w programie Visual Studio 2015 i obsługiwane w programie Visual Studio 2017.

## <a name="feature-comparison"></a>Porównanie funkcji

|Funkcja|Mieszany (/ clr)|Czysty (/ clr: pure)|Bezpieczne (/ CLR: Safe)|Informacje pokrewne|
|-------------|---------------------|-------------------------|-------------------------|-------------------------|
|Biblioteka CRT|Obsługiwane|przestarzałe||[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)|
|MFC I ATL|Obsługiwane|||[Aplikacje klasyczne MFC](../mfc/mfc-desktop-applications.md) &#124; [Przegląd klas](../atl/atl-class-overview.md)|
|Funkcje niezarządzane|Obsługiwane|||[Zestawy mieszane (natywne i zarządzane)](../dotnet/mixed-native-and-managed-assemblies.md)|
|Niezarządzanych danych|Obsługiwane|przestarzałe||[Kod czysty i weryfikowalny (C++/CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)|
|Można wywołać za pomocą funkcji niezarządzanych|Obsługiwane||||
|Obsługuje wywoływanie niezarządzanych funkcji|Obsługiwane|przestarzałe|przestarzałe|[Korzystanie z międzyoperacyjności języka C++ (niejawna funkcja PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)|
|Obsługuje odbicia|Tylko bibliotek DLL|przestarzałe|przestarzałe|[Odbicie (C++/CLI)](../dotnet/reflection-cpp-cli.md)|

## <a name="see-also"></a>Zobacz także

- [Kod czysty i weryfikowalny (C++/CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)