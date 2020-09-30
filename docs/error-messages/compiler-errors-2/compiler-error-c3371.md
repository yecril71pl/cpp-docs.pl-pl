---
title: Błąd kompilatora C3371
ms.date: 11/04/2016
f1_keywords:
- C3371
helpviewer_keywords:
- C3371
ms.assetid: f7ecf1aa-ed0a-4f73-81e5-62cf98f88ea1
ms.openlocfilehash: f4b4b516c3c06bd575b114da62030c94fcee6806
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91503169"
---
# <a name="compiler-error-c3371"></a>Błąd kompilatora C3371

"idl_module": tylko właściwość "name" jest dozwolona w tym miejscu

[idl_module](../../windows/attributes/idl-module.md) użycie bezpośrednio w deklaracji funkcji nie może mieć żadnych parametrów innych niż nazwa.

Poniższy przykład generuje C3371:

```cpp
// C3371.cpp
[idl_module(name="Name", dllname="Some.dll")];
[idl_module(name="Name", helpstring="Some help")]   // C3371
int f1();
// try
// [idl_module(name="Name")]
// int f1();

int main()
{
}
```
