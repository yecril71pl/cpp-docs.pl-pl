---
title: is_move_constructible, klasa
ms.date: 10/24/2019
f1_keywords:
- type_traits/std::is_move_constructible
helpviewer_keywords:
- is_move_constructible
ms.assetid: becdf076-7419-488d-a335-78adf2478b9b
ms.openlocfilehash: 9585a932a34a24769201aaa379525a9b4c181e41
ms.sourcegitcommit: 33a898bf976c65f998b4e88a84765a0cef4193a8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920094"
---
# <a name="is_move_constructible-class"></a>is_move_constructible, klasa

Testuje, czy typ można utworzyć przy użyciu operacji przenoszenia.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
struct is_move_constructible;
```

### <a name="parameters"></a>Parametry

*T* \
Typ do obliczenia.

## <a name="remarks"></a>Uwagi

Predykat typu, którego wynikiem jest **wartość true** , jeśli typ *T* może być skonstruowany przy użyciu operacji przenoszenia. Ten predykat jest równoważny `is_constructible<T, T&&>`. Typ *T* , który nie ma konstruktora Move, ale ma Konstruktor kopiujący akceptujący argument `const T&`, spełnia `std::is_move_constructible`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)
