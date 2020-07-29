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
ms.openlocfilehash: 752230db54727516e0c48c0621eaadc59486e2e4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218848"
---
# <a name="lifetime"></a>Okres istnienia

„Okres istnienia” jest okresem podczas wykonywania programu, w którym istnieje zmienna lub funkcja. Czas magazynowania identyfikatora określa jego okres istnienia.

Identyfikator zadeklarowany za pomocą *specyfikatora klasy magazynu* **`static`** ma statyczny czas przechowywania. Identyfikatory z statycznym czasem magazynowania (zwane również „global”) są przechowywane i mają zdefiniowaną wartość na czas trwania programu. Magazyn jest zarezerwowany i wartość przechowywana identyfikatora jest zainicjowana tylko raz, przed uruchomieniem programu. Identyfikator zadeklarowany za pomocą zewnętrznego lub wewnętrznego powiązania ma także statyczny czas przechowywania (zobacz [powiązania](../c-language/linkage.md)).

Identyfikator zadeklarowany bez **`static`** specyfikatora klasy magazynu ma Automatyczny czas przechowywania, jeśli jest zadeklarowany wewnątrz funkcji. Identyfikator z czasem automatycznego przechowywania („identyfikator lokalny”) posiada magazyn i zdefiniowaną wartością tylko w bloku, w którym został zdefiniowany lub zadeklarowany identyfikator. Nowy magazyn jest każdorazowo przydzielany automatycznemu identyfikatorowi, program wchodzi do tego bloku, a następnie traci swój magazyn (oraz jego wartość) gdy program zamyka blok. Identyfikatory zadeklarowane w funkcji bez powiązania mają również automatyczny czas magazynowania.

Następujące reguły określają, czy identyfikator ma globalny (statyczny) lub lokalny (automatyczny) okres istnienia:

- Wszystkie funkcje mają statyczny okres istnienia. Dlatego istnieją cały czas podczas wykonywania programu. Identyfikatory zadeklarowane na poziomie zewnętrznym (czyli na zewnątrz wszystkich bloków w programie, na tym samym poziomie co definicje funkcji) zawsze mają globalne (statyczne) okresy istnienia.

- Jeśli zmienna lokalna ma inicjator, zmienna jest inicjowana za każdym razem, gdy jest tworzony (chyba że jest zadeklarowany jako **`static`** ). Parametry funkcji mają również lokalne okresy istnienia. Możesz określić globalny okres istnienia identyfikatora w bloku, dołączając **`static`** specyfikator klasy magazynu w swojej deklaracji. Po zadeklarowaniu **`static`** zmienna zachowuje swoją wartość z jednego wpisu bloku do następnego.

Chociaż identyfikator z globalnym okresem istnienia istnieje w trakcie wykonywania programu źródłowego (na przykład zmienna zadeklarowana zewnętrznie lub zmienna lokalna zadeklarowana za pomocą **`static`** słowa kluczowego), może nie być widoczna we wszystkich częściach programu. Zobacz [zakres i widoczność](../c-language/scope-and-visibility.md) informacji o widoczności i zobacz [klasy magazynu](../c-language/c-storage-classes.md) w celu omówienia nieterminalu *specyfikatora klasy magazynu* .

Pamięć może być przydzielenia w razie potrzeby (dynamicznie), jeżeli użytkownik użyje specjalnie utworzonej biblioteki procedur, takiej jak `malloc`. Ponieważ dynamiczna alokacja pamięci używa biblioteki procedur, nie uważa się tego za część języka. Zobacz funkcja [malloc](../c-runtime-library/reference/malloc.md) w *dokumentacji dotyczącej biblioteki wykonawczej*.

## <a name="see-also"></a>Zobacz także

[Okres istnienia, zakres, widoczność i połączenie](../c-language/lifetime-scope-visibility-and-linkage.md)
