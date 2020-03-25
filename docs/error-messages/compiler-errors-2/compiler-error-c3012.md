---
title: Błąd kompilatora C3012
ms.date: 11/04/2016
f1_keywords:
- C3012
helpviewer_keywords:
- C3012
ms.assetid: cc7040b1-b3fb-4da6-a474-877914d30332
ms.openlocfilehash: 69f0544815804e9827631be81bf9735a95bd1a22
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80176705"
---
# <a name="compiler-error-c3012"></a>Błąd kompilatora C3012

> "*wewnętrzna*": wewnętrzna funkcja nie jest dozwolona bezpośrednio w ramach równoległego regionu

Funkcja [wewnętrzna kompilatora](../../intrinsics/compiler-intrinsics.md) nie jest dozwolona w regionie `omp parallel`. Aby rozwiązać ten problem, Przenieś wewnętrzne elementy z regionu lub zastąp je odpowiednikami niewewnętrznym.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3012 i pokazuje jeden ze sposobów rozwiązania tego problemu:

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
