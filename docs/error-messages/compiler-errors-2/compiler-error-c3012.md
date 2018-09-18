---
title: Błąd kompilatora C3012 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3012
dev_langs:
- C++
helpviewer_keywords:
- C3012
ms.assetid: cc7040b1-b3fb-4da6-a474-877914d30332
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 99bdac5ffb75978479ae7ef420a48b3d1b2f8e64
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46063674"
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