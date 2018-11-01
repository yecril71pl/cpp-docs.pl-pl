---
title: Błąd kompilatora C3012
ms.date: 11/04/2016
f1_keywords:
- C3012
helpviewer_keywords:
- C3012
ms.assetid: cc7040b1-b3fb-4da6-a474-877914d30332
ms.openlocfilehash: 9fe0ac7d3637cad3a5571c4631345dac1a0021bb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50503098"
---
# <a name="compiler-error-c3012"></a>Błąd kompilatora C3012

> "*wewnętrzne*": wewnętrzna funkcja nie jest dozwolona bezpośrednio w ramach równoległego regionu

A [wewnętrzne polecenie kompilatora](../../intrinsics/compiler-intrinsics.md) funkcja nie jest dozwolona w `omp parallel` regionu. Aby rozwiązać ten problem, Przenieś funkcje wewnętrzne regionu lub Zastąp ich odpowiedniki — wewnętrzne.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3012 i pokazano jeden ze sposobów, aby rozwiązać ten problem:

```cpp
// C3012.cpp
// compile with: /openmp
#ifdef __cplusplus
extern "C" {
#endif
void* _ReturnAddress();
#ifdef __cplusplus
}
#endif

int main()
{
   #pragma omp parallel
   {
      _ReturnAddress();   // C3012
   }
   _ReturnAddress();      // OK
}
```