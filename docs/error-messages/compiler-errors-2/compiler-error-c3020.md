---
title: Błąd kompilatora C3020 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3020
dev_langs:
- C++
helpviewer_keywords:
- C3020
ms.assetid: f625c7a3-afaa-4bd8-9c1b-51891b832f36
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4c7f86d116c1a830db54490f3e5231d837d4246c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46060646"
---
# <a name="compiler-error-c3020"></a>Błąd kompilatora C3020

"var": zmienna index OpenMP pętli "for" nie może być modyfikowana w ciele pętli

OpenMP `for` pętli nie mogą być modyfikowane indeksu (licznika pętli) w treści `for` pętli.

Poniższy przykład spowoduje wygenerowanie C3020:

```
// C3020.cpp
// compile with: /openmp
int main() {
   int i = 0, n = 3;

   #pragma omp parallel
   {
      #pragma omp for
      for (i = 0; i < 10; i += n)
         i *= 2;   // C3020
         // try the following line instead
         // n++;
   }
}
```

Zmienna zadeklarowana ze [lastprivate](../../parallel/openmp/reference/lastprivate.md) nie można użyć jako indeks wewnątrz pętli, równoległego.

Poniższy przykład zapewni C3020 dla drugiego lastprivate, ponieważ ten lastprivate wyzwoli zapisu idx_a w najbardziej zewnętrznej pętli for. Pierwszy lastprivate nie wyświetli błąd, ponieważ tego lastprivate wyzwala zapisu idx_a poza najbardziej zewnętrzna dla pętli (z technicznego punktu widzenia. na końcu w ostatniej iteracji). Poniższy przykład spowoduje wygenerowanie C3020.

```
// C3020b.cpp
// compile with: /openmp /c
float a[100][100];
int idx_a, idx_b;
void test(int first, int last)
{
   #pragma omp parallel for lastprivate(idx_a)
   for (idx_a = first; idx_a <= last; ++idx_a) {
      #pragma omp parallel for lastprivate(idx_a)   // C3020
      for (idx_b = first; idx_b <= last; ++idx_b) {
         a[idx_a][idx_b] += 1.0f;
      }
   }
}
```

W poniższym przykładzie pokazano możliwe rozwiązania:

```
// C3020c.cpp
// compile with: /openmp /c
float a[100][100];
int idx_a, idx_b;
void test(int first, int last)
{
   #pragma omp parallel for lastprivate(idx_a)
   for (idx_a = first; idx_a <= last; ++idx_a) {
      #pragma omp parallel for lastprivate(idx_b)
      for (idx_b = first; idx_b <= last; ++idx_b) {
         a[idx_a][idx_b] += 1.0f;
      }
   }
}
```