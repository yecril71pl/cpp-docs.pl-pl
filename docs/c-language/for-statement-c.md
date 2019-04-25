---
title: for — instrukcja (C)
ms.date: 11/04/2016
helpviewer_keywords:
- for keyword [C]
ms.assetid: 560a8de4-19db-4868-9f18-dbe51b17900d
ms.openlocfilehash: df00bcab2f9f9e51a6f37e19670b6cd240fa5cc4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62233647"
---
# <a name="for-statement-c"></a>for — instrukcja (C)

**Dla** instrukcji umożliwia powtarzanie instrukcję lub instrukcja złożona określoną liczbę razy. Treść **dla** instrukcja jest wykonywana na zero lub więcej razy, aż opcjonalny warunek przestaje być prawdziwy. Można użyć wyrażenia opcjonalny w **dla** instrukcję, aby zainicjować i zmień wartości podczas **dla** wykonywania instrukcji.

## <a name="syntax"></a>Składnia

*instrukcji iteracji*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Aby uzyskać** **(** *init-expression*<sub>zoptymalizowany pod kątem</sub> **;** *cond-expression*<sub>zoptymalizowany pod kątem</sub> **;** *loop-expression*<sub>zoptymalizowany pod kątem</sub> **)** *— instrukcja*

Wykonywanie **dla** instrukcji przechodzi w następujący sposób:

1. *Init-expression*, jeśli istnieje, jest obliczane. To ustawienie określa inicjowania dla pętli. Nie ma żadnych ograniczeń typu *init-expression*.

1. *Cond-expression*, jeśli istnieje, jest obliczane. To wyrażenie musi mieć typ arytmetyczny lub wskaźnika. Jest on oceniane przed każdą iteracją. Możliwe są trzy wyniki:

   - Jeśli *cond-expression* jest **true** (niezerowe), *instrukcji* jest wykonywana; następnie *loop-expression*, jeśli istnieje, jest obliczane. *Loop-expression* jest oceniane po każdej iteracji. Nie ma żadnych ograniczeń dla jego typu. Efekty uboczne będzie wykonywany w kolejności. Następnie rozpocznie się proces ponownie z wersją ewaluacyjną usługi *cond-expression*.

   - Jeśli *cond-expression* zostanie pominięty, *cond-expression* jest traktowane jako PRAWDA, a następnie kontynuowane wykonywanie dokładnie zgodnie z opisem w poprzednim akapicie. A **dla** instrukcję bez *cond-expression* argument kończy się tylko wtedy, gdy **podziału** lub **zwracają** instrukcji wewnątrz instrukcji zawartość jest wykonywana, lub gdy **goto** (do oznaczonej instrukcji poza **dla** treść instrukcji) jest wykonywana.

   - Jeśli *cond-expression* jest **false** (0), wykonywanie **dla** kończy się i przekazuje kontrolę do następnej instrukcji w programie.

A **dla** również kończy się po **podziału**, **goto**, lub **zwracają** zostaje wykonana instrukcja w treści instrukcji. A **nadal** instrukcji w **dla** powoduje, że w pętli *loop-expression* ma zostać obliczone. Gdy **podziału** instrukcja jest wykonywana wewnątrz **dla** pętli, *loop-expression* nie ocenić lub wykonać. Ta instrukcja

```C
for( ; ; )
```

to zwyczajowy sposób, aby wygenerować wejścia w nieskończoną pętlę, która tylko można zakończył działanie ze **podziału**, **goto**, lub **zwracają** instrukcji.

## <a name="example"></a>Przykład

Ten przykład ilustruje **dla** instrukcji:

```C
// c_for.c
int main()
{
   char* line = "H e  \tl\tlo World\0";
   int space = 0;
   int tab = 0;
   int i;
   int max = strlen(line);
   for (i = 0; i < max; i++ )
   {
      if ( line[i] == ' ' )
      {
          space++;
      }
      if ( line[i] == '\t' )
      {
          tab++;
      }
   }

   printf("Number of spaces: %i\n", space);
   printf("Number of tabs: %i\n", tab);
   return 0;
}
```

## <a name="output"></a>Dane wyjściowe

```Output
Number of spaces: 4
Number of tabs: 2
```

## <a name="see-also"></a>Zobacz także

[Instrukcje](../c-language/statements-c.md)
