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
ms.openlocfilehash: 759a2ee50f047fbd5777481d009332be998ad359
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33688807"
---
# <a name="2726-reduction"></a>2.7.2.6 — redukcja

Klauzulę wykonuje zmniejszenie na zmienne skalarne, które są widoczne w *zmiennej listy*, z operatorem *op*. Składnia `reduction` klauzuli wygląda następująco:

> redukcja (*op*: *zmiennej listy*)

Zmniejszenie jest zazwyczaj określana dla instrukcji z jednym z następujących formatów:

> *x* = *x* *op* *wyrażenie*  
> *x* *binop* = *wyrażenie*  
> *x* = *wyrażenie* *op* *x* (z wyjątkiem odejmowania)  
> *x*++  
> ++*x*  
> *x*--  
> --*x*  

gdzie:

*x*  
Jeden z zmienne redukcji określone w `list`.

*variable-list*  
Rozdzielana przecinkami lista zmienne redukcji skalarne.

*expr*  
Wyrażenie typu skalarne nie odwołuje się *x*.

*OP*  
Przeciążony operator NOT oprócz jednego +, &#42;, -, &amp;, ^, &#124;, &amp; &amp;, lub &#124; &#124;.

*binop*  
Przeciążony operator NOT oprócz jednego +, &#42;, -, &amp;, ^, lub &#124;.

Poniżej przedstawiono przykład `reduction` klauzuli:  
  
```cpp  
#pragma omp parallel for reduction(+: a, y) reduction(||: am)  
for (i=0; i<n; i++) {  
   a += b[i];  
   y = sum(y, c[i]);  
   am = am || b[i] == c[i];  
}  
```  
  
Jak pokazano w przykładzie, operator może być ukryty wewnątrz wywołania funkcji. Użytkownik należy zachować ostrożność, że operator określona w `reduction` klauzuli pasuje operacji zmniejszenia.

Mimo że prawy argument operacji &#124; &#124; operator nie ma żadnych efektów ubocznych w tym przykładzie, są dozwolone, ale należy z rozwagą. W tym kontekście efektu ubocznego, który nie może wystąpić w trakcie wykonywania sekwencyjnego pętli mogą wystąpić podczas przetwarzania równoległego. Ta różnica może wystąpić, ponieważ kolejność wykonywania iteracji jest nieokreślony.

Operator służy do określenia początkowej wartości zmiennych prywatnych używany przez kompilator do zmniejszenia oraz ustalenie operator finalizacji. Jawne określenie operator umożliwia instrukcji redukcji przekraczających zakres leksykalne konstrukcji. Dowolną liczbę `reduction` klauzule można określić w dyrektywie, ale zmienna może występować w co najmniej jeden `reduction` klauzula dla tej dyrektywy.

Prywatnej kopii każdej zmiennej w *zmiennej listy* jest tworzony, po jednej dla każdego wątku tak, jakby `private` klauzuli została użyta. Zainicjowano prywatnej kopii zgodnie z operatora (patrz poniższa tabela).

Na koniec regionu, dla którego `reduction` określono klauzulę, oryginalny obiekt jest aktualizowany w celu odzwierciedlenia wynikiem połączenia oryginalnej wartości z końcowej każdej kopii prywatnej przy użyciu operatora określony. Operatory redukcji są wszystkie asocjacyjne (z wyjątkiem odejmowania), a kompilator za darmo ponownie skojarzyć obliczenia wartości końcowej. (Wyniki częściowe zmniejszenie odejmowania są dodawane do formularza końcowej).

Wartość obiektu oryginalnego stają się nieokreślony po pierwszym wątkiem osiągnie klauzuli zawierającego i pozostaje, aż do zakończenia obliczenia zmniejszenie.  Zwykle obliczenia zostanie wykonana na końcu konstrukcji; Jednak jeśli `reduction` na konstrukcję, do której jest używana klauzula `nowait` jest również stosowane wartość obiektu oryginalnego pozostaje nieokreślony dopóki nie przeprowadzono synchronizacji bariery, aby upewnić się, że wszystkie wątki zostały ukończone `reduction`klauzuli.

W poniższej tabeli wymieniono operatory, które są prawidłowe i ich wartości inicjowania kanoniczny. Wartość rzeczywistego inicjowania będzie zgodny z typem danych zmiennej redukcji.

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

- Typ zmiennych w `reduction` klauzuli musi być prawidłowy dla operatorem redukcji z tą różnicą, że typy wskaźników i typy referencyjne nigdy nie są dozwolone.

- Zmienna, która została określona w `reduction` klauzuli nie może być **const**-kwalifikowaną.

- Zmienne, które są prywatne w ramach równoległego regionu lub które są widoczne w `reduction` klauzuli **równoległych** dyrektywy nie można określić w `reduction` klauzuli w dyrektywie podziału pracy, która jest powiązana z konstrukcji równoległych.

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
