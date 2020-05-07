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

Instrukcja **for** umożliwia powtarzanie instrukcji lub złożonej instrukcji określoną liczbę razy. Treść instrukcji **for** jest wykonywana zero lub więcej razy do momentu, gdy opcjonalny warunek stanie się fałszywy. Można użyć opcjonalnych wyrażeń w instrukcji **for** , aby inicjować i zmieniać wartości podczas wykonywania instrukcji **for** .

## <a name="syntax"></a>Składnia

*iteracja — instrukcja*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**for** **(** *instrukcja* *init-Expression*<sub>opt</sub> **;** *cond-expression*<sub>opt</sub> **;** *wyrażenie pętli-Expression*<sub>opt</sub> **)**

Wykonanie instrukcji **for** zostanie przeprowadzone w następujący sposób:

1. *Wyrażenie init-*(jeśli istnieje) jest oceniane. Ta wartość określa inicjalizację pętli. Nie ma ograniczeń dotyczących typu elementu *init-Expression*.

1. *Wyrażenie cond (* Jeśli istnieje) jest oceniane. To wyrażenie musi mieć typ arytmetyczny lub wskaźnikowy. Jest on oceniany przed każdą iteracją. Możliwe są trzy wyniki:

   - Jeśli *cond-expression* jest **prawdziwe** (niezerowe), *instrukcja* jest wykonywana; następnie jest oceniane *wyrażenie Loop*(jeśli istnieje). *Wyrażenie pętli* jest oceniane po każdej iteracji. Nie ma ograniczeń dla tego typu. Efekty uboczne zostaną wykonane w pożądanej kolejności. Następnie proces rozpoczyna się ponownie z oceną *cond-expression*.

   - Jeśli *cond-expression* zostanie pominięte, *wyrażenie cond-expression* jest uznawane za prawdziwe, a wykonywanie jest wykonywane dokładnie zgodnie z opisem w poprzednim akapicie. Instrukcja **for** bez argumentu *cond* kończy się tylko wtedy, gdy jest wykonywana instrukcja **Break** lub **Return** w treści instrukcji lub gdy zostanie wykonane wyrażenie **goto** (do oznaczonej etykietą poza treścią instrukcji **for** ).

   - Jeśli *cond-expression* ma **wartość false** (0), wykonanie instrukcji **for** kończy działanie i kontrola przechodzi do następnej instrukcji w programie.

Instrukcja **for** przerywa również działanie, gdy zostanie wykonana instrukcja **Break**, **goto**lub **Return** w treści instrukcji. Instrukcja **Continue** w pętli **for** powoduje obliczenie *wyrażenia pętli* . Gdy instrukcja **Break** jest wykonywana wewnątrz pętli **for** , *wyrażenie Loop* nie jest oceniane ani wykonywane. Ta instrukcja

```C
for( ; ; )
```

jest to niestandardowy sposób tworzenia pętli nieskończonej, która może zostać zakończona tylko za pomocą instrukcji **Break**, **goto**lub **Return** .

## <a name="example"></a>Przykład

Ten przykład ilustruje instrukcję **for** :

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

## <a name="see-also"></a>Zobacz też

[Instrukcje](../c-language/statements-c.md)
