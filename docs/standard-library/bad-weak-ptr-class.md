---
title: bad_weak_ptr — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- memory/std::bad_weak_ptr
dev_langs:
- C++
helpviewer_keywords:
- bad_weak_ptr
- bad_weak_ptr class
ms.assetid: a09336d5-7237-4480-ab6b-3787e0e6025e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8cb6e00341e5e40d04be1d447f03e43818e53291
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="badweakptr-class"></a>bad_weak_ptr — Klasa

Zgłasza zły wyjątek weak_ptr.

## <a name="syntax"></a>Składnia

```cpp
class bad_weak_ptr : public std::exception
 {
public:
    bad_weak_ptr();
    const char *what() throw();
 };
```

## <a name="remarks"></a>Uwagi

Klasa opisuje wyjątek, który może zostać wygenerowany z [shared_ptr — klasa](../standard-library/shared-ptr-class.md) konstruktora, który przyjmuje argument typu [weak_ptr — klasa](../standard-library/weak-ptr-class.md). Funkcja członkowska `what` zwraca `"bad_weak_ptr"`.

## <a name="example"></a>Przykład

```cpp
// std__memory__bad_weak_ptr.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::weak_ptr<int> wp;

    {
        std::shared_ptr<int> sp(new int);
        wp = sp;
    }

    try
    {
        std::shared_ptr<int> sp1(wp); // weak_ptr has expired
    }
    catch (const std::bad_weak_ptr&)
    {
        std::cout << "bad weak pointer" << std::endl;
    }
    catch (...)
    {
        std::cout << "unknown exception" << std::endl;
    }

    return (0);
}
```

```Output
bad weak pointer
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<pamięci >

**Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[weak_ptr, klasa](../standard-library/weak-ptr-class.md)<br/>
