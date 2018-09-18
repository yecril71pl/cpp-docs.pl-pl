---
title: __alignof operator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- alignas_cpp
- __alignof_cpp
- alignof_cpp
dev_langs:
- C++
helpviewer_keywords:
- alignas [C++]
- alignment of structures
- __alignof keyword [C++]
- alignof [C++]
- types [C++], alignment requirements
ms.assetid: acb1eed7-6398-40bd-b0c5-684ceb64afbc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ffea0fdf40f7ef794563849f97b0b68631b9734e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099788"
---
# <a name="alignof-operator"></a>Operator __alignof

C ++ 11 wprowadza **alignof** operator, który zwraca wyrównanie, w bajtach dla określonego typu. Dla uzyskania maksymalnej przenośności należy użyć operatora alignof zamiast operator __alignof specyficzne dla firmy Microsoft.

**Microsoft Specific**

Zwraca wartość typu `size_t` czyli wymóg wyrównania tego typu.

## <a name="syntax"></a>Składnia

```cpp
  __alignof( type )
```

## <a name="remarks"></a>Uwagi

Na przykład:

|Wyrażenie|Wartość|
|----------------|-----------|
|**__alignof (char)**|1|
|**__alignof (krótki)**|2|
|**__alignof (int)**|4|
|**__alignof ( \__int64)**|8|
|**__alignof (zmiennoprzecinkowego)**|4|
|**__alignof (podwójny)**|8|
|**__alignof (char\* )**|4|

**__Alignof** wartość jest taka sama jak wartość `sizeof` dla typów podstawowych. Rozważmy jednak, w tym przykładzie:

```cpp
typedef struct { int a; double b; } S;
// __alignof(S) == 8
```

W tym przypadku **__alignof** wartość jest wymóg wyrównania największego elementu w strukturze.

Podobnie Aby uzyskać

```cpp
typedef __declspec(align(32)) struct { int a; } S;
```

`__alignof(S)` jest równa `32`.

Jednym z zastosowań **__alignof** byłoby jako parametr do jednego z własnych procedur alokacji pamięci. Na przykład, biorąc pod uwagę następujące zdefiniowana struktura `S`, może wywołać procedurę alokacji pamięci o nazwie `aligned_malloc` można przydzielić pamięci na granicy określonego wyrównania.

```cpp
typedef __declspec(align(32)) struct { int a; double b; } S;
int n = 50; // array size
S* p = (S*)aligned_malloc(n * sizeof(S), __alignof(S));
```

Aby uzyskać więcej informacji na temat modyfikowania wyrównania zobacz:

- [pakiet](../preprocessor/pack.md)

- [align](../cpp/align-cpp.md)

- [__unaligned](../cpp/unaligned.md)

- [/Zp (Wyrównanie składowej struktury)](../build/reference/zp-struct-member-alignment.md)

- [Przykłady wyrównania struktury](../build/examples-of-structure-alignment.md) — x64 określonych 64

Aby uzyskać więcej informacji na temat różnic w wyrównania w kodzie x86 i x64 zobacz:

- [Konflikty z kompilatorem x86](../build/conflicts-with-the-x86-compiler.md)

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Wyrażenia z operatorami jednoargumentowymi](../cpp/expressions-with-unary-operators.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)