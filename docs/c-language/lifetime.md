---
title: Okres istnienia
ms.date: 11/04/2016
helpviewer_keywords:
- local variables, lifetime
- variables, automatic
- storage classes, lifetime
- variables, lifetime
- automatic storage class
- automatic storage class, duration
- storage class specifiers, storage duration
- memory allocation, dynamic allocation
- functions [C++], lifetime
- storage duration
- dynamic memory allocation
- memory allocation, dynamic
- lifetime
- global variables, lifetime
ms.assetid: ff0b42cb-3f0f-49a3-a94f-d1d825d8ddfe
ms.openlocfilehash: 5e5d3b852148284312d2e1fb4cee1df432ac161b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50665221"
---
# <a name="lifetime"></a>Okres istnienia

„Okres istnienia” jest okresem podczas wykonywania programu, w którym istnieje zmienna lub funkcja. Czas magazynowania identyfikatora określa jego okres istnienia.

Identyfikator zadeklarowany za pomocą *storage-class-specifier* **statyczne** ma statyczny czas magazynowania. Identyfikatory z statycznym czasem magazynowania (zwane również „global”) są przechowywane i mają zdefiniowaną wartość na czas trwania programu. Magazyn jest zarezerwowany i wartość przechowywana identyfikatora jest zainicjowana tylko raz, przed uruchomieniem programu. Identyfikator zadeklarowany za pomocą zewnętrznego lub wewnętrznego powiązania ma także statyczny czas magazynowania (zobacz [powiązania](../c-language/linkage.md)).

Identyfikator zadeklarowany bez **statyczne** Specyfikator klasy magazynowania ma czas trwania automatycznego przechowywania, jeśli zostanie ona zadeklarowana wewnątrz funkcji. Identyfikator z czasem automatycznego przechowywania („identyfikator lokalny”) posiada magazyn i zdefiniowaną wartością tylko w bloku, w którym został zdefiniowany lub zadeklarowany identyfikator. Nowy magazyn jest każdorazowo przydzielany automatycznemu identyfikatorowi, program wchodzi do tego bloku, a następnie traci swój magazyn (oraz jego wartość) gdy program zamyka blok. Identyfikatory zadeklarowane w funkcji bez powiązania mają również automatyczny czas magazynowania.

Następujące reguły określają, czy identyfikator ma globalny (statyczny) lub lokalny (automatyczny) okres istnienia:

- Wszystkie funkcje mają statyczny okres istnienia. Dlatego istnieją cały czas podczas wykonywania programu. Identyfikatory zadeklarowane na poziomie zewnętrznym (czyli na zewnątrz wszystkich bloków w programie, na tym samym poziomie co definicje funkcji) zawsze mają globalne (statyczne) okresy istnienia.

- Jeśli zmienna lokalna ma inicjator, zmienna jest zawsze zainicjowana podczas jego tworzenia (o ile nie jest zadeklarowany jako **statyczne**). Parametry funkcji mają również lokalne okresy istnienia. Można określić globalny okres istnienia dla identyfikatora w bloku, umieszczając **statyczne** — Specyfikator klasy magazynowania w jego deklaracji. Po zadeklarowaniu **statyczne**, zmienna zachowuje swoją wartość od jednego wpisu bloku do następnego.

Mimo że istnieje identyfikator z globalnym okresem istnienia, podczas wykonywania programu źródłowego (na przykład zewnętrznie zadeklarowana zmienna lub zmienna lokalna zadeklarowana **statyczne** — słowo kluczowe), nie mogą nie być widoczne we wszystkich części programu. Zobacz [zakres i widoczność](../c-language/scope-and-visibility.md) informacje o widoczności i zobacz [klasy magazynu](../c-language/c-storage-classes.md) dyskusję na temat *storage-class-specifier* nieterminalnych.

Pamięć może być przydzielenia w razie potrzeby (dynamicznie), jeżeli użytkownik użyje specjalnie utworzonej biblioteki procedur, takiej jak `malloc`. Ponieważ dynamiczna alokacja pamięci używa biblioteki procedur, nie uważa się tego za część języka. Zobacz [— funkcja malloc](../c-runtime-library/reference/malloc.md) działa w programach *odwołanie do biblioteki wykonawczej*.

## <a name="see-also"></a>Zobacz też

[Okres istnienia, zakres, widoczność i połączenie](../c-language/lifetime-scope-visibility-and-linkage.md)