---
title: Deklaracje wskaźników | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- pointer declarations
- declarations, pointers
- const keyword [C]
- pointers, declarations
ms.assetid: 8b3b7fc7-f44d-480d-b6f9-cebe4e5462a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ca5ef287ad853387635bbcc349374e1f174b4fd6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46095940"
---
# <a name="pointer-declarations"></a>Deklaracje wskaźników

A *deklaracji wskaźnika* nazwy zmiennej wskaźnika i określa typ obiektu, na który wskazuje zmienna. Zmienna zadeklarowana jako wskaźnika przechowuje adres pamięci.

## <a name="syntax"></a>Składnia

*deklarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wskaźnik*<sub>zoptymalizowany pod kątem</sub> *deklaratora bezpośrednie*

*deklarator bezpośrednio*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Identyfikator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**(** *deklaratora* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarator bezpośrednio* **[** *wyrażenie_stałe*<sub>zoptymalizowany pod kątem</sub> **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarator bezpośrednio* **(** *listy parametrów typu* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarator bezpośrednio* **(** *listy identyfikatorów*<sub>zoptymalizowany pod kątem</sub> **)**

*wskaźnik*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong> *Lista typów kwalifikator*<sub>zoptymalizowany pod kątem</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong> *Lista typów kwalifikator*<sub>zoptymalizowany pod kątem</sub> *wskaźnika*

*Lista typów kwalifikator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Kwalifikator typu*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Lista typów kwalifikator* *kwalifikator typu*

*Specyfikator typu* zapewnia typ obiektu, który może być żadnych podstawowych, struktury lub Unii. Zmienne wskaźnik może też wskazywać funkcji, tablice i inne wskaźniki. (Informacje na temat deklarowanie i interpretowanie bardziej złożonych typów wskaźnika, można znaleźć [interpretowanie Deklaratorów bardziej złożonych](../c-language/interpreting-more-complex-declarators.md).)

Podejmując *Specyfikator typu* **void**, można opóźnić Specyfikacja typu, do którego odwołuje się wskaźnik myszy. Taki element jest określany jako "wskaźnik do **void**" i jest zapisywany jako `void *`. Zmienna zadeklarowana jako wskaźnik do *void* można wskazać obiekt dowolnego typu. Jednak do wykonywania większości operacji na wskaźnik lub obiektu, na który wskazuje, typu, na który wskazuje muszą być jawnie określone dla każdej operacji. (Zmienne typu **char** <strong>\*</strong> i typ **void** <strong>\*</strong> są zgodnego przypisania bez typu Rzutowanie.) Takie Konwersja może się odbywać za pomocą typu rzutowanego (zobacz [konwersje rzutowania typów](../c-language/type-cast-conversions.md) Aby uzyskać więcej informacji).

*Kwalifikator typu* może być **const** lub **volatile**, lub obu. Określają one, odpowiednio, czy wskaźnik nie można zmodyfikować przez sam program (**const**), lub który wskaźnik rzeczywiście może być modyfikowany przez niektóre procesy poza kontrolą programu (**volatile**). (Zobacz [kwalifikatory typów](../c-language/type-qualifiers.md) więcej informacji na temat **const** i **volatile**.)

*Deklaratora* nazwy zmiennej i może zawierać modyfikatora typu. Na przykład jeśli *deklaratora* reprezentuje tablicę, typ wskaźnika jest modyfikowany jako wskaźnik do tablicy.

Można zadeklarować wskaźnik do struktury, Unii lub typu wyliczeniowego, przed zdefiniowaniem struktury, Unii lub typ wyliczenia. Możesz zadeklarować wskaźnik przy użyciu tagu struktury lub Unii, jak pokazano w poniższych przykładach. Deklaracje te są dozwolone, ponieważ kompilator nie musi wiedzieć, rozmiar struktury lub Unii, można przydzielić obszaru do zmiennej wskaźnika.

## <a name="examples"></a>Przykłady

Poniższe przykłady ilustrują deklaracje wskaźników.

```
char *message; /* Declares a pointer variable named message */
```

*Komunikat* wskazuje wskaźnik do zmiennej **char** typu.

```
int *pointers[10];  /* Declares an array of pointers */
```

*Wskaźniki* tablica zawiera 10 elementów; każdy element jest wskaźnikiem do zmiennej **int** typu.

```
int (*pointer)[10]; /* Declares a pointer to an array of 10 elements */
```

*Wskaźnik* wskazuje zmienną tablicy o liczbie 10 elementów. Każdy element w tej tablicy ma **int** typu.

```
int const *x;      /* Declares a pointer variable, x,
                      to a constant value */
```

Wskaźnik *x* można modyfikować, aby wskazać inną **int** wartość, ale wartość, na który punktów nie może być modyfikowany.

```
const int some_object = 5 ;
int other_object = 37;
int *const y = &fixed_object;
int volatile *const z = &some_object;
int *const volatile w = &some_object;
```

Zmienna *y* w deklaracjach jest zadeklarowany jako stały wskaźnik do **int** wartość. Można zmodyfikować wartość wskazuje, ale sam wskaźnik zawsze musi wskazywać na tej samej lokalizacji: adres *fixed_object*. Podobnie *z* jest stały wskaźnik, ale wskazują także jest zadeklarowany **int** którego wartość nie można zmodyfikować przez program. Specyfikator dodatkowe **volatile** wskazuje, że mimo że wartość **const int** wskazywany przez *z* nie może być modyfikowana przez program, może rzeczywiście być zmodyfikowane przez proces uruchomiony wątkom program. Deklaracja *w* Określa, że program nie można zmienić wartość wskazywana i że program nie można zmodyfikować wskaźnika.

```
struct list *next, *previous; /* Uses the tag for list */
```

Ten przykład deklaruje dwie zmienne wskaźnika, *dalej* i *poprzedniej*, wskazujące na typ struktury *listy*. Ta deklaracja może następować przed elementem definicji *listy* struktury typu (patrz następny przykład), tak długo, jak *listy* definicji typu ma taką samą widoczność jak deklaracja.

```
struct list
{
    char *token;
    int count;
    struct list *next;
} line;
```

Zmienna *wiersza* ma typ struktury o nazwie *listy*. *Listy* typ struktury ma trzy elementy członkowskie: pierwszy element członkowski jest wskaźnikiem do **char** , druga wartość **int** wartości, a trzeci to wskaźnik do innego *listy* struktury.

```
struct id
{
    unsigned int id_no;
    struct name *pname;
} record;
```

Zmienna *rekordu* ma typ struktury *identyfikator*. Należy pamiętać, że *pname* jest zadeklarowany jako wskaźnik do innego typu struktury o nazwie *nazwa*. Ta deklaracja może następować przed elementem *nazwa* typ jest zdefiniowany.

## <a name="see-also"></a>Zobacz też

[Deklaratory i deklaracje zmiennych](../c-language/declarators-and-variable-declarations.md)