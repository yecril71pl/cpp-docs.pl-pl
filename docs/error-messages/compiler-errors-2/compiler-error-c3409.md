---
title: Compiler Error C3409
ms.date: 11/06/2018
f1_keywords:
- C3409
helpviewer_keywords:
- C3409
ms.assetid: e372d9fa-230c-4b28-b6d3-6ad81ccf9dbb
ms.openlocfilehash: a4d9271153618fab47a8b5b9cb11b2a5eed35230
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58769306"
---
# <a name="compiler-error-c3409"></a>Compiler Error C3409

> pusty blok atrybutu nie jest dozwolone.

## <a name="remarks"></a>Uwagi

Nawiasy kwadratowe są interpretowane przez kompilator jako [atrybut](../../windows/attributes-alphabetical-reference.md) znaleziono blok, ale żadne atrybuty.

Kompilator może wygenerować tego błędu, korzystając z nawiasami kwadratowymi jako część definicji wyrażenia lambda. Ten błąd występuje, gdy kompilator nie może określić, czy nawiasy kwadratowe są częścią definicji wyrażenia lambda lub bloku atrybutu. Aby uzyskać więcej informacji na temat wyrażeń lambda, zobacz [wyrażeń Lambda](../../cpp/lambda-expressions-in-cpp.md).

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Jeśli nawiasy kwadratowe są częścią blokiem atrybutu:

   1. Należy podać jeden lub więcej atrybutów w bloku attribute.

   1. Usuń blok atrybutu.

1. Jeśli nawiasy kwadratowe są częścią wyrażenia lambda, upewnij się, że wyrażenie lambda regułom prawidłowej składni.

   Aby uzyskać więcej informacji na temat składni wyrażeń lambda, zobacz [Lambda Expression Syntax](../../cpp/lambda-expression-syntax.md).

## <a name="example"></a>Przykład

Poniższy przykład generuje C3409.

```cpp
// C3409.cpp
// compile with: /c
#include <windows.h>
[]   // C3409
class a {};

// OK
[object, uuid("00000000-0000-0000-0000-000000000000")]
__interface x {};

[coclass, uuid("00000000-0000-0000-0000-000000000001")]
class b : public x {};
```

## <a name="example"></a>Przykład

Poniższy przykład generuje C3409, ponieważ korzysta z wyrażenia lambda `mutable` specyfikacji, ale nie zapewnia listę parametrów. Kompilator nie może określić, czy nawiasy kwadratowe są częścią definicji wyrażenia lambda lub bloku atrybutu.

```cpp
// C3409b.cpp

int main()
{
   [] mutable {}();
}
```

## <a name="see-also"></a>Zobacz też

[attribute](../../windows/attributes-alphabetical-reference.md)<br/>
[Wyrażenia lambda](../../cpp/lambda-expressions-in-cpp.md)<br/>
[Składnia wyrażenia lambda](../../cpp/lambda-expression-syntax.md)