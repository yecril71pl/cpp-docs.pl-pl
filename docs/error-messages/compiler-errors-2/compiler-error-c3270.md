---
title: Błąd kompilatora C3270 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3270
dev_langs:
- C++
helpviewer_keywords:
- C3270
ms.assetid: 70e6e76b-7415-48f5-a61e-2ed50caf08e4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9c421ee1efa56e7f7e9a9444bafa15d392a78ae3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46053495"
---
# <a name="compiler-error-c3270"></a>Błąd kompilatora C3270

"field": atrybut FieldOffset należy używać tylko w kontekście StructLayout(Explicit), w tym przypadku jest wymagana

Pole zostało oznaczone **FieldOffset**, który jest dozwolony tylko w przypadku **StructLayout(Explicit)** jest aktywna.

Poniższy przykład spowoduje wygenerowanie C3270:

```
// C3270_2.cpp
// compile with: /clr /c
using namespace System::Runtime::InteropServices;

[ StructLayout(LayoutKind::Sequential) ]
// try the following line instead
// [ StructLayout(LayoutKind::Explicit) ]
public value struct MYUNION
{
   [FieldOffset(0)] int a;   // C3270
   // ...
};
```
