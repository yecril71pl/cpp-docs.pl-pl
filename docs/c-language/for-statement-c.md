---
title: for — instrukcja (C)
ms.date: 11/04/2016
helpviewer_keywords:
- for keyword [C]
ms.assetid: 560a8de4-19db-4868-9f18-dbe51b17900d
ms.openlocfilehash: 91675fbe15ec6abf5aae4548990d9b4e0703e967
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229730"
---
# <a name="for-statement-c"></a>for — instrukcja (C)

**`for`** Instrukcja umożliwia powtarzanie instrukcji lub złożonej instrukcji określoną liczbę razy. Treść **`for`** instrukcji jest wykonywana zero lub więcej razy do momentu, gdy opcjonalny warunek stanie się fałszywy. Można użyć opcjonalnych wyrażeń w **`for`** instrukcji, aby inicjować i zmieniać wartości podczas **`for`** wykonywania instrukcji.

## <a name="syntax"></a>Składnia

*iteracja — instrukcja*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`for`****(** *instrukcja* *init-Expression*<sub>opt</sub> **;** *cond-expression*<sub>opt</sub> **;** *wyrażenie pętli-Expression*<sub>opt</sub> **)**

Wykonanie **`for`** instrukcji przebiega w następujący sposób:

1. *Wyrażenie init-*(jeśli istnieje) jest oceniane. Ta wartość określa inicjalizację pętli. Nie ma ograniczeń dotyczących typu elementu *init-Expression*.

1. *Wyrażenie cond (* Jeśli istnieje) jest oceniane. To wyrażenie musi mieć typ arytmetyczny lub wskaźnikowy. Jest on oceniany przed każdą iteracją. Możliwe są trzy wyniki:

   - Jeśli *cond-expression* jest **`true`** (niezerowe), *instrukcja* jest wykonywana, a następnie *wyrażenie pętli*, jeśli istnieje, jest oceniane. *Wyrażenie pętli* jest oceniane po każdej iteracji. Nie ma ograniczeń dla tego typu. Efekty uboczne zostaną wykonane w pożądanej kolejności. Następnie proces rozpoczyna się ponownie z oceną *cond-expression*.

   - Jeśli *cond-expression* zostanie pominięte, *wyrażenie cond-expression* jest uznawane za prawdziwe, a wykonywanie jest wykonywane dokładnie zgodnie z opisem w poprzednim akapicie. **`for`** Instrukcja bez argumentu *cond-expression* kończy się tylko wtedy, gdy jest **`break`** **`return`** wykonywana instrukcja or w treści instrukcji lub gdy **`goto`** zostanie wykonana instrukcja (do etykiety na zewnątrz **`for`** treści instrukcji).

   - Jeśli *cond-expression* jest **`false`** (0), wykonywanie **`for`** instrukcji kończy się i kontrola przechodzi do następnej instrukcji w programie.

**`for`** Instrukcja kończy również działanie **`break`** , gdy **`goto`** **`return`** jest wykonywana instrukcja,, lub w treści instrukcji. **`continue`** Instrukcja w **`for`** pętli powoduje *wyrażenie pętli* , które ma zostać obliczone. Gdy **`break`** instrukcja jest wykonywana wewnątrz **`for`** pętli, *wyrażenie pętli* nie jest oceniane ani wykonywane. Ta instrukcja

```C
for( ; ; )
```

jest to niestandardowy sposób tworzenia pętli nieskończonej, która może zostać zakończona tylko przy użyciu **`break`** **`goto`** instrukcji,, lub **`return`** .

## <a name="example"></a>Przykład

Ten przykład ilustruje **`for`** instrukcję:

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
