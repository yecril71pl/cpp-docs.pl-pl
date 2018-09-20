---
title: A.19 przykłady pokazujące nieprawidłowe zagnieżdżanie dyrektyw podziału pracy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 906e900d-9259-44d6-a095-c1ba9135d269
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3cf9502fd17fced7a4bc2a208634b825443f196a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46411524"
---
# <a name="a19---examples-showing-incorrect-nesting-of-work-sharing-directives"></a>A.19   Przykłady pokazujące nieprawidłowe zagnieżdżanie dyrektyw podziału pracy

Przykłady w tej sekcji przedstawiają dyrektywy reguły zagnieżdżenia. Aby uzyskać więcej informacji na temat zagnieżdżanie dyrektywy, zobacz [2.9 sekcji](../../parallel/openmp/2-9-directive-nesting.md) na stronie 33.

Poniższy przykład jest niezgodne ponieważ wewnętrznych i zewnętrznych `for` dyrektywy są gnieżdżone i powiązania do tej samej `parallel` dyrektywy:

```
void wrong1(int n)
{
  #pragma omp parallel default(shared)
  {
      int i, j;
      #pragma omp for
      for (i=0; i<n; i++) {
          #pragma omp for
              for (j=0; j<n; j++)
                 work(i, j);
     }
   }
}
```

Następująca wersja dynamicznie zagnieżdżonych powyższego przykładu jest również niezgodne:

```
void wrong2(int n)
{
  #pragma omp parallel default(shared)
  {
    int i;
    #pragma omp for
      for (i=0; i<n; i++)
        work1(i, n);
  }
}

void work1(int i, int n)
{
  int j;
  #pragma omp for
    for (j=0; j<n; j++)
      work2(i, j);
}
```

Poniższy przykład jest niezgodne ponieważ `for` i `single` dyrektywy są zagnieżdżone, a następnie powiązać ten sam równoległego regionu:

```
void wrong3(int n)
{
  #pragma omp parallel default(shared)
  {
    int i;
    #pragma omp for
      for (i=0; i<n; i++) {
        #pragma omp single
          work(i);
      }
  }
}
```

Poniższy przykład jest niezgodne ponieważ `barrier` dyrektywy wewnątrz `for` może doprowadzić do zakleszczenia:

```
void wrong4(int n)
{
  #pragma omp parallel default(shared)
  {
    int i;
    #pragma omp for
      for (i=0; i<n; i++) {
        work1(i);
        #pragma omp barrier
        work2(i);
      }
  }
}
```

Poniższy przykład jest niezgodne ponieważ `barrier` skutkuje zakleszczenie z faktu, że tylko jeden wątek jednocześnie można wprowadzić sekcję krytyczną:

```
void wrong5()
{
  #pragma omp parallel
  {
    #pragma omp critical
    {
       work1();
       #pragma omp barrier
       work2();
    }
  }
}
```

Poniższy przykład jest niezgodne ponieważ `barrier` skutkuje zakleszczenie z faktu, że tylko jeden wątek wykonuje `single` sekcji:

```
void wrong6()
{
  #pragma omp parallel
  {
    setup();
    #pragma omp single
    {
      work1();
      #pragma omp barrier
      work2();
    }
    finish();
  }
}
```