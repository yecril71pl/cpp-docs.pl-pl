---
title: Błąd kompilatora C3384
ms.date: 11/04/2016
f1_keywords:
- C3384
helpviewer_keywords:
- C3384
ms.assetid: c9f92c6a-62a9-4333-b2b1-bc55c7f288b6
ms.openlocfilehash: 059518462bd7a0463fd03fec6434acbbda7ee60a
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756438"
---
# <a name="compiler-error-c3384"></a>Błąd kompilatora C3384

"type_parameter": ograniczenie wartości i ograniczenie ref wzajemnie się wykluczają

Nie można ograniczyć typu ogólnego do `value class` i `ref class`.

Aby uzyskać więcej informacji, zobacz [ograniczeniaC++dotyczące parametrów typu ogólnego (/CLI)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md) .

## <a name="example"></a>Przykład

Poniższy przykład generuje C3384.

```cpp
// C3384.cpp
// compile with: /c /clr
generic <typename T>
where T : ref class
where T : value class   // C3384
ref class List {};
```
