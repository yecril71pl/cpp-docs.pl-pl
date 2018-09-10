---
title: is_pointer — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_pointer
dev_langs:
- C++
helpviewer_keywords:
- is_pointer class
- is_pointer
ms.assetid: 44e0a403-7241-4e0a-8922-32877bcb9a4c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a61276cc47e13205f0076789049881305faf0760
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44106725"
---
# <a name="ispointer-class"></a>is_pointer — Klasa

Sprawdza, czy typ jest wskaźnikiem.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
struct is_pointer;
```

### <a name="parameters"></a>Parametry

*Ty*<br/>
Typ do zapytania.

## <a name="remarks"></a>Uwagi

Wystąpienie typu predykatu ma wartość true, jeśli typ *Ty* jest wskaźnikiem do **void**, wskaźnik do obiektu lub wskaźnik do funkcji lub na `cv-qualified` postaci jednego z tych funkcji, w przeciwnym razie przechowuje wartość false. Należy pamiętać, że `is_pointer` przechowuje FAŁSZ Jeśli *Ty* jest wskaźnik do składowej lub wskaźnika do funkcji składowej.

## <a name="example"></a>Przykład

```cpp
// std__type_traits__is_pointer.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

int main()
    {
    std::cout << "is_pointer<trivial> == " << std::boolalpha
        << std::is_pointer<trivial>::value << std::endl;
    std::cout << "is_pointer<int trivial::*> == " << std::boolalpha
        << std::is_pointer<int trivial::*>::value << std::endl;
    std::cout << "is_pointer<trivial *> == " << std::boolalpha
        << std::is_pointer<trivial *>::value << std::endl;
    std::cout << "is_pointer<int> == " << std::boolalpha
        << std::is_pointer<int>::value << std::endl;
    std::cout << "is_pointer<int *> == " << std::boolalpha
        << std::is_pointer<int *>::value << std::endl;

    return (0);
    }

```

```Output
is_pointer<trivial> == false
is_pointer<int trivial::*> == false
is_pointer<trivial *> == true
is_pointer<int> == false
is_pointer<int *> == true
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
[is_member_pointer, klasa](../standard-library/is-member-pointer-class.md)<br/>
[is_reference, klasa](../standard-library/is-reference-class.md)<br/>
