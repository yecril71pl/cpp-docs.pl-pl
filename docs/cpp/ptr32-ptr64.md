---
title: __ptr32, __ptr64
ms.date: 10/09/2018
f1_keywords:
- __ptr32_cpp
- __ptr64_cpp
- __ptr32
- __ptr64
- _ptr32
- _ptr64
helpviewer_keywords:
- __ptr64 keyword [C++]
- _ptr32 keyword [C++]
- ptr32 keyword [C++]
- ptr64 keyword [C++]
- _ptr64 keyword [C++]
- __ptr32 keyword [C++]
ms.assetid: afb563d8-7458-4fe7-9c30-bd4b5385a59f
ms.openlocfilehash: 5ff2fa22c8a466252cfaf8b80dc8d56774aff58e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227156"
---
# <a name="__ptr32-__ptr64"></a>__ptr32, __ptr64

**Specyficzne dla firmy Microsoft**

**`__ptr32`** reprezentuje natywny wskaźnik w systemie 32-bitowym, podczas gdy **`__ptr64`** reprezentuje natywny wskaźnik w systemie 64-bitowym.

Poniższy przykład pokazuje, jak zadeklarować każdy z tych typów wskaźnika:

```cpp
int * __ptr32 p32;
int * __ptr64 p64;
```

W przypadku systemu 32-bitowego wskaźnik zadeklarowany z **`__ptr64`** jest obcinany do wskaźnika 32-bitowego. W systemie 64-bitowym wskaźnik zadeklarowany z **`__ptr32`** jest przekształcony na wskaźnik 64-bitowy.

> [!NOTE]
> Nie można użyć **`__ptr32`** lub **`__ptr64`** podczas kompilowania z **/CLR: Pure**. W przeciwnym razie zostanie wygenerowany błąd kompilatora C2472. **/CLR: Pure** i **/CLR:** opcje kompilatora bezpiecznego są przestarzałe w programie Visual Studio 2015 i nieobsługiwane w programie Visual Studio 2017.

W celu zapewnienia zgodności z poprzednimi wersjami **_ptr32** i **_ptr64** są synonimami dla **`__ptr32`** i, **`__ptr64`** chyba że opcja kompilatora [/za \( wyłączenie rozszerzeń języka)](../build/reference/za-ze-disable-language-extensions.md) jest określona.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak zadeklarować i przydzielić wskaźniki przy **`__ptr32`** użyciu **`__ptr64`** słów kluczowych i.

```cpp
#include <cstdlib>
#include <iostream>

int main()
{
    using namespace std;

    int * __ptr32 p32;
    int * __ptr64 p64;

    p32 = (int * __ptr32)malloc(4);
    *p32 = 32;
    cout << *p32 << endl;

    p64 = (int * __ptr64)malloc(4);
    *p64 = 64;
    cout << *p64 << endl;
}
```

```Output
32
64
```

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Typy wbudowane](../cpp/fundamental-types-cpp.md)
