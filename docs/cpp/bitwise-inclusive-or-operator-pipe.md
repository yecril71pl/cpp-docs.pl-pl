---
title: 'Bitowe or włączny operator OR: || Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 06/14/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- bitor
- '|'
dev_langs:
- C++
helpviewer_keywords:
- OR operator [C++], bitwise inclusive
- bitwise operators [C++], OR operator
- inclusive OR operator
- '| operator'
ms.assetid: 4c8a6a68-d828-447d-875a-aedb4ce3aa9a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 75cb922f2bd5cc6da2666a59bd0827b7ec013bf2
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39408720"
---
# <a name="bitwise-inclusive-or-operator-"></a>Bitowe or włączny operator OR: |

## <a name="syntax"></a>Składnia

> *wyrażenie1* **|** *wyrażenie2*

## <a name="remarks"></a>Uwagi

Bitowe włączny operator OR (**&#124;**) porównuje każdy bit pierwszy argument operacji na odpowiadający mu bit drugim argumentem. Jeśli bit albo ma wartość 1, odpowiadający mu bit wynik jest równa 1. W przeciwnym razie odnośny bit wynik jest równa 0.

Oba operandy bitowe włączny operator OR musi być typu całkowitoliczbowego. Popularne konwersje arytmetyczne omówione w [konwersje standardowe](standard-conversions.md) są stosowane do operandów.

## <a name="operator-keyword-for-124"></a>Operator — słowo kluczowe dla&#124;

**Bitor** operator jest odpowiednikiem tekstu **&#124;**. Istnieją dwa sposoby dostępu do **bitor** operatora w programach: uwzględnić plik nagłówka \<iso646.h >, lub kompilowanie z [/Za](../build/reference/za-ze-disable-language-extensions.md) — opcja kompilatora (Wyłącz rozszerzenia językowe).

## <a name="example"></a>Przykład

```cpp
// expre_Bitwise_Inclusive_OR_Operator.cpp
// compile with: /EHsc
// Demonstrate bitwise inclusive OR
#include <iostream>
using namespace std;

int main() {
   unsigned short a = 0x5555;      // pattern 0101 ...
   unsigned short b = 0xAAAA;      // pattern 1010 ...

   cout  << hex << ( a | b ) << endl;   // prints "ffff" pattern 1111 ...
}
```

## <a name="see-also"></a>Zobacz także
 [Wbudowane operatory, pierwszeństwo i kojarzenie języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)  
 [Operatory bitowe języka C](../c-language/c-bitwise-operators.md)  