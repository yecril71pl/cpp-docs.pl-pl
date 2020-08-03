---
title: Specyfikatory typu danych i odpowiedniki
ms.date: 11/04/2016
helpviewer_keywords:
- type specifiers [C++], list
- widening integers
- data types [C++], equivalents
- sign-extending integral types
- zero-extending
- identifiers, data type
- data types [C++], specifiers
- simple types, names
- type names [C++], simple
ms.assetid: 0d4b515a-4f68-4786-83cf-a5d43c7cb6f3
ms.openlocfilehash: cc8ba746bea7f6ea885beb625de414d83367b53f
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/03/2020
ms.locfileid: "87520684"
---
# <a name="data-type-specifiers-and-equivalents"></a>Specyfikatory typu danych i odpowiedniki

Ta książka zazwyczaj używa formularzy specyfikatorów typu wymienionych w poniższej tabeli, a nie w postaci długich, i zakłada, że **`char`** Typ jest podpisany domyślnie. W związku z tym, w tej książce, **`char`** jest równoważne **`signed char`** .

## <a name="type-specifiers-and-equivalents"></a>Specyfikatory typów i równoważne

| Specyfikator typu | Równoważne |
|--|--|
| **`signed char`**<sup>jedno</sup> | **`char`** |
| **`signed int`** | **`signed`**, **`int`** |
| **`signed short int`** | **`short`**, **`signed short`** |
| **`signed long int`** | **`long`**, **`signed long`** |
| **`unsigned char`** | — |
| **`unsigned int`** | **`unsigned`** |
| **`unsigned short int`** | **`unsigned short`** |
| **`unsigned long int`** | **`unsigned long`** |
| **`float`** | — |
| **`long double`**<sup>dwóch</sup> | — |

<sup>1</sup> w przypadku wybrania **`char`** typu bez znaku domyślnie (przez określenie **`/J`** opcji kompilatora) nie można skrócić **`signed char`** **`char`** .

<sup>2</sup> w 32-bitowych i 64-bitowych systemach operacyjnych kompilator języka Microsoft C mapuje **`long double`** do typu **`double`** .

**Specyficzne dla firmy Microsoft**

Możesz określić **`/J`** opcję kompilatora, aby zmienić domyślny **`char`** Typ z **`signed char`** na **`unsigned char`** . Gdy ta opcja jest stosowana, **`char`** oznacza to samo, co **`unsigned char`** , i musisz użyć **`signed`** słowa kluczowego, aby zadeklarować wartość znaku ze znakiem. Jeśli **`char`** wartość jest zadeklarowana jawnie **`signed`** , ta **`/J`** opcja nie ma wpływu na tę opcję, a wartość jest podpisywany po rozszerzeniu do **`int`** typu. **`char`** Typ ma wartość zero-Extended, gdy zostanie rozszerzony do **`int`** typu.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Specyfikatory typu C](../c-language/c-type-specifiers.md)
