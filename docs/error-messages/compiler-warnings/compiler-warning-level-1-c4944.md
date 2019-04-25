---
title: Kompilator ostrzeżenie (poziom 1) C4944
ms.date: 11/04/2016
f1_keywords:
- C4944
helpviewer_keywords:
- C4944
ms.assetid: e2905eb1-2e3b-4fab-a48b-c0cae0fd997f
ms.openlocfilehash: 0c58a438f4e2c1437e1038b6087d57f47db30775
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62301997"
---
# <a name="compiler-warning-level-1-c4944"></a>Kompilator ostrzeżenie (poziom 1) C4944

'symbol': nie można zaimportować symbolu z "assembly1": ponieważ "symbol" już istnieje w bieżącym zakresie

Symbol został zdefiniowany w pliku kodu źródłowego i następnie # instrukcję using odwołanie do zestawu zdefiniowanego symbolu. Symbol w zestawie jest ignorowany.

## <a name="example"></a>Przykład

Poniższy przykład tworzy składnik o typie o nazwie ClassA.

```
// C4944.cs
// compile with: /target:library
// C# source code to create a dll
public class ClassA {
   public int i;
}
```

## <a name="example"></a>Przykład

Poniższe przykłady Generowanie C4944.

```
// C4944b.cpp
// compile with: /clr /W1
class ClassA {
public:
   int u;
};

#using "C4944.dll"   // C4944 ClassA also defined C4944.dll

int main() {
   ClassA * x = new ClassA();
   x->u = 9;
   System::Console::WriteLine(x->u);
}
```