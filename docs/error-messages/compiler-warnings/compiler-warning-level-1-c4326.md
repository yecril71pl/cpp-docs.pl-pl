---
title: Kompilator ostrzeżenie (poziom 1) C4326 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4326
dev_langs:
- C++
helpviewer_keywords:
- C4326
ms.assetid: d44d2c4e-9456-42d3-b35b-4ba4b2d42ec7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cee18a9ccc807370cf2fb40748939f211a4ba52f
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43211007"
---
# <a name="compiler-warning-level-1-c4326"></a>Kompilator ostrzeżenie (poziom 1) C4326

> zwracany typ "*funkcja*powinien być*type1*"zamiast z"*type2*"

## <a name="remarks"></a>Uwagi

Funkcja zwróciło typ inny niż *type1*. Na przykład za pomocą [/Za](../../build/reference/za-ze-disable-language-extensions.md), **głównego** nie zwrócił **int**.

## <a name="example"></a>Przykład

Poniższy przykład generuje C4326 i pokazuje, jak go naprawić:

```cpp
// C4326.cpp
// compile with: /Za /W1
char main()
{
    // C4326, instead use int main()
}
```