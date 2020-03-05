---
title: Wprowadzenie do szczegółowych informacji o kompilowaniu w języku C++
description: Ogólne omówienie usługi C++ Build Insights.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 2a5799fecc885b96f4278e0f5077662ce5fd7c8f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332010"
---
# <a name="get-started-with-c-build-insights"></a>Wprowadzenie do szczegółowych informacji o kompilowaniu w języku C++

::: moniker range="<=vs-2017"

Narzędzia C++ Build Insights są dostępne w programie Visual Studio 2019. Aby zapoznać się z dokumentacją tej wersji, ustaw kontrolkę selektora wersji programu Visual Studio dla tego artykułu na Visual Studio 2019.

::: moniker-end
::: moniker range="vs-2019"

C++Build Insights to zbiór narzędzi, które zapewniają lepszy wgląd w łańcuch narzędzi Microsoft Visual C++ (MSVC). Narzędzia zbierają dane o C++ kompilacjach i są wyświetlane w formacie, który może pomóc odpowiedzieć na często zadawane pytania, takie jak:

- Czy moje kompilacje są wystarczająco równoległe?
- Co należy uwzględnić we wstępnie skompilowanym nagłówku (PCH)?
- Czy istnieje określone wąskie gardło, na które należy się skoncentrować, aby zwiększyć szybkość kompilacji?

Główne składniki tej technologii to:

- *vcperf. exe*, narzędzie wiersza polecenia, które służy do zbierania śladów dla kompilacji,
- rozszerzenie analizatora wydajności systemu Windows (WPA), które umożliwia wyświetlanie śladów kompilacji w WPA i
- zestaw C++ SDK usługi Build Insights (Software Development Kit) służący do tworzenia własnych narzędzi, C++ które wykorzystują dane usługi Build Insights.

Kliknij poniższe linki, aby szybko rozpocząć pracę z następującymi składnikami:

[Samouczek: vcperf i Analizator wydajności systemu Windows](tutorials/vcperf-and-wpa.md)\
Dowiedz się, jak zbierać ślady C++ kompilacji dla projektów i jak wyświetlać je w WPA.

[Samouczek: podstawy wydajności systemu Windows](tutorials/wpa-basics.md)\
Odkryj przydatne porady dotyczące protokołu WPA do analizowania śladów kompilacji.

[\ zestawu SDK usługi Build Insights C++ ](reference/sdk/overview.md)
Omówienie zestawu SDK usługi C++ Build Insights.

::: moniker-end
