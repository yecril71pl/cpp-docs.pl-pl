---
title: Właściwości zdalnego archiwum (C++ Linux)
ms.date: 06/07/2019
ms.assetid: 5ee1e44c-8337-4c3a-b2f3-35e4be954f9f
f1_keywords: []
ms.openlocfilehash: 00de4ac56a9ce390672019c7fe5a838367823100
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2019
ms.locfileid: "66821269"
---
# <a name="remote-archive-properties-c-linux"></a>Właściwości zdalnego archiwum (C++ Linux)

::: moniker range="vs-2015"

Pomoc techniczna Linux support jest dostępne w programie Visual Studio 2017 i nowszych wersjach.

::: moniker-end

::: moniker range=">=vs-2017"

Właściwość | Opis
--- | ---
Utwórz indeks archiwum | Utwórz indeks archiwum (ponieważ jest to wykonywane przez ranlib). Ta opcja może przyspieszyć konsolidowanie i ograniczyć zależność w obrębie własnej biblioteki.
Utwórz archiwum uproszczone | Utwórz archiwum uproszczone.  Archiwum uproszczone zawiera ścieżki względne do obiektów zamiast osadzania obiektów.  Przełączanie między uproszczonym i normalnym wymaga usunięcia istniejącej biblioteki.
Bez ostrzeżenia o utworzeniu | Nie Ostrzegaj, jeśli lub po utworzeniu biblioteki.
Obetnij sygnaturę czasową | Użyj wartości zero dla sygnatur czasowych i GID.
Pomijaj transparent startowy | Nie pokazuj numeru wersji.
Pełny | Pełny
Dodatkowe opcje | Dodatkowe opcje.
Plik wyjściowy | Opcja/out przesłania domyślną nazwę i lokalizację programu, który tworzy lib.
Programu archiwizującego | Określa program do wywołania podczas łączenia obiektów statycznych lub ścieżkę do programu archiwizującego w systemie zdalnym.
Limit czasu programu archiwizującego | Czasu zdalnego programu archiwizującego, w milisekundach.
Kopiuj dane wyjściowe | Określa, czy można skopiować pliku danych wyjściowych kompilacji z systemu zdalnego na maszynę lokalną.

::: moniker-end
