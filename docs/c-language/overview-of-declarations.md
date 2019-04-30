---
title: Przegląd deklaracji
ms.date: 11/04/2016
helpviewer_keywords:
- declarations, about declarations
- type qualifiers
ms.assetid: fcd2364c-c2a5-4fbf-9027-19dac4144cb5
ms.openlocfilehash: 439bc878bbcd1c9778fb74738cb3b32b908a5943
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "64343201"
---
# <a name="overview-of-declarations"></a>Przegląd deklaracji

"Deklaracją" Określa interpretacji i atrybuty zestaw identyfikatorów. Deklaracja, która również powoduje, że magazyn, które mają zostać zarezerwowane do obiektu lub funkcji o nazwie określonej przez identyfikator nazywa się "definition". Deklaracje języka C dla zmiennych, funkcji i typów ma następującej składni:

## <a name="syntax"></a>Składnia

*Deklaracja*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers* *attribute-seq*<sub>opt</sub> *init-declarator-list*<sub>opt</sub>**;**

/\* *Atrybut seq*<sub>zoptymalizowany pod kątem</sub> zależy od firmy Microsoft * /

*Specyfikatory deklaracji*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Storage-class-specifier* *specyfikatory deklaracji*<sub>zoptymalizowany pod kątem</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Specyfikator typu* *specyfikatory deklaracji*<sub>zoptymalizowany pod kątem</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Kwalifikator typu* *specyfikatory deklaracji*<sub>zoptymalizowany pod kątem</sub>

*init-declarator-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-declarator-list* **,** *init-declarator*

*init-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarator* **=** *inicjatora*

> [!NOTE]
> Ta składnia *deklaracji* nie jest powtarzany w poniższych sekcjach. Składnia w poniższych sekcjach zwykle zaczyna się od *deklaratora* nieterminalnych.

Deklaracje w *init-declarator-list* zawierają identyfikatory o nazwie; *init* jest skrótem dla inicjatora. *Init-declarator-list* jest rozdzielaną przecinkami sekwencję deklaratorów, z których każdy może mieć informacji o typie dodatkowe i/lub inicjatora. *Deklaratora* zawiera identyfikatory, jeśli został zadeklarowany. *Specyfikatory deklaracji* nieterminalnych składa się z sekwencji specyfikatorów typ i Klasa magazynu, które wskazują na powiązania, czas trwania przechowywania i jest częścią typu jednostki, które wyznaczają deklaratory. W związku z tym deklaracje składają się z kombinacji specyfikatory klasy magazynowania, specyfikatory typu, typu kwalifikatorów, deklaratory i inicjatory.

Deklaracje może zawierać jeden lub więcej z opcjonalnych atrybutów na liście *atrybutu seq*; *seq* jest skrótem sekwencji. Te atrybuty specyficzne dla firmy Microsoft wykonywania różnych funkcji, które opisano szczegółowo w tym podręczniku.

W formularzu ogólne deklaracji zmiennej *Specyfikator typu* zawiera typ danych zmiennej. *Specyfikator typu* mogą być złożone, jako gdy typ został zmodyfikowany przez **const** lub `volatile`. `declarator` Nadaje nazwę zmiennej, prawdopodobnie zmodyfikowana, aby zadeklarować tablicę lub typ wskaźnika. Na przykład

```C
int const *fp;
```

deklaruje zmienną o nazwie `fp` jako wskaźnik do niemodyfikowalnymi (**const**) `int` wartość. Można zdefiniować więcej niż jednej zmiennej w deklaracji, za pomocą wiele deklaratorów, oddzielonych przecinkami.

