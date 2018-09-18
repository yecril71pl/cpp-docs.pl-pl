---
title: Błąd kompilatora C2725 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2725
dev_langs:
- C++
helpviewer_keywords:
- C2725
ms.assetid: 13cd5b1b-e906-4cd8-9b2b-510d587c665a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 969ddd9343073dff3732204eb4b17375bb5ab9cc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46056043"
---
# <a name="compiler-error-c2725"></a>Błąd kompilatora C2725

"exception": nie można zgłosić lub przechwycić zarządzanej lub obiektu WinRT przez wartość lub odwołanie

Typ zarządzany lub WinRT wyjątku nie jest poprawny.

## <a name="example"></a>Przykład

Poniższy przykład generuje C2725 i pokazuje, jak go naprawić.

```
// C2725.cpp
// compile with: /clr
ref class R {
public:
   int i;
};

int main() {
   R % r1 = *gcnew R;
   throw r1;   // C2725

   R ^ r2 = gcnew R;
   throw r2;   // OK
}
```

## <a name="example"></a>Przykład

Poniższy przykład generuje C2725 i pokazuje, jak go naprawić.

```
// C2725b.cpp
// compile with: /clr
using namespace System;
int main() {
   try {}
   catch( System::Exception%) {}   // C2725
   // try the following line instead
   // catch( System::Exception ^e) {}
}
```
