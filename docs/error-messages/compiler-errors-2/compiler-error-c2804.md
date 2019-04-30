---
title: Błąd kompilatora C2804
ms.date: 11/04/2016
f1_keywords:
- C2804
helpviewer_keywords:
- C2804
ms.assetid: b066e563-cca4-450c-8ba7-3b0d7a89f3ea
ms.openlocfilehash: 1ebcfdc2f2555fa694ab8dfeabe77e5140ddace2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408423"
---
# <a name="compiler-error-c2804"></a>Błąd kompilatora C2804

plik binarny "operator operator" ma zbyt wiele parametrów

Funkcja elementu członkowskiego Przeciążony operator binarny jest zadeklarowana z więcej niż jeden parametr. Pierwszy parametr operand operatora binarnego funkcji członkowskiej, którego typ jest operatorem typ otaczający, jest domyślna.

## <a name="example"></a>Przykład

Poniższy przykład generuje C2804 i pokazuje, jak go naprawić.

```
// C2804.cpp
// compile by using: cl /c /W4 C2804.cpp
class X {
public:
   X& operator+= (const X &left, const X &right);   // C2804
   X& operator+= (const X &right);   // OK - left operand implicitly *this
};

int main() {
   X x, y;
   x += y;   // equivalent to x.operator+=(y)
}
```

## <a name="example"></a>Przykład

Poniższy przykład generuje C2804 i pokazuje, jak go naprawić.

```
// C2804_2.cpp
// compile with: /clr /c
ref struct Y {
   Y^ operator +(Y^ hY, int i);   // C2804
   static Y^ operator +(Y^ hY, int i);   // OK
   Y^ operator +(int i);   // OK
};
```