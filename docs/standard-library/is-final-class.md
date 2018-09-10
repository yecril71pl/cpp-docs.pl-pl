---
title: is_final, klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- type_traits/std::is_final
dev_langs:
- C++
helpviewer_keywords:
- is_final
ms.assetid: 9dbad82f-6685-4909-94e8-98e4a93994b9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 016ad1c5017635000f17b8852f7ebdb8e2f62e4a
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44108697"
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
