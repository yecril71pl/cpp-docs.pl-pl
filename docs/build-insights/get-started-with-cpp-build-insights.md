---
title: Wprowadzenie do szczegółowych informacji o kompilowaniu w języku C++
description: Omówienie wysokiego poziomu usługi C++ Build Insights.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 3a75dfe3bf1263cce53d70b764607cad4eec86d5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325713"
---
# <a name="get-started-with-c-build-insights"></a>Wprowadzenie do szczegółowych informacji o kompilowaniu w języku C++

::: moniker range="<=vs-2017"

Narzędzia aplikacji Skompilowanie kompilacji języka C++ są dostępne w programie Visual Studio 2019. Aby zapoznać się z dokumentacją dla tej wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range="vs-2019"

C++ Build Insights to zbiór narzędzi, które zapewnia lepszy wgląd w łańcuch narzędzi microsoft visual c++(MSVC). Narzędzia zbierają dane o kompilacjach języka C++ i przedstawiają je w formacie, który pomoże Ci odpowiedzieć na typowe pytania, takie jak:

- Czy moje kompilacje są wystarczająco równoległe?
- Co należy uwzględnić w moim wstępnie skompilowanym nagłówku (PCH)?
- Czy istnieje konkretne wąskie gardło, na które powinienem się skupić, aby zwiększyć szybkość budowy?

Głównymi składnikami tej technologii są:

- *vcperf.exe*, narzędzie wiersza polecenia, którego można użyć do zbierania śladów dla kompilacji,
- rozszerzenie analizatora wydajności systemu Windows (WPA), które umożliwia wyświetlanie śladów kompilacji w WPA, oraz
- Zestaw SDK kompilacji aplikacji C++ do tworzenia oprogramowania do tworzenia własnych narzędzi, które zużywają dane programu C++ Build Insights.

Kliknij poniższe linki, aby szybko rozpocząć korzystanie z tych składników:

[Samouczek: vcperf i analizator wydajności systemu Windows](tutorials/vcperf-and-wpa.md)\
Dowiedz się, jak zbierać ślady kompilacji dla projektów języka C++ i jak je wyświetlać w WPA.

[Samouczek: Podstawy wydajności systemu Windows](tutorials/wpa-basics.md)\
Poznaj przydatne wskazówki WPA dotyczące analizowania śladów kompilacji.

[SDK kompilacji języka C++](reference/sdk/overview.md)\
Omówienie SDK analizy kompilacji języka C++.

::: moniker-end
