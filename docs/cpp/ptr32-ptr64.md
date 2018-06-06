---
title: __ptr32 i __ptr64 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __ptr32_cpp
- __ptr64_cpp
dev_langs:
- C++
helpviewer_keywords:
- __ptr64 keyword [C++]
- _ptr32 keyword [C++]
- ptr32 keyword [C++]
- ptr64 keyword [C++]
- _ptr64 keyword [C++]
- __ptr32 keyword [C++]
ms.assetid: afb563d8-7458-4fe7-9c30-bd4b5385a59f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5746c8f54a51e24bad23dcb66f6648266e2e4b56
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704818"
---
# <a name="ptr32-ptr64"></a>__ptr32, __ptr64

**Microsoft Specific**

`__ptr32` reprezentuje wskaźnik natywny w systemie 32-bitowy, podczas gdy `__ptr64` reprezentuje wskaźnik natywny w 64-bitowym systemie.

Poniższy przykład przedstawia sposób zadeklarować każdego z tych typów wskaźnika:

```cpp
int * __ptr32 p32;
int * __ptr64 p64;
```

 W systemie 32-bitowy, wskaźnik zadeklarowana z `__ptr64` został obcięty do wskaźnika 32-bitowych. W systemie 64-bitowym, wskaźnik zadeklarowana z `__ptr32` jest traktowany jak wskaźnik 64-bitowych.

> [!NOTE]
> Nie można użyć `__ptr32` lub `__ptr64` podczas kompilowania za pomocą **/CLR: pure**. W przeciwnym razie zostanie wygenerowany C2472 błąd kompilatora. **/CLR: pure** i **/CLR: Safe** — opcje kompilatora są używane w programie Visual Studio 2015 i nieobsługiwane w programie Visual Studio 2017 r.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak można zadeklarować i przydzielić wskaźników za pomocą `__ptr32` i `__ptr64` słów kluczowych.

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

**KOŃCOWY określonych firmy Microsoft**

## <a name="see-also"></a>Zobacz także

- [Typy podstawowe](../cpp/fundamental-types-cpp.md)