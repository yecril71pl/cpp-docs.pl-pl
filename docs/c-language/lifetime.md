---
title: Okres istnienia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b1030bf3f0ef907f3904bca92da4e43646d0e1a8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32387486"
---
# <a name="lifetime"></a>Okres istnienia
„Okres istnienia” jest okresem podczas wykonywania programu, w którym istnieje zmienna lub funkcja. Czas magazynowania identyfikatora określa jego okres istnienia.  
  
 Identyfikator zadeklarowana z *Specyfikator klasy magazynu* **statycznych** ma statycznym okresem magazynu. Identyfikatory z statycznym czasem magazynowania (zwane również „global”) są przechowywane i mają zdefiniowaną wartość na czas trwania programu. Magazyn jest zarezerwowany i wartość przechowywana identyfikatora jest zainicjowana tylko raz, przed uruchomieniem programu. Identyfikator zadeklarowana z zewnętrznego lub statycznym okresem magazynu ma również połączenie wewnętrzne (zobacz [połączenie](../c-language/linkage.md)).  
  
 Identyfikator zadeklarowana bez **statycznych** Specyfikator klasy składującej ma automatycznym okresem magazynu, jeśli jest on zadeklarowany jako wewnątrz funkcji. Identyfikator z czasem automatycznego przechowywania („identyfikator lokalny”) posiada magazyn i zdefiniowaną wartością tylko w bloku, w którym został zdefiniowany lub zadeklarowany identyfikator. Nowy magazyn jest każdorazowo przydzielany automatycznemu identyfikatorowi, program wchodzi do tego bloku, a następnie traci swój magazyn (oraz jego wartość) gdy program zamyka blok. Identyfikatory zadeklarowane w funkcji bez powiązania mają również automatyczny czas magazynowania.  
  
 Następujące reguły określają, czy identyfikator ma globalny (statyczny) lub lokalny (automatyczny) okres istnienia:  
  
-   Wszystkie funkcje mają statyczny okres istnienia. Dlatego istnieją cały czas podczas wykonywania programu. Identyfikatory zadeklarowane na poziomie zewnętrznym (czyli na zewnątrz wszystkich bloków w programie, na tym samym poziomie co definicje funkcji) zawsze mają globalne (statyczne) okresy istnienia.  
  
-   Jeśli zmienna lokalna ma inicjatora, zmienna jest ustawiana na każdym utworzeniu (o ile nie jest zadeklarowany jako **statycznych**). Parametry funkcji mają również lokalne okresy istnienia. Globalny okres istnienia dla identyfikatora w bloku można określić, umieszczając w niej **statycznych** Specyfikator klasy magazynu w jego deklaracji. Raz zadeklarowany **statycznych**, zmienna przechowuje wartość zapisu bloku do następnego.  
  
 Mimo że identyfikator globalny okres istnienia istnieje podczas wykonywania programu źródłowego (na przykład zewnętrznie zadeklarowana zmienna lub zmienna lokalna zadeklarowana z **statycznych** — słowo kluczowe), mogą nie być widoczne we wszystkich części programu. Zobacz [zakres i widoczność](../c-language/scope-and-visibility.md) informacji o widoczność i zobaczyć [klasy magazynu](../c-language/c-storage-classes.md) omówienie *Specyfikator klasy magazynu* nonterminal.  
  
 Pamięć może być przydzielenia w razie potrzeby (dynamicznie), jeżeli użytkownik użyje specjalnie utworzonej biblioteki procedur, takiej jak `malloc`. Ponieważ dynamiczna alokacja pamięci używa biblioteki procedur, nie uważa się tego za część języka. Zobacz [— funkcja malloc](../c-runtime-library/reference/malloc.md) działać w *odwołanie do biblioteki wykonawczej*.  
  
## <a name="see-also"></a>Zobacz też  
 [Okres istnienia, zakres, widoczność i połączenie](../c-language/lifetime-scope-visibility-and-linkage.md)