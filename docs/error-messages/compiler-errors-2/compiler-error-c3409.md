---
title: Błąd kompilatora C3409 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3409
dev_langs:
- C++
helpviewer_keywords:
- C3409
ms.assetid: e372d9fa-230c-4b28-b6d3-6ad81ccf9dbb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 338a98adb45ee9fc8eb392853a5693d10a171940
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46058838"
---
# <a name="compiler-error-c3409"></a>Błąd kompilatora C3409

pusty blok atrybutu nie jest dozwolone.

Nawiasy kwadratowe są interpretowane przez kompilator jako [atrybut](../../windows/cpp-attributes-reference.md) znaleziono blok, ale żadne atrybuty.

Kompilator może wygenerować tego błędu, korzystając z nawiasami kwadratowymi jako część definicji wyrażenia lambda. Ten błąd występuje, gdy kompilator nie może określić, czy nawiasy kwadratowe są częścią definicji wyrażenia lambda lub bloku atrybutu. Aby uzyskać więcej informacji na temat wyrażeń lambda, zobacz [wyrażeń Lambda](../../cpp/lambda-expressions-in-cpp.md).

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Jeśli nawiasy kwadratowe są częścią blokiem atrybutu:

   1. Należy podać jeden lub więcej atrybutów w bloku attribute.

   1. Usuń blok atrybutu.

1. Jeśli nawiasy kwadratowe są częścią wyrażenia lambda:

   1. Upewnij się, że wyrażenie lambda regułom prawidłowej składni.

         Aby uzyskać więcej informacji na temat składni wyrażeń lambda, zobacz [Lambda Expression Syntax](../../cpp/lambda-expression-syntax.md).

    2.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3409.

```
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

```
// C3409b.cpp

int main()
{
   [] mutable {}();
}
```

## <a name="see-also"></a>Zobacz też

[attribute](../../windows/cpp-attributes-reference.md)<br/>
[Wyrażenia lambda](../../cpp/lambda-expressions-in-cpp.md)<br/>
[Składnia wyrażenia lambda](../../cpp/lambda-expression-syntax.md)