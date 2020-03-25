---
title: Błąd kompilatora C3813
ms.date: 11/04/2016
f1_keywords:
- C3813
helpviewer_keywords:
- C3813
ms.assetid: ffdbc489-71bf-4cd6-988c-f824c9ab3ceb
ms.openlocfilehash: c16ce501e25040a7ac7672a9ea131b4fe89570f5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165616"
---
# <a name="compiler-error-c3813"></a>Błąd kompilatora C3813

Deklaracja właściwości może wystąpić tylko w definicji typu zarządzanego lub WinRT

[Właściwość](../../dotnet/how-to-use-properties-in-cpp-cli.md) może być zadeklarowana tylko w typie zarządzanym lub środowisko wykonawcze systemu Windows. Typy natywne nie obsługują słowa kluczowego `property`.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3813 i pokazuje, jak to naprawić:

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
