---
title: Błąd kompilatora C3813
ms.date: 11/04/2016
f1_keywords:
- C3813
helpviewer_keywords:
- C3813
ms.assetid: ffdbc489-71bf-4cd6-988c-f824c9ab3ceb
ms.openlocfilehash: 302b21d709424cda50abd0247f7b82048511cd73
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50470593"
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