---
title: Korzystanie z Clang-uporządkowanego w programie Visual Studio
description: Jak używać Clang-uporządkowanego w programie Visual Studio do analizy kodu w języku Microsoft C++.
ms.date: 02/19/2020
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.clangtidy
ms.openlocfilehash: 30378ab0713d5e00e704f778646b9d60856f2234
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88842471"
---
# <a name="using-clang-tidy-in-visual-studio"></a>Korzystanie z Clang-uporządkowanego w programie Visual Studio

::: moniker range="<=vs-2017"

Obsługa Clang-uporządkowanego wymaga programu Visual Studio 2019 w wersji 16,4 lub nowszej. Aby zapoznać się z dokumentacją tej wersji, ustaw kontrolkę selektora **wersji** programu Visual Studio dla tego artykułu na Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end

::: moniker range=">=vs-2019"

Analiza kodu natywnie obsługuje [Clang-uporządkowanego](https://clang.llvm.org/extra/clang-tidy/) dla projektów MSBuild i cmake, niezależnie od tego, czy są używane zestawy narzędzi CLANG czy MSVC. Testy Clang — uporządkowanego mogą być uruchamiane w ramach analizy kodu w tle. Pojawiają się one jako ostrzeżenia w edytorze (zygzaki) i są wyświetlane w Lista błędów.

Pomoc techniczna Clang-uporządkowanego jest dostępna w programie Visual Studio 2019 w wersji 16,4. Jest ona uwzględniana automatycznie po wybraniu obciążenia C++ w Instalator programu Visual Studio.

Clang-uporządkowanego jest domyślnym narzędziem do analizy przy użyciu zestawu narzędzi LLVM/Clang-CL, dostępnego zarówno w programie MSBuild, jak i w CMake. Można ją skonfigurować przy użyciu zestawu narzędzi MSVC do uruchamiania w programie lub do zastępowania standardowego środowiska analizy kodu. Jeśli używasz zestawu narzędzi Clang-CL, analiza kodu firmy Microsoft jest niedostępna.

Clang-uporządkowanego jest uruchamiany po pomyślnej kompilacji. Może być konieczne rozwiązanie błędów kodu źródłowego w celu uzyskania wyników Clang-uporządkowanego.

## <a name="msbuild"></a>MSBuild

Można skonfigurować Clang-uporządkowanego do uruchamiania w ramach analizy kodu i kompilacji na stronie Ogólne **analizy kodu**  >  **General** w okno właściwości projektu. Opcje konfigurowania narzędzia znajdują się w podmenu Clang-uporządkowanego.

Aby uzyskać więcej informacji, zobacz [jak: Ustawianie właściwości analizy kodu dla projektów C/C++](../code-quality/how-to-set-code-analysis-properties-for-c-cpp-projects.md).

## <a name="cmake"></a>CMake

W projektach CMake można skonfigurować kontrole Clang-uporządkowanego w ramach programu `CMakeSettings.json` . Po otwarciu wybierz pozycję "Edytuj kod JSON" w prawym górnym rogu edytora ustawień projektu CMake. Następujące klucze są rozpoznawane:

- `enableMicrosoftCodeAnalysis`: Włącza analizę kodu firmy Microsoft
- `enableClangTidyCodeAnalysis`: Włącza analizę Clang-uporządkowanego
- `clangTidyChecks`: Konfiguracja Clang-uporządkowanego, określona jako lista rozdzielona przecinkami, czyli sprawdzenia, czy są one włączone lub wyłączone.

Jeśli żadna z opcji "Włącz" nie zostanie określona, program Visual Studio wybierze narzędzie do analizy pasujące do używanego zestawu narzędzi platformy.

## <a name="warning-display"></a>Wyświetlanie ostrzeżeń

Uruchomienia Clang-uporządkowanego powodują wyświetlenie ostrzeżeń w Lista błędów, a jak w edytorze. Użyj kolumny "Kategoria" w Lista błędów, aby sortować i organizować ostrzeżenia Clang-uporządkowanego. Ostrzeżenia w edytorze można skonfigurować przez przełączenie ustawienia "Wyłącz Zawijanie analizy kodu" w obszarze Opcje **narzędzi**  >  **Options**.

## <a name="clang-tidy-configuration"></a>Clang — konfiguracja uporządkowanego

Można skonfigurować sprawdzanie, czy Clang-uporządkowanego działa w programie Visual Studio za pomocą opcji **checks Clang-uporządkowanego** . Ta wartość wejściowa jest dostarczana z **`--checks`** argumentem narzędzia. Dowolna dodatkowa konfiguracja może być uwzględniona w *`.clang-tidy`* plikach niestandardowych. Aby uzyskać więcej informacji, zobacz [dokumentację Clang-uporządkowanego w witrynie LLVM.org](https://clang.llvm.org/extra/clang-tidy/).

## <a name="see-also"></a>Zobacz też

- [Obsługa Clang/LLVM dla projektów MSBuild](https://devblogs.microsoft.com/cppblog/clang-llvm-support-for-msbuild-projects/)
- [Obsługa Clang/LLVM dla projektów CMake](https://devblogs.microsoft.com/cppblog/visual-studio-cmake-support-clang-llvm-cmake-3-14-vcpkg-and-performance-improvements/)

::: moniker-end
