---
title: __ptr32, __ptr64 | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 050317be4c5f933ca9e08055a02555f5597c583c
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39406536"
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