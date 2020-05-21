---
title: Wprowadzenie do szczegółowych informacji o kompilowaniu w języku C++
description: Ogólne omówienie tworzenia szczegółowych informacji w języku C++.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 28d7e0758ea521af424129c546297fc97e3d6659
ms.sourcegitcommit: 8c8ed02a6f3bcb5ee008e3fe30ba7595d7c4c922
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83759228"
---
# <a name="get-started-with-c-build-insights"></a>Wprowadzenie do szczegółowych informacji o kompilowaniu w języku C++

::: moniker range="<=vs-2017"

Narzędzia do tworzenia szczegółowych danych w języku C++ są dostępne w programie Visual Studio 2019. Aby zapoznać się z dokumentacją tej wersji, ustaw kontrolkę selektora **wersji** programu Visual Studio dla tego artykułu na Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range="vs-2019"

Program C++ build Insights to zbiór narzędzi, które zapewniają lepszy wgląd w łańcuch narzędzi Microsoft Visual C++ (MSVC). Narzędzia zbierają dane o kompilacjach języka C++ i są wyświetlane w formacie, który może pomóc odpowiedzieć na często zadawane pytania, takie jak:

- Czy moje kompilacje są wystarczająco równoległe?
- Co należy uwzględnić we wstępnie skompilowanym nagłówku (PCH)?
- Czy istnieje określone wąskie gardło, na które należy się skoncentrować, aby zwiększyć szybkość kompilacji?

Główne składniki tej technologii to:

- *vcperf. exe*, narzędzie wiersza polecenia, które służy do zbierania śladów dla kompilacji,
- rozszerzenie analizatora wydajności systemu Windows (WPA), które umożliwia wyświetlanie śladów kompilacji w WPA i
- zestaw SDK usługi Build Insights, który umożliwia tworzenie własnych narzędzi, które zużywają dane usługi C++ build Insights.

## <a name="documentation-sections"></a>Sekcje dokumentacji

[Samouczek: vcperf i Analizator wydajności systemu Windows](tutorials/vcperf-and-wpa.md)\
Dowiedz się, jak zbierać ślady kompilacji dla projektów języka C++ i jak wyświetlać je w protokole WPA.

[Samouczek: podstawy wydajności systemu Windows](tutorials/wpa-basics.md)\
Odkryj przydatne porady dotyczące protokołu WPA do analizowania śladów kompilacji.

[Zestaw SDK usługi Build Insights dla języka C++](reference/sdk/overview.md)\
Omówienie zestawu SDK usługi Build Insights dla języka C++.

## <a name="articles"></a>Artykuły

Przeczytaj te artykuły z oficjalnego bloga zespołu języka C++, aby uzyskać więcej informacji na temat kompilacji w języku C++:

[Wprowadzenie do wglądu w dane kompilacji języka C++](https://devblogs.microsoft.com/cppblog/introducing-c-build-insights/)

[Programistycznie Analizuj kompilacje za pomocą zestawu SDK usługi Build Insights](https://devblogs.microsoft.com/cppblog/analyze-your-builds-programmatically-with-the-c-build-insights-sdk/)

[Znajdowanie wąskich gardeł kompilacji za pomocą usługi C++ build Insights](https://devblogs.microsoft.com/cppblog/finding-build-bottlenecks-with-cpp-build-insights/)

[Szybsze kompilacje z sugestiami PCH z usługi C++ build Insights](https://devblogs.microsoft.com/cppblog/faster-builds-with-pch-suggestions-from-c-build-insights/)

::: moniker-end
