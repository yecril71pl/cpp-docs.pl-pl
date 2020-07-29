---
title: Operator alignof
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
ms.openlocfilehash: 6a2046774674858211ae89abb9b4cfc7b09c0a6d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227637"
---
# <a name="alignof-operator"></a>Operator alignof

**`alignof`** Operator zwraca wyrównanie w bajtach określonego typu jako wartość typu **`size_t`** .

## <a name="syntax"></a>Składnia

```cpp
alignof( type )
```

## <a name="remarks"></a>Uwagi

Na przykład:

| Wyrażenie | Wartość |
|--|--|
| **`alignof( char )`** | 1 |
| **`alignof( short )`** | 2 |
| **`alignof( int )`** | 4 |
| **`alignof( long long )`** | 8 |
| **`alignof( float )`** | 4 |
| **`alignof( double )`** | 8 |

**`alignof`** Wartość jest taka sama jak wartość dla **`sizeof`** typów podstawowych. Należy jednak wziąć pod uwagę następujący przykład:

```cpp
typedef struct { int a; double b; } S;
// alignof(S) == 8
```

W tym przypadku **`alignof`** wartość jest wymaganiem wyrównania największego elementu w strukturze.

Podobnie w przypadku

```cpp
typedef __declspec(align(32)) struct { int a; } S;
```

`alignof(S)`jest równe `32` .

Jeden z nich **`alignof`** może być parametrem do jednej z własnych procedur alokacji pamięci. Na przykład przy użyciu następującej zdefiniowanej struktury `S` można wywołać procedurę alokacji pamięci o nazwie, `aligned_malloc` Aby przydzielić pamięć na określonej granicy wyrównania.

```cpp
typedef __declspec(align(32)) struct { int a; double b; } S;
int n = 50; // array size
S* p = (S*)aligned_malloc(n * sizeof(S), alignof(S));
```

Aby uzyskać więcej informacji na temat modyfikowania wyrównania, zobacz:

- [pakiet](../preprocessor/pack.md)

- [dostosowania](../cpp/align-cpp.md)

- [__unaligned](../cpp/unaligned.md)

- [/ZP (wyrównanie składowej struktury)](../build/reference/zp-struct-member-alignment.md)

- [Przykłady wyrównania struktury](../build/x64-software-conventions.md#examples-of-structure-alignment) (specyficzne dla architektury x64)

Aby uzyskać więcej informacji na temat różnic w obrównaniu kodu dla procesorów x86 i x64, zobacz:

- [Konflikty z kompilatorem x86](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)

### <a name="microsoft-specific"></a>specyficzne dla firmy Microsoft

**`alignof`** i **`__alignof`** są synonimami w kompilatorze firmy Microsoft. Zanim stanie się częścią standardu języka C++ 11, operator specyficzny dla firmy Microsoft **`__alignof`** udostępnił tę funkcję. W celu uzyskania maksymalnej przenośności należy użyć **`alignof`** operatora zamiast operatora specyficznego dla firmy Microsoft **`__alignof`** .

W celu zapewnienia zgodności z poprzednimi wersjami, **`_alignof`** jest synonimem, **`__alignof`** Jeśli opcja kompilatora [ `/Za` \( disable rozszerzenia języka](../build/reference/za-ze-disable-language-extensions.md) nie jest określona.

## <a name="see-also"></a>Zobacz także

[Wyrażenia z operatorami jednoargumentowymi](../cpp/expressions-with-unary-operators.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)
