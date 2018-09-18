---
title: Błąd kompilatora C3535 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3535
dev_langs:
- C++
helpviewer_keywords:
- C3535
ms.assetid: 24449c98-f681-484d-a00b-32533dca3a88
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 215fa52f892cb569b32335ca439811eb07b28dc7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46094081"
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

## <a name="see-also"></a>Zobacz też

[Auto, słowo kluczowe](../../cpp/auto-keyword.md)<br/>
[Typy podstawowe](../../cpp/fundamental-types-cpp.md)