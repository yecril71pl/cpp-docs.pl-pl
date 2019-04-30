---
title: Właściwości zdalnego archiwum (C++ Linux)
ms.date: 9/26/2017
ms.assetid: 5ee1e44c-8337-4c3a-b2f3-35e4be954f9f
f1_keywords: []
ms.openlocfilehash: bcd0e0eef16addc60743000b6ed8cba12276e29c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393002"
---
# <a name="remote-archive-properties-c-linux"></a>Właściwości zdalnego archiwum (C++ Linux)

Właściwość | Opis
--- | ---
Utwórz indeks archiwum | Utwórz indeks archiwum (cf. ranlib).  Może to przyspieszyć konsolidowanie i ograniczyć zależność w obrębie własnej biblioteki.
Utwórz archiwum uproszczone | Utwórz archiwum uproszczone.  Archiwum uproszczone zawiera ścieżki względne do obiektów zamiast osadzania obiektów.  Przełączanie między uproszczonym i normalnym wymaga usunięcia istniejącej biblioteki.
Bez ostrzeżenia o utworzeniu | Nie Ostrzegaj, jeśli po utworzeniu biblioteki.
Obetnij sygnaturę czasową | Użyj wartości zero dla sygnatur czasowych i GID.
Pomijaj transparent startowy | Nie pokazuj numeru wersji.
Pełny | Pełny
Dodatkowe opcje | Dodatkowe opcje.
Plik wyjściowy | Opcja/out przesłania domyślną nazwę i lokalizację programu, który tworzy lib.
Programu archiwizującego | Określa program do wywołania podczas łączenia obiektów statycznych lub ścieżkę do programu archiwizującego w systemie zdalnym.
Limit czasu programu archiwizującego | Czasu zdalnego programu archiwizującego, w milisekundach.
Kopiuj dane wyjściowe | Określa, czy można skopiować pliku danych wyjściowych kompilacji z systemu zdalnego na maszynę lokalną.
