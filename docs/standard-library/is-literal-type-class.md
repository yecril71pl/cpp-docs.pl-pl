---
title: is_literal_type, klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- type_traits/std::is_literal_type
dev_langs:
- C++
helpviewer_keywords:
- is_literal_type
ms.assetid: a03a4ebb-ee66-48d6-91bb-41cf72b2401f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fd4481be124cbcbba04f6b45b4c5a08beb34f04d
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44103308"
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
