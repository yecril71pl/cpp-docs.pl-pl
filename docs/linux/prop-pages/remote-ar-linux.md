---
title: Właściwości archiwum zdalnego (C++ Linux)
ms.date: 06/07/2019
ms.assetid: 5ee1e44c-8337-4c3a-b2f3-35e4be954f9f
f1_keywords: []
ms.openlocfilehash: dc20eecef9947581ca87b9489285bc058a249e26
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446815"
---
# <a name="remote-archive-properties-c-linux"></a>Właściwości archiwum zdalnego (C++ Linux)

::: moniker range="vs-2015"

Obsługa systemu Linux jest dostępna w programie Visual Studio 2017 i nowszych.

::: moniker-end

::: moniker range=">=vs-2017"

| Właściwość | Opis |
|--|--|
| Utwórz indeks Archiwum | Utwórz indeks archiwum (zgodnie z ranlib). Ta opcja umożliwia przyspieszenie konsolidacji i zmniejszenie zależności w ramach własnej biblioteki. |
| Utwórz cienkie Archiwum | Utwórz cienkie archiwum.  Cienkie archiwum zawierają ścieżki względne do obiektów zamiast osadzania obiektów.  Przełączenie między cienkim i normalnym wymaga usunięcia istniejącej biblioteki. |
| Brak ostrzeżenia podczas tworzenia | Nie ostrzega o tym, czy biblioteka została utworzona. |
| Obetnij sygnaturę czasową | Użyj wartości zero dla sygnatur czasowych i identyfikatorów UID/GIDs. |
| Pomiń transparent startowy | Nie pokazuj numeru wersji. |
| Pełny | Pełny |
| Opcje dodatkowe | Opcje dodatkowe. |
| Plik wyjściowy | Opcja/OUT zastępuje domyślną nazwę i lokalizację programu tworzonego przez bibliotekę. |
| Programu archiwizującego | Określa program do wywołania podczas łączenia obiektów statycznych lub ścieżkę do archiwum w systemie zdalnym. |
| Limit czasu Archiwum | Limit czasu zdalnego archiwum (w milisekundach). |
| Kopiuj dane wyjściowe | Określa, czy plik danych wyjściowych kompilacji ma być kopiowany z systemu zdalnego na maszynę lokalną. |

::: moniker-end
