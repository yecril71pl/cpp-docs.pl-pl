---
title: Błąd kompilatora C3666
ms.date: 11/04/2016
f1_keywords:
- C3666
helpviewer_keywords:
- C3666
ms.assetid: 459e51dd-cefb-4346-99b3-644f2d8b65b2
ms.openlocfilehash: edca117da585fee731041d696e05af1baf6d3e5c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62214987"
---
# <a name="compiler-error-c3666"></a>Błąd kompilatora C3666

"Konstruktor": specyfikator "— słowo kluczowe" nie jest dozwolony na konstruktorze override

Specyfikator przesłonięcia był używany w konstruktorze, a nie jest dozwolone. Aby uzyskać więcej informacji, zobacz [zastąpienie specyfikatorów](../../extensions/override-specifiers-cpp-component-extensions.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3666.

```
// C3666.cpp
// compile with: /clr /c
ref struct R {
   R() new {}   // C3666
   R(int i) {}   // OK
};
```