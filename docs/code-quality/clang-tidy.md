---
title: Korzystanie z clang-tidy w programie Visual Studio
description: Jak używać Clang-Tidy w programie Visual Studio do analizy kodu Microsoft C++.
ms.date: 02/19/2020
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.clangtidy
author: frozenpandaman
ms.author: efessler
ms.openlocfilehash: ff32f522eaacee67e19aedaa1153b2c68edc98d4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81355151"
---
# <a name="using-clang-tidy-in-visual-studio"></a>Korzystanie z clang-tidy w programie Visual Studio

::: moniker range="<=vs-2017"

Obsługa programu Clang-Tidy wymaga programu Visual Studio 2019 w wersji 16.4 lub nowszej. Aby zapoznać się z dokumentacją dla tej wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end

::: moniker range=">=vs-2019"

Analiza kodu natywnie obsługuje [Clang-Tidy](https://clang.llvm.org/extra/clang-tidy/) dla projektów MSBuild i CMake, niezależnie od tego, czy używasz zestawów narzędzi Clang lub MSVC. Kontrole Clang-Tidy mogą być uruchamiane w ramach analizy kodu w tle. Są one wyświetlane jako ostrzeżenia w edytorze (squiggles) i wyświetlane na liście błędów.

Obsługa programu Clang-Tidy jest dostępna od programu Visual Studio 2019 w wersji 16.4. Jest on dołączony automatycznie po wybraniu obciążenia języka C++ w Instalatorze programu Visual Studio.

Clang-Tidy jest domyślnym narzędziem do analizy podczas korzystania z zestawu narzędzi LLVM/clang-cl, dostępnego zarówno w MSBuild, jak i CMake. Można go skonfigurować podczas korzystania z zestawu narzędzi MSVC do uruchamiania obok lub zastąpić standardowe środowisko analizy kodu. Jeśli używasz zestawu narzędzi clang-cl, analiza kodu firmy Microsoft jest niedostępna.

Clang-Tidy działa po udanej kompilacji. Może być konieczne rozwiązanie błędów kodu źródłowego, aby uzyskać wyniki Clang-Tidy.

## <a name="msbuild"></a>MSBuild

Można skonfigurować Clang-Tidy do uruchamiania jako część analizy kodu i kompilacji na stronie**Ogólne** **analizy** > kodu w oknie Właściwości projektu. Opcje konfiguracji narzędzia można znaleźć w podmenu Clang-Tidy.

Aby uzyskać więcej informacji, zobacz [Jak: Ustawianie właściwości analizy kodu dla projektów C/C++.](../code-quality/how-to-set-code-analysis-properties-for-c-cpp-projects.md)

## <a name="cmake"></a>CMake

W projektach CMake możesz skonfigurować kontrole Clang-Tidy w ramach `CMakeSettings.json`. Po otwarciu kliknij "Edytuj JSON" w prawym górnym rogu Edytora ustawień projektu CMake. Rozpoznawane są następujące klucze:

- `enableMicrosoftCodeAnalysis`: Włącza analizę kodu firmy Microsoft
- `enableClangTidyCodeAnalysis`: Umożliwia analizę Clang-Tidy
- `clangTidyChecks`: Konfiguracja Clang-Tidy, określona jako lista oddzielona przecinkami, to jest, sprawdza, czy ma być włączona lub wyłączona

Jeśli żadna z opcji "włącz" nie zostanie określona, program Visual Studio wybierze narzędzie analityczne pasujące do używanego zestawu narzędzi platformy.

## <a name="warning-display"></a>Wyświetlacz ostrzegawczy

Przebiegi Clang-Tidy powodują ostrzeżenia wyświetlane na liście błędów i jako w edytorze squiggles pod odpowiednimi sekcjami kodu. Użyj kolumny "Kategoria" na liście błędów, aby sortować i organizować ostrzeżenia Clang-Tidy. Ostrzeżenia w edytorze można skonfigurować, przełączając ustawienie "Wyłącz squiggles analizy kodu" w obszarze**Opcje** **narzędzi** > .

## <a name="clang-tidy-configuration"></a>Konfiguracja Clang-Tidy

Można skonfigurować kontrole, które clang-tidy działa wewnątrz programu Visual Studio za pomocą **opcji Clang-Tidy Checks.** To dane wejściowe są dostarczane do **argumentu --checks** narzędzia. Każda dalsza konfiguracja może *`.clang-tidy`* być zawarta w plikach niestandardowych. Aby uzyskać więcej informacji, zobacz [dokumentację Clang-Tidy na temat LLVM.org](https://clang.llvm.org/extra/clang-tidy/).

## <a name="see-also"></a>Zobacz też

- [Wsparcie clang/LLVM dla projektów MSBuild](https://devblogs.microsoft.com/cppblog/clang-llvm-support-for-msbuild-projects/)
- [Wsparcie Clang/LLVM dla projektów CMake](https://devblogs.microsoft.com/cppblog/visual-studio-cmake-support-clang-llvm-cmake-3-14-vcpkg-and-performance-improvements/)

::: moniker-end
