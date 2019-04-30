---
title: is_final, klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_final
helpviewer_keywords:
- is_final
ms.assetid: 9dbad82f-6685-4909-94e8-98e4a93994b9
ms.openlocfilehash: f605b160f6ed71aaafcc7c391e17180e4b243444
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "64346439"
---
# <a name="isfinal-class"></a>is_final, klasa

Sprawdza, czy typ jest typem klasy oznaczone `final`.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
struct is_final;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ do zapytania.

## <a name="remarks"></a>Uwagi

Wystąpienie typu predykatu ma wartość true, jeśli typ *T* typu klasy jest oznaczony `final`, w przeciwnym razie przechowuje wartość false. Jeśli *T* jest typem klasy musi być typem kompletnym.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
[final, specyfikator](../cpp/final-specifier.md)<br/>
