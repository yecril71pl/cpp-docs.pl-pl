---
title: Błąd kompilatora C3902 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3902
dev_langs:
- C++
helpviewer_keywords:
- C3902
ms.assetid: feb3bb29-f836-4d77-ba71-3876f7f4f216
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5998c0836f3adfbf047cc7259b032258a584f272
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46070044"
---
# <a name="compiler-error-c3902"></a>Błąd kompilatora C3902

"Metoda dostępu": Typ ostatniego parametru musi być "type"

Typ ostatniego parametru metody co najmniej jeden zestaw musi być zgodna z typem właściwości. Aby uzyskać więcej informacji, zobacz [właściwość](../../windows/property-cpp-component-extensions.md).

Poniższy przykład spowoduje wygenerowanie C3902:

```
// C3902.cpp
// compile with: /clr /c
using namespace System;
ref class X {
   property String ^Name {
      void set(int);   // C3902
      // try the following line instead
      // void set(String^){}
   }

   property double values[int,int] {
      void set(int, int, float);   // C3902
      // try the following line instead
      // void set(int, int, double){}
   }
};
```