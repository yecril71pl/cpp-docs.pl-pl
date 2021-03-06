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
ms.openlocfilehash: 4f793e8485628faf0a80445ce0414835e3b71d1f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217171"
---
# <a name="c-storage-classes"></a>Klasy magazynu w języku C

"Klasa magazynu" zmiennej określa, czy element ma okres istnienia "globalny", czy "lokalny". C wywołuje te dwa okresy istnienia "static" i "Automatic". Element z globalnym okresem istnienia istnieje i ma wartość w trakcie wykonywania programu. Wszystkie funkcje mają globalne okresy istnienia.

Zmienne automatyczne lub zmienne z lokalnymi okresami istnienia są przypisywanych nowych magazynów po każdym przekroczeniu przez Sterowanie wykonywaniem do bloku, w którym są zdefiniowane. Po powrocie wykonywania zmienne nie mają już wartości znaczących.

C zawiera następujące specyfikatory klasy magazynowania:

## <a name="syntax"></a>Składnia

*specyfikator klasy magazynu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`auto`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`register`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`static`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`extern`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`typedef`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`__declspec (`***Extended-decl-modyfikator-SEQ* **`)`**  / \* Specyficzne dla firmy Microsoft\*/

Z wyjątkiem dla **`__declspec`** , można użyć tylko jednego *specyfikatora klasy magazynu* w deklaracji *-specyfikatora deklaracji* . Jeśli nie zostanie utworzona Specyfikacja klasy magazynu, deklaracje w bloku tworzą obiekty automatyczne.

Elementy zadeklarowane ze **`auto`** **`register`** specyfikatorem or mają lokalne okresy istnienia. Elementy zadeklarowane ze **`static`** **`extern`** specyfikatorem or mają globalne okresy istnienia.

Ponieważ **`typedef`** i **`__declspec`** są semantycznie inne niż pozostałe cztery końce *specyfikatora klasy magazynu* , są one omawiane osobno. Aby uzyskać szczegółowe informacje na temat **`typedef`** , zobacz [ `typedef` deklaracje](../c-language/typedef-declarations.md). Aby uzyskać szczegółowe informacje na temat **`__declspec`** , zobacz [atrybuty klasy magazynu rozszerzonego](../c-language/c-extended-storage-class-attributes.md).

Umieszczenie deklaracji zmiennej i funkcji w plikach źródłowych wpływa również na klasę i widoczność magazynu. Deklaracje poza wszystkimi definicjami funkcji są wyświetlane na stronie "poziom zewnętrzny". Deklaracje w ramach definicji funkcji są wyświetlane na "poziomie wewnętrznym".

Dokładne znaczenie każdego specyfikatora klasy magazynu zależy od dwóch czynników:

- Czy deklaracja pojawia się na poziomie zewnętrznym, czy wewnętrznym

- Czy zadeklarowany element jest zmienną lub funkcją

[Specyfikatory klasy magazynowania dla deklaracji na poziomie zewnętrznym](../c-language/storage-class-specifiers-for-external-level-declarations.md) i [specyfikatory klasy magazynowania dla deklaracji na poziomie wewnętrznym](../c-language/storage-class-specifiers-for-internal-level-declarations.md) opisują terminale *specyfikatora klasy magazynu* w każdym rodzaju deklaracji i objaśniają zachowanie domyślne, gdy *specyfikator klasy magazynu* został pominięty ze zmiennej. [Specyfikatory klasy magazynowania z deklaracjami funkcji](../c-language/storage-class-specifiers-with-function-declarations.md) omawiają specyfikatory klasy magazynu używane z funkcjami.

## <a name="see-also"></a>Zobacz także

[Deklaracje i typy](../c-language/declarations-and-types.md)
