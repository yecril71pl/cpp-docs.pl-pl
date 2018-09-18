---
title: Błąd kompilatora C3657 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3657
dev_langs:
- C++
helpviewer_keywords:
- C3657
ms.assetid: 89a28a18-4c17-43a1-bda6-deb52c32d203
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1462ac1c63104406473fde2c839d490bdfb24c6c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46117039"
---
# <a name="compiler-error-c3657"></a>Błąd kompilatora C3657

destruktory nie można jawnie przesłonić lub być jawnie przesłonięte

Destruktory i finalizatory nie może być jawnie przesłonięte. Aby uzyskać więcej informacji, zobacz [jawne zastępowanie](../../windows/explicit-overrides-cpp-component-extensions.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3657.

```
// C3657.cpp
// compile with: /clr
public ref struct I {
   virtual ~I() { }
   virtual void a();
};

public ref struct D : I {
   virtual ~D() = I::~I {}   // C3657
   virtual void a() = I::a {}   // OK
};
```