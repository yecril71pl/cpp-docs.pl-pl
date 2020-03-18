---
title: Operator __alignof
ms.date: 12/17/2018
f1_keywords:
- __alignof_cpp
- alignof_cpp
- __alignof
- _alignof
helpviewer_keywords:
- alignas [C++]
- alignment of structures
- __alignof keyword [C++]
- alignof [C++]
- types [C++], alignment requirements
ms.assetid: acb1eed7-6398-40bd-b0c5-684ceb64afbc
ms.openlocfilehash: b3764e95846d48d293991d69d04bc71c6b3aed90
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79443604"
---
# <a name="__alignof-operator"></a>Operator __alignof

W języku c++ 11 wprowadzono operator **alignof** , który zwraca wyrównanie w bajtach określonego typu. W celu uzyskania maksymalnej przenośności należy użyć operatora alignof zamiast operatora __alignof określonego przez firmę Microsoft.

**Specyficzne dla firmy Microsoft**

Zwraca wartość typu `size_t`, która jest wymaganiem wyrównania typu.

## <a name="syntax"></a>Składnia

```cpp
  __alignof( type )
```

## <a name="remarks"></a>Uwagi

Na przykład:

|Wyrażenie|Wartość|
|----------------|-----------|
|**__alignof (Char)**|1|
|**__alignof (krótki)**|2|
|**__alignof (int)**|4|
|**__alignof (\__int64)**|8|
|**__alignof (float)**|4|
|**__alignof (Double)**|8|
|**__alignof (\* znak)**|4|

Wartość **__alignof** jest taka sama jak wartość `sizeof` dla typów podstawowych. Należy jednak wziąć pod uwagę następujący przykład:

```cpp
typedef struct { int a; double b; } S;
// __alignof(S) == 8
```

W tym przypadku wartość **__alignof** jest wymaganiem wyrównania największego elementu w strukturze.

Podobnie w przypadku

```cpp
typedef __declspec(align(32)) struct { int a; } S;
```

`__alignof(S)` jest równa `32`.

Jeden z wartości **__alignof** byłby jako parametr do jednej z własnych procedur alokacji pamięci. Na przykład, uwzględniając następującą zdefiniowaną strukturę `S`, można wywołać procedurę alokacji pamięci o nazwie `aligned_malloc`, aby przydzielić pamięć na określonej granicy wyrównania.

```cpp
typedef __declspec(align(32)) struct { int a; double b; } S;
int n = 50; // array size
S* p = (S*)aligned_malloc(n * sizeof(S), __alignof(S));
```

W celu zapewnienia zgodności z poprzednimi wersjami **_alignof** jest synonimem dla **__alignof** , chyba że opcja kompilatora [/za \(Wyłącz rozszerzenia językowe)](../build/reference/za-ze-disable-language-extensions.md) .

Aby uzyskać więcej informacji na temat modyfikowania wyrównania, zobacz:

- [pakiet](../preprocessor/pack.md)

- [align](../cpp/align-cpp.md)

- [__unaligned](../cpp/unaligned.md)

- [/Zp (Wyrównanie składowej struktury)](../build/reference/zp-struct-member-alignment.md)

- [Przykłady wyrównania struktury](../build/x64-software-conventions.md#examples-of-structure-alignment) (specyficzne dla architektury x64)

Aby uzyskać więcej informacji na temat różnic w obrównaniu kodu dla procesorów x86 i x64, zobacz:

- [Konflikty z kompilatorem x86](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[Wyrażenia z operatorami jednoargumentowymi](../cpp/expressions-with-unary-operators.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)