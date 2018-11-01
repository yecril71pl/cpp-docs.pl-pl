---
title: Klasy magazynu w języku C
ms.date: 08/31/2018
helpviewer_keywords:
- static variables, lifetime
- storage classes
- lifetime, variables
- specifiers, storage class
- storage class specifiers, C storage classes
- storage duration
ms.assetid: 893fb929-f7a9-43dc-a0b3-29cb1ef845c1
ms.openlocfilehash: cb472ea0db67e0fd8d7f2a8e2af4513ffb0fbe1c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50466186"
---
# <a name="c-storage-classes"></a>Klasy magazynu w języku C

"Klasa magazynu" zmiennej określa, czy element ma okres istnienia "global" lub "local". C wywołuje te dwa okresy istnienia "statyczne" i "Automatyczny". Element z globalnym okresem istnienia istnieje i ma wartość podczas wykonywania programu. Wszystkie funkcje mają globalne okresy istnienia.

Automatyczne zmienne lub zmienne lokalne okresy istnienia, są przydzielane nowego magazynu, każdy czas wykonywania kontrola przechodzi do bloku, w którym są zdefiniowane. Po powrocie wykonywania, zmiennych już istotne wartości.

C, oferuje następujące specyfikatory klasy magazynowania:

## <a name="syntax"></a>Składnia

*storage-class-specifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Automatycznie**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Zarejestruj się**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Statyczne**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**extern**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Element TypeDef**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__declspec (** *extended-decl modyfikator seq* **)**  / \* Specific firmy Microsoft \*/

Z wyjątkiem `__declspec`, można użyć tylko jednej *storage-class-specifier* w *Specyfikator deklaracji* w deklaracji. Jeśli nie specyfikacja klasy magazynowania, deklaracje w bloku tworzenia obiektów automatycznych.

Elementy zadeklarowane za pomocą **automatycznie** lub **zarejestrować** specyfikator okresy istnienia lokalnego. Elementy zadeklarowane za pomocą **statyczne** lub `extern` specyfikator okresy istnienia globalnego.

Ponieważ `typedef` i `__declspec` są semantycznie różne od innych cztery *storage-class-specifier* terminali, zostały omówione oddzielnie. Aby uzyskać szczegółowe informacje dotyczące `typedef`, zobacz [deklaracje Typedef](../c-language/typedef-declarations.md). Aby uzyskać szczegółowe informacje dotyczące `__declspec`, zobacz [rozszerzone atrybuty klasy magazynowania](../c-language/c-extended-storage-class-attributes.md).

Położenie deklaracje zmiennych i funkcji w obrębie pliki źródłowe wpływa również na klasę magazynu i widoczności. Deklaracje poza wszystkie definicje funkcji są określane jako pojawiają się na poziomie"zewnętrzne." Deklaracje w obrębie definicje funkcji są wyświetlane na poziomie"wewnętrzny."

Dokładne znaczenie każdy Specyfikator klasy magazynowania zależy od dwa czynniki:

- Czy deklaracja jest wyświetlane na poziomie zewnętrznym lub wewnętrznym

- Czy element został zadeklarowany jest zmienna lub funkcja

[Specyfikatory klasy magazynowania dla deklaracji na poziomie zewnętrznym](../c-language/storage-class-specifiers-for-external-level-declarations.md) i [specyfikatory klasy magazynowania dla deklaracji na poziomie wewnętrznym](../c-language/storage-class-specifiers-for-internal-level-declarations.md) opisują *storage-class-specifier* terminali w Każdy rodzaj elementu deklaracji i wyjaśnić zachowanie domyślne podczas *storage-class-specifier* pominięto w zmiennej. [Specyfikatory klasy magazynowania z deklaracjami funkcji](../c-language/storage-class-specifiers-with-function-declarations.md) opisano specyfikatory klasy magazynowania używana z usługą functions.

## <a name="see-also"></a>Zobacz też

[Deklaracje i typy](../c-language/declarations-and-types.md)
