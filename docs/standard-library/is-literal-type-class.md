---
title: is_literal_type, klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_literal_type
helpviewer_keywords:
- is_literal_type
ms.assetid: a03a4ebb-ee66-48d6-91bb-41cf72b2401f
ms.openlocfilehash: 804ef0462308b967fc0c4c95d8dfa96476475aab
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50514008"
---
# <a name="isliteraltype-class"></a>is_literal_type, klasa

Sprawdza, czy typ mogą być używane jako `constexpr` zmiennej lub skonstruowany, używane przez lub zwrócone w wyniku `constexpr` funkcji.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
struct is_literal_type;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ do zapytania.

## <a name="remarks"></a>Uwagi

Wystąpienie typu predykatu ma wartość true, jeśli typ *T* jest *literalne*, w przeciwnym razie przechowuje wartość false. Jest typem literału **void**, typowi skalarnemu, typ odwołania, tablicy literału typu lub typu klasy literału. Typ literału klasy jest typu klasy, która ma destruktor proste, jest albo odpowiedni typ agregacji lub ma co najmniej jednego innego niż z przeniesienia / kopia `constexpr` Konstruktor i wszystkie jej klasy bazowe i elementy członkowskie danych niestatycznych są typy literałów trwałej. Chociaż typ literału jest zawsze typem literału, koncepcji typem literału obejmuje wszystkie elementy, które kompilator może być interpretowane jako `constexpr` w czasie kompilacji.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
