---
title: 2.7.2.6 redukcja | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: e7630a15-2978-4dbe-a29b-3a46371a0151
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 05ed97968921692f69f2ff0040ae14dc41ef52b5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46375605"
---
# <a name="2726-reduction"></a>2.7.2.6 — redukcja

Ta klauzula wykonuje zmniejszenie na zmienne skalarne, które pojawiają się w *liście zmiennych*, za pomocą operatora *op*. Składnia `reduction` klauzula jest w następujący sposób:

> redukcja (*op*: *liście zmiennych*)

Ograniczenie jest zazwyczaj określana dla instrukcji przy użyciu jednego z następujących form:

> *x* = *x* *op* *expr*
> *x* *binop* = *expr*
> *x* = *expr* *op* *x* (z wyjątkiem odejmowanie) *x*++
> ++*x*
> *x*--
> --*x*

gdzie:

*x*<br/>
Jedna ze zmiennych redukcji określone w `list`.

*variable-list*<br/>
Rozdzielana przecinkami lista zmiennych redukcja skalaru.

*expr*<br/>
Wyrażenie typowi skalarnemu, który nie odwołuje się *x*.

*OP*<br/>
Nie przeciążonego operatora, ale jeden z +, &#42;, -, &amp;, ^, &#124;, &amp; &amp;, lub &#124; &#124;.

*binop*<br/>
Nie przeciążonego operatora, ale jeden z +, &#42;, -, &amp;, ^, lub &#124;.

Oto przykład `reduction` klauzuli:

```cpp
#pragma omp parallel for reduction(+: a, y) reduction(||: am)
for (i=0; i<n; i++) {
   a += b[i];
   y = sum(y, c[i]);
   am = am || b[i] == c[i];
}
```

Jak pokazano w przykładzie, operator może być ukryta wewnątrz wywołania funkcji. Użytkownik należy zachować ostrożność, że operator określona w `reduction` klauzuli odpowiada operację redukcji.

Mimo że prawy operand &#124; &#124; operator ma żadnych efektów ubocznych, w tym przykładzie, są dozwolone, ale powinna być stosowana z rozwagą. W tym kontekście efekt uboczny, która może nie wystąpić podczas wykonywania sekwencyjnego pętli mogą wystąpić podczas wykonywania równoległego. Różnica ta może być fakt, że kolejność wykonywania iteracji jest nieokreślony.

Operator jest używany do określenia początkowej wartości żadnych zmiennych prywatnego używany przez kompilator do zmniejszenia oraz określeniem operator finalizacji jest zakończona. Jawne określenie operator umożliwia instrukcji redukcji przekraczających zakres leksykalne konstrukcja. Dowolną liczbę `reduction` klauzule mogą być określone dla dyrektywy, ale zmiennej może występować w co najwyżej jeden `reduction` klauzula dla tej dyrektywy.

Prywatną kopię każdej zmiennej w *liście zmiennych* zostanie utworzony, jeden dla każdego wątku, tak jakby `private` została użyta klauzula. Zainicjowano prywatnej kopii zgodnie z operatora (patrz poniższa tabela).

Na koniec region, dla którego `reduction` określono klauzulę, oryginalny obiekt jest aktualizowany w celu odzwierciedlenia wynikiem połączenia oryginalnej wartości z końcowa wartość każdego prywatne kopie za pomocą operatora określono. Operatory redukcji są wszystkie asocjacyjnych (z wyjątkiem odejmowania), a kompilator swobodnie ponownie skojarzyć obliczenie wartości końcowej. (Wyniki częściowe redukcji odejmowania są dodawane do utworzenia końcowej).

Wartość obiektu oryginalnego staje się nieokreślony, gdy pierwszy wątek osiągnie zawierających klauzulę i pozostaje, więc przed zakończeniem obliczania redukcji.  Zwykle obliczeń zostanie wykonana na końcu konstrukcji; Jednak jeśli `reduction` na konstrukcję, do której jest używana klauzula `nowait` jest również stosowane wartości oryginalnego obiektu pozostanie nieokreślone do czasu, aby upewnić się, że wszystkie wątki zostały ukończone zostaławykonanasynchronizacjabarierę`reduction`klauzuli.

W poniższej tabeli wymieniono operatory, które są prawidłowe i ich wartości canonical inicjowania. Wartość rzeczywista inicjalizacji będzie zgodny z typem danych zmiennej redukcji.

|Operator|Inicjalizacja|
|--------------|--------------------|
|+|0|
|&#42;|1|
|-|0|
|&amp;|~0|
|&#124;|0|
|^|0|
|&amp;&amp;|1|
|&#124;&#124;|0|

Ograniczenia do `reduction` klauzuli są następujące:

- Typ zmiennych w `reduction` klauzula musi mieć prawidłowy dla operatorem redukcji, z tą różnicą, że nigdy nie są dozwolone typy wskaźników i odwołań.

- Zmienna, która została określona w `reduction` klauzuli nie może być **const**-kwalifikowaną.

- Zmienne, które są prywatne w ramach równoległego regionu lub które są widoczne w `reduction` klauzuli **równoległe** dyrektywy nie można określić w `reduction` klauzuli w dyrektywie podziału pracy, która jest powiązywana z konstrukcja równoległa.

   ```cpp
   #pragma omp parallel private(y)
   { /* ERROR - private variable y cannot be specified
                in a reduction clause */
      #pragma omp for reduction(+: y)
      for (i=0; i<n; i++)
         y += b[i];
   }

   /* ERROR - variable x cannot be specified in both
              a shared and a reduction clause */
   #pragma omp parallel for shared(x) reduction(+: x)
   ```
