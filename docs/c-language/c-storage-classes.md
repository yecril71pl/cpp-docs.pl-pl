---
title: Klasy magazynu w języku C | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- static variables, lifetime
- storage classes
- lifetime, variables
- specifiers, storage class
- storage class specifiers, C storage classes
- storage duration
ms.assetid: 893fb929-f7a9-43dc-a0b3-29cb1ef845c1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 089f2298cac21ac9fff0d25a76e9393cddb84bba
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32386073"
---
# <a name="c-storage-classes"></a>Klasy magazynu w języku C
"Klasy magazynu" zmiennej, która określa, czy element ma "globalny" lub "local" okresu istnienia. C wymaga tych dwóch okresy "statyczna" i "Automatyczny". Element globalny okres istnienia istnieje i ma wartość podczas wykonywania programu. Wszystkie funkcje istnienia globalnego.  
  
 Automatyczne zmienne lub zmienne lokalne okresy są przydzielane nowego magazynu, każdy czas wykonywania formant przekazuje do bloku, w którym są zdefiniowane. Po powrocie z wykonywania zmienne już istotnych wartości.  
  
 C zapewnia następujące specyfikatory klasy magazynowania:  
  
## <a name="syntax"></a>Składnia  
 *storage-class-specifier*:  
 **auto**  
  
 **register**  
  
 **static**  
  
 **extern**  
  
 **Element TypeDef**  
  
 **__declspec** ( *rozszerzony decl — modyfikator seq* ) / * Specific firmy Microsoft \*/  
  
 Z wyjątkiem `__declspec`, można użyć tylko jednego *Specyfikator klasy magazynu* w *Specyfikator deklaracji* w deklaracji. Jeśli brak specyfikacji klasy magazynowania, deklaracje w bloku Utwórz automatyczny obiektów.  
  
 Zadeklarowane elementy z **automatycznie** lub **zarejestrować** specyfikator okresy istnienia lokalnego. Zadeklarowane elementy z **statycznych** lub `extern` specyfikator okresy istnienia globalnego.  
  
 Ponieważ `typedef` i `__declspec` semantycznie różnią się od innych cztery *Specyfikator klasy magazynu* terminale, jest omówiona osobno. Aby uzyskać szczegółowe informacje na `typedef`, zobacz [deklaracje Typedef](../c-language/typedef-declarations.md). Aby uzyskać szczegółowe informacje na `__declspec`, zobacz [rozszerzone atrybuty klasy magazynu](../c-language/c-extended-storage-class-attributes.md).  
  
 Umieszczanie deklaracje zmiennych i funkcji w plikach źródłowych dotyczy również klasy magazynu i widoczności. Deklaracje poza wszystkie definicje funkcji są określane jako pojawiają się na poziomie"zewnętrzne." Deklaracje w definicjach funkcji są wyświetlane na poziomie"wewnętrzny."  
  
 Dokładne znaczenie poszczególnych Specyfikator klasy magazynu zależy od dwa składniki:  
  
-   Określa, czy deklaracja jest wyświetlany na poziomie zewnętrznym lub wewnętrznym  
  
-   Określa, czy element został zadeklarowany jest zmiennej lub funkcji  
  
 [Specyfikatory klasy magazynowania dla deklaracji na poziomie zewnętrznym](../c-language/storage-class-specifiers-for-external-level-declarations.md) i [specyfikatory klasy magazynowania dla deklaracji na poziomie wewnętrznym](../c-language/storage-class-specifiers-for-internal-level-declarations.md) opisano *Specyfikator klasy magazynu* terminali w Każdy rodzaj deklaracji oraz wyjaśniono domyślne zachowanie podczas *Specyfikator klasy magazynu* pominięto w zmiennej. [Specyfikatory klasy magazynowania z deklaracjami funkcji](../c-language/storage-class-specifiers-with-function-declarations.md) omówiono specyfikatory klasy magazynowania używane z funkcjami.  
  
## <a name="see-also"></a>Zobacz też  
 [Deklaracje i typy](../c-language/declarations-and-types.md)