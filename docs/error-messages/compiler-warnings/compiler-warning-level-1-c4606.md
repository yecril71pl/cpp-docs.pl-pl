---
title: Ostrzeżenie kompilatora (poziom 1) C4606
ms.date: 11/04/2016
f1_keywords:
- C4606
helpviewer_keywords:
- C4606
ms.assetid: c1b45fb6-672b-42eb-9e1c-c67b3e4150d3
ms.openlocfilehash: 9b38e9670157fd15dc7c4b6a96ced7ad40c43e34
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186000"
---
# <a name="compiler-warning-level-1-c4606"></a>Ostrzeżenie kompilatora (poziom 1) C4606

Ostrzeżenie \#pragma: zignorowano element "warning_number"; Ostrzeżenia analizy kodu nie są skojarzone z poziomami ostrzeżeń

W przypadku ostrzeżeń dotyczących analizy kodu tylko `error`, `once`i `default` są obsługiwane przez pragmę [ostrzeżenia](../../preprocessor/warning.md) .

## <a name="example"></a>Przykład

Poniższy przykład generuje C4606.

```cpp
// C4606.cpp
// compile with: /c /W1
#pragma warning(1: 6001)   // C4606
#pragma warning(once: 6001)   // OK
```
