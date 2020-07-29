---
title: Błąd kompilatora C3409
ms.date: 11/06/2018
f1_keywords:
- C3409
helpviewer_keywords:
- C3409
ms.assetid: e372d9fa-230c-4b28-b6d3-6ad81ccf9dbb
ms.openlocfilehash: 0bf8b918f254c05bfe57034e25611c8dc17a783a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231965"
---
# <a name="compiler-error-c3409"></a>Błąd kompilatora C3409

> pusty blok atrybutu jest niedozwolony

## <a name="remarks"></a>Uwagi

Nawiasy kwadratowe zostały zinterpretowane przez kompilator jako blok [atrybutu](../../windows/attributes-alphabetical-reference.md) , ale nie znaleziono żadnych atrybutów.

Kompilator może generować ten błąd w przypadku używania nawiasów kwadratowych jako części definicji wyrażenia lambda. Ten błąd występuje, gdy kompilator nie może określić, czy nawiasy kwadratowe są częścią definicji wyrażenia lambda lub bloku atrybutu. Aby uzyskać więcej informacji na temat wyrażeń lambda, zobacz [lambda Expressions](../../cpp/lambda-expressions-in-cpp.md).

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Jeśli nawiasy kwadratowe są częścią bloku atrybutu:

   1. Podaj jeden lub więcej atrybutów w bloku atrybutu.

   1. Usuń blok atrybutu.

1. Jeśli nawiasy kwadratowe są częścią wyrażenia lambda, upewnij się, że wyrażenie lambda jest zgodne z prawidłowymi regułami składni.

   Aby uzyskać więcej informacji na temat składni wyrażenia lambda, zobacz [składnia wyrażenia lambda](../../cpp/lambda-expression-syntax.md).

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

Poniższy przykład generuje C3409, ponieważ wyrażenie lambda używa **`mutable`** specyfikacji, ale nie dostarcza listy parametrów. Kompilator nie może określić, czy nawiasy kwadratowe są częścią definicji wyrażenia lambda lub bloku atrybutu.

```cpp
// C3409b.cpp

int main()
{
   [] mutable {}();
}
```

## <a name="see-also"></a>Zobacz także

[przypisane](../../windows/attributes-alphabetical-reference.md)<br/>
[Wyrażenia lambda](../../cpp/lambda-expressions-in-cpp.md)<br/>
[Składnia wyrażenia lambda](../../cpp/lambda-expression-syntax.md)
