---
title: Błąd kompilatora C3798 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3798
dev_langs:
- C++
helpviewer_keywords:
- C3798
ms.assetid: b2f8b1d8-8812-49b8-a346-28e48f02ba5c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 217aa46cdd643361fed16f8a69de7f8ec75214fb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099846"
---
# <a name="compiler-error-c3798"></a>Błąd kompilatora C3798

"specyfikatora": deklaracja właściwości nie może posiadać specyfikatora przesłonięcia (powinna być umieszczona dla właściwości get/set metody zamiast)

Właściwość została zadeklarowana niepoprawnie. Aby uzyskać więcej informacji, zobacz artykuł

- [właściwość](../../windows/property-cpp-component-extensions.md)

- [abstract](../../windows/abstract-cpp-component-extensions.md)

- [sealed](../../windows/sealed-cpp-component-extensions.md)

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3798

```
// C3798.cpp
// compile with: /clr /c
ref struct A {
   property int Prop_1 abstract;   // C3798
   property int Prop_2 sealed;   // C3798

   // OK
   property int Prop_3 {
      virtual int get() abstract;
      virtual void set(int i) abstract;
   }

   property int Prop_4 {
      virtual int get() sealed;
      virtual void set(int i) sealed;
   }
};
```