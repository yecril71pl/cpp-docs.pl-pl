---
title: Błąd kompilatora C3470
ms.date: 11/04/2016
f1_keywords:
- C3470
helpviewer_keywords:
- C3470
ms.assetid: 170c7a9d-214d-41b1-8f15-d4a4fc38aaa5
ms.openlocfilehash: 7d6c8627fe0904dd2fe81dd805d8f87bbebf29c7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62173239"
---
# <a name="compiler-error-c3470"></a>Błąd kompilatora C3470

"type": klasa nie może posiadać zarówno indeksatora (właściwość domyślnie indeksowana) i operatora]

Typ nie można zdefiniować zarówno indeksatora domyślny, jak i operatora [].

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3470

```
// C3470.cpp
// compile with: /clr
using namespace System;

ref class R {
public:
   property int default[int] {
      int get(int i) {
         return i+1;
      }
   }

   int operator[](String^ s) { return Convert::ToInt32(s); }   // C3470
};

int main() {
   R ^ r = gcnew R;
   // return r[9] + r["32"] - 42;
}
```