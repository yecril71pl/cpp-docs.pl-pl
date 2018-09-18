---
title: Błąd kompilatora C3813 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3813
dev_langs:
- C++
helpviewer_keywords:
- C3813
ms.assetid: ffdbc489-71bf-4cd6-988c-f824c9ab3ceb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b8984feb5b657c26d2137eb9a3c648f1bcf442bf
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46066274"
---
# <a name="compiler-error-c3813"></a>Błąd kompilatora C3813

Deklaracja właściwości może wystąpić tylko wewnątrz definicji zarządzanej lub typu WinRT

A [właściwości](../../dotnet/how-to-use-properties-in-cpp-cli.md) mogą być deklarowane tylko w zarządzanej lub Windows Runtime typu. Typy natywne nie obsługują `property` — słowo kluczowe.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3813 i pokazuje, jak go naprawić:

```cpp
// C3813.cpp
// compile by using: cl /c /clr C3813.cpp
class A
{
   property int Int; // C3813
};

ref class B
{
   property int Int; // OK - declared within managed type
};
```