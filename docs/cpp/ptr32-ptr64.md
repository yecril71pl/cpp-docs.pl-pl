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
ms.openlocfilehash: 0e979ed51f9c34700cef75113018c23e69a304f9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62244466"
---
# <a name="ptr32-ptr64"></a>__ptr32, __ptr64

**Microsoft Specific**

**__ptr32** reprezentuje wskaźnik natywny w systemie 32-bitowy, podczas gdy **__ptr64** reprezentuje wskaźnik natywny w systemie 64-bitowych.

Poniższy przykład pokazuje sposób deklarowania każdy z tych typów wskaźnika:

```cpp
int * __ptr32 p32;
int * __ptr64 p64;
```

W systemie 32-bitowe, wskaźnik jest zadeklarowany za pomocą **__ptr64** jest obcinana do wskaźnika 32-bitowego. W systemie 64-bitowy wskaźnik jest zadeklarowany za pomocą **__ptr32** jest traktowany jak wskaźnika 64-bitowego.

> [!NOTE]
> Nie można użyć **__ptr32** lub **__ptr64** podczas kompilowania za pomocą **/CLR: pure**. W przeciwnym razie zostanie wygenerowany błąd kompilatora C2472. **/CLR: pure** i **/CLR: Safe** opcje kompilatora są przestarzałe w programie Visual Studio 2015 i obsługiwane w programie Visual Studio 2017.

W celu zgodności z poprzednimi wersjami **_ptr32** i **_ptr64** są synonimy **__ptr32** i **__ptr64** chyba że — opcja kompilatora [/Za \(Wyłącz rozszerzenia językowe)](../build/reference/za-ze-disable-language-extensions.md) jest określony.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje sposób deklarowania i przydzielania wskaźników za pomocą **__ptr32** i **__ptr64** słów kluczowych.

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

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Typy podstawowe](../cpp/fundamental-types-cpp.md)