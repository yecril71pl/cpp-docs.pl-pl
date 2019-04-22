---
title: Błąd kompilatora C3535
ms.date: 11/04/2016
f1_keywords:
- C3535
helpviewer_keywords:
- C3535
ms.assetid: 24449c98-f681-484d-a00b-32533dca3a88
ms.openlocfilehash: e80fa62db9795838980c63e113300a554afabef3
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59040864"
---
# <a name="compiler-error-c3535"></a>Błąd kompilatora C3535

Nie można ustalić typu 'Typ1' od 'type2'

Typ zmiennej zadeklarowanej przez `auto` — słowo kluczowe nie można wywnioskować z typu wyrażenia inicjowania. Na przykład ten błąd występuje, jeśli wynikiem obliczenia wyrażenia inicjowania jest `void`, która nie jest typem.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Upewnij się, że typ wyrażenia inicjowania nie `void`.

1. Upewnij się, że deklaracja nie jest wskaźnik do typu podstawowych. Aby uzyskać więcej informacji, zobacz [podstawowych typów](../../cpp/fundamental-types-cpp.md).

1. Upewnij się, że jeśli deklaracja znajduje się wskaźnik do typu wyrażenia inicjowania jest typem wskaźnika.

## <a name="example"></a>Przykład

Poniższy przykład daje C3535, ponieważ daje w wyniku wyrażenia inicjowania `void`.

```
// C3535a.cpp
// Compile with /Zc:auto
void f(){}
int main()
{
   auto x = f();   //C3535
   return 0;
}
```

## <a name="example"></a>Przykład

Poniższy przykład daje C3535, ponieważ instrukcja deklaruje zmienną `x` jako wskaźnik do typu wywnioskowane, ale typ inicjatora wyrażenie jest podwójny. W związku z tym kompilator nie można wywnioskować typu zmiennej.

```
// C3535b.cpp
// Compile with /Zc:auto
int main()
{
   auto* x = 123.0;   // C3535
   return 0;
}
```

## <a name="example"></a>Przykład

Poniższy przykład daje C3535, ponieważ zmienna `p` deklaruje wskaźnik do typu wywnioskowane, ale wyrażenia inicjowania, nie jest typem wskaźnika.

```
// C3535c.cpp
// Compile with /Zc:auto
class A { };
A x;
auto *p = x;  // C3535
```

## <a name="see-also"></a>Zobacz także

[Auto, słowo kluczowe](../../cpp/auto-keyword.md)<br/>
[Typy podstawowe](../../cpp/fundamental-types-cpp.md)