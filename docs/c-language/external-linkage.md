---
title: Połączenie zewnętrzne
ms.date: 11/04/2016
helpviewer_keywords:
- linkage [C++], external
- external linkage, about external linkage
- external linkage
ms.assetid: a6f8ea69-b405-4cdd-bf12-ad5462b73183
ms.openlocfilehash: d8a7655b7504aa8458bda8db24ff3f919b5b09c1
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509917"
---
# <a name="external-linkage"></a>Połączenie zewnętrzne

Jeśli pierwsza deklaracja na poziomie zakresu plików dla identyfikatora nie używa **`static`** specyfikatora klasy magazynu, obiekt ma połączenie zewnętrzne.

Jeśli deklaracja identyfikatora dla funkcji nie ma *specyfikatora klasy magazynu*, jego połączenie jest określane dokładnie tak, jakby zostało zadeklarowane za pomocą *specyfikatora klasy magazynu* **`extern`** . Jeśli deklaracja identyfikatora dla obiektu ma zakres plików i brak *specyfikatora klasy magazynu*, jego powiązanie jest zewnętrzne.

Nazwa identyfikatora z zewnętrznym powiązaniem wyznacza tę samą funkcję lub obiekt danych, tak jak każda inna Deklaracja dla tej samej nazwy z zewnętrznym powiązaniem. Dwie deklaracje mogą znajdować się w tej samej jednostce translacji lub w różnych jednostkach tłumaczenia. Jeśli obiekt lub funkcja ma także globalny okres istnienia, obiekt lub funkcja jest współużytkowany przez cały program.

## <a name="see-also"></a>Zobacz też

[Użycie zewnętrznie w celu określenia powiązania](../cpp/extern-cpp.md)
