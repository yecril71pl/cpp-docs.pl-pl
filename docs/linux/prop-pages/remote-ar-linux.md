---
title: Właściwości archiwum zdalnego (C++ Linux)
ms.date: 06/07/2019
ms.assetid: 5ee1e44c-8337-4c3a-b2f3-35e4be954f9f
f1_keywords: []
ms.openlocfilehash: 3b6f71d9cceccf0b0221be46bacb1294d84533cd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364301"
---
# <a name="remote-archive-properties-c-linux"></a>Właściwości archiwum zdalnego (C++ Linux)

::: moniker range="vs-2015"

Obsługa systemu Linux jest dostępna w programie Visual Studio 2017 i nowszych.

::: moniker-end

::: moniker range=">=vs-2017"

| Właściwość | Opis |
|--|--|
| Tworzenie indeksu archiwum | Utwórz indeks archiwum (tak jak to robi ranlib). Ta opcja może przyspieszyć łączenie i zmniejszyć zależność w ramach własnej biblioteki. |
| Tworzenie cienkiego archiwum | Utwórz cienkie archiwum.  Cienkie archiwum zawiera względne ścieżki do obiektów zamiast osadzania obiektów.  Przełączanie między cienkim i normalnym wymaga usunięcia istniejącej biblioteki. |
| Brak ostrzeżenia podczas tworzenia | Nie ostrzega, czy i kiedy biblioteka jest tworzona. |
| Obcięcie znacznika czasu | Użyj zera dla znaczników czasu i uids /gids. |
| Pomijanie banera startowego | Nie pokazuj numeru wersji. |
| Pełny | Pełny |
| Opcje dodatkowe | Dodatkowe opcje. |
| Plik wyjściowy | Opcja /OUT zastępuje domyślną nazwę i lokalizację programu tworzonego przez lib. |
| Archiver | Określa program do wywołania podczas łączenia obiektów statycznych lub ścieżkę do archiwizatora w systemie zdalnym. |
| Limit czasu archiwizatora | Zdalny limit czasu archiwizatora w milisekundach. |
| Kopiuj dane wyjściowe | Określa, czy plik wyjściowy kompilacji ma być kopiowany z systemu zdalnego na komputer lokalny. |

::: moniker-end