Deklaracja musi mieć co najmniej jednego deklaratora, lub jego specyfikatora typu, należy zadeklarować tag struktury, złożenia tag lub elementów członkowskich wyliczenia. Deklaratory Podaj wszelkie pozostałe informacje na temat identyfikatora. Deklarator jest identyfikatorem, który może być modyfikowany w nawiasach kwadratowych (**[**), gwiazdki (<strong>\*</strong>), lub nawiasy ( **()** ) do tablicy, wskaźnika, lub Funkcja typu odpowiednio. Przy deklarowaniu zmiennych prostych (takie jak znak, liczba całkowita i zmiennoprzecinkowa elementów), lub struktur i Unii proste zmiennych `declarator` jest po prostu identyfikatorem. Aby uzyskać więcej informacji dotyczących deklaratorów, zobacz [deklaratory i deklaracje zmiennych](../c-language/declarators-and-variable-declarations.md).

Wszystkie definicje są niejawnie deklaracji, ale nie wszystkie deklaracje definicje. Na przykład deklaracji zmiennych, które zaczynają się od `extern` Specyfikator klasy składującej "odwołują się do," zamiast "Definiowanie" deklaracji. Jeśli zewnętrznej zmiennej jest określane zanim zostanie on zdefiniowany lub jest on zdefiniowany w innym pliku źródłowym z jednego miejsca jest używany, `extern` deklaracja jest to konieczne. Magazyn nie jest przydzielany przez "" deklaracje odwołaniowe, nie można zainicjować zmienne w deklaracji.

Klasa magazynu lub typu (lub obie) jest wymagany w deklaracjach zmiennych. Z wyjątkiem `__declspec`, tylko jeden — Specyfikator klasy magazynowania jest dozwolone w deklaracji i nie wszystkie specyfikatory klasy magazynowania są dozwolone w każdym kontekście. `__declspec` Klasa magazynu jest dozwolona z innych specyfikatorów klasy magazynowania i może on więcej niż jeden raz. Specyfikator klasy składującej deklaracji wpływa na sposób przechowywania i zainicjować element zadeklarowany i części programu, które mogą odwoływać się do elementu.

*Storage-class-specifier* obejmują terminale zdefiniowany w języku C **automatycznie**, `extern`, **zarejestrować**, **statyczne**i `typedef`. Ponadto Microsoft C zawiera *storage-class-specifier* terminalu `__declspec`. Wszystkie *storage-class-specifier* terminali z wyjątkiem `typedef` i `__declspec` zostały omówione w [klasy magazynu](../c-language/c-storage-classes.md). Zobacz [deklaracje Typedef](../c-language/typedef-declarations.md) uzyskać informacji na temat `typedef`. Zobacz [rozszerzone atrybuty klasy magazynowania](../c-language/c-extended-storage-class-attributes.md) uzyskać informacji na temat `__declspec`.

Lokalizacja deklaracji w ramach programu źródłowego i obecności lub braku innych deklaracji zmiennej są niezwykle ważne przy określaniu okres istnienia zmiennych. Może to być redeclarations wiele, ale tylko jedną definicję. Jednak definicję może znajdować się w więcej niż jednej jednostce translacji. Obiekty z wewnętrznym powiązaniem stosowana ta reguła oddzielnie każdą jednostkę translacji, ponieważ wewnętrznie połączone obiekty są unikatowe dla jednostki translacji. W przypadku obiektów za pomocą zewnętrznego powiązania ta reguła ma zastosowanie do całego programu. Zobacz [okres istnienia, zakres, widoczność i powiązania](../c-language/lifetime-scope-visibility-and-linkage.md) uzyskać więcej informacji o widoczności.

Specyfikatory typu podanie pewnych informacji o typach danych identyfikatorów. Domyślny Specyfikator typu jest `int`. Aby uzyskać więcej informacji, zobacz [specyfikatory typu](../c-language/c-type-specifiers.md). Specyfikatory typu można również zdefiniować tagi typów, struktury i nazw składników union oraz stałe wyliczeń. Aby uzyskać więcej informacji, zobacz [deklaracje modułów Wyliczających](../c-language/c-enumeration-declarations.md), [deklaracje struktur](../c-language/structure-declarations.md), i [deklaracje złożeń](../c-language/union-declarations.md).

Istnieją dwa *kwalifikator typu* terminale: **const** i `volatile`. Kwalifikatory określić dodatkowe właściwości typów, które mają zastosowanie tylko wtedy, gdy dostęp do obiektów tego typu za pośrednictwem l wartościami. Aby uzyskać więcej informacji na temat **const** i `volatile`, zobacz [kwalifikatory typów](../c-language/type-qualifiers.md). Aby uzyskać pełną definicję l wartości, zobacz [wyrażenia wartości L i r](../c-language/l-value-and-r-value-expressions.md).

## <a name="see-also"></a>Zobacz także

[Podsumowanie dotyczące składni języka C](../c-language/c-language-syntax-summary.md)<br/>
[Deklaracje i typy](../c-language/declarations-and-types.md)<br/>
[Podsumowanie deklaracji](../c-language/summary-of-declarations.md)
