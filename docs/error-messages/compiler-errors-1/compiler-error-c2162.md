---
title: Błąd kompilatora C2162
ms.date: 11/04/2016
f1_keywords:
- C2162
helpviewer_keywords:
- C2162
ms.assetid: 34923628-d35e-48ab-9072-b95e3b5f6b45
ms.openlocfilehash: 02c0101324b28ebe548c38c6dc617faaa62315b7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62174786"
---
# <a name="compiler-error-c2162"></a>Błąd kompilatora C2162

Oczekiwany parametr formalny makra

Token po operator tworzenia ciągu (#) nie jest nazwą parametrów formalnych.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C2162:

```
// C2162.cpp
// compile with: /c
#include <stdio.h>

#define print(a) printf_s(b)   // OK
#define print(a) printf_s(#b)    // C2162
```