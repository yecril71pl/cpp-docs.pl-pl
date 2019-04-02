---
title: Błąd kompilatora C3363
ms.date: 11/04/2016
f1_keywords:
- C3363
helpviewer_keywords:
- C3363
ms.assetid: 41aa922f-608e-4f7a-ba66-451fc1161935
ms.openlocfilehash: eca598233dbe4cae4730e952b45945653ec8ffaa
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58775507"
---
# <a name="compiler-error-c3363"></a>Błąd kompilatora C3363

"type": "typeid" można stosować tylko do typu

[Typeid](../../extensions/typeid-cpp-component-extensions.md) operator zostało niepoprawnie użyte.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3363.

```
// C3363.cpp
// compile with: /clr
int main() {
   System::typeid;   // C3363
}
```