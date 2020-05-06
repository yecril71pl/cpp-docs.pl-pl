---
title: Połączenie zewnętrzne
ms.date: 11/04/2016
helpviewer_keywords:
- linkage [C++], external
- external linkage, about external linkage
- external linkage
ms.assetid: a6f8ea69-b405-4cdd-bf12-ad5462b73183
ms.openlocfilehash: 35b0fda1f501755640123f5181454a5c36b7e986
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62233744"
---
# <a name="external-linkage"></a>Połączenie zewnętrzne

Jeśli pierwsza deklaracja na poziomie zakresu plików dla identyfikatora nie korzysta ze specyfikatora klasy magazynu **static** , obiekt ma połączenie zewnętrzne.

Jeśli deklaracja identyfikatora dla funkcji nie ma *specyfikatora klasy magazynu*, jego połączenie jest określane dokładnie tak, jakby zostało zadeklarowane za pomocą *specyfikatora klasy magazynu* `extern`. Jeśli deklaracja identyfikatora dla obiektu ma zakres plików i brak *specyfikatora klasy magazynu*, jego powiązanie jest zewnętrzne.

Nazwa identyfikatora z zewnętrznym powiązaniem wyznacza tę samą funkcję lub obiekt danych, tak jak każda inna Deklaracja dla tej samej nazwy z zewnętrznym powiązaniem. Dwie deklaracje mogą znajdować się w tej samej jednostce translacji lub w różnych jednostkach tłumaczenia. Jeśli obiekt lub funkcja ma także globalny okres istnienia, obiekt lub funkcja jest współużytkowany przez cały program.

## <a name="see-also"></a>Zobacz też

[Użycie zewnętrznie w celu określenia powiązania](../cpp/using-extern-to-specify-linkage.md)
