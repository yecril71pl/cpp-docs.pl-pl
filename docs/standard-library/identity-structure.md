---
title: identity — Struktura
ms.date: 11/04/2016
f1_keywords:
- utility/std::identity
helpviewer_keywords:
- identity class
- identity structure
ms.assetid: 990756fd-7969-4b39-ad7e-0878e8dac8fd
ms.openlocfilehash: 722eb9c0579d0c07765434127d0a7c43718fbc37
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50615517"
---
# <a name="identity-structure"></a>identity — Struktura

Struktury, która zawiera definicję dla typu jako parametru szablonu.

## <a name="syntax"></a>Składnia

```cpp
struct identity {
   typedef Type type;
   Type operator()(const Type& left) const;
   };
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*left*|Wartość do identyfikacji.|

## <a name="remarks"></a>Uwagi

Klasa zawiera definicję typu publicznego `type`, która jest taka sama jak wartość parametru szablonu typu. Jest używana w połączeniu z funkcją szablonu [do przodu](../standard-library/utility-functions.md#forward) to upewnić się, że parametr funkcji żądanego typu.

Zgodność z starszego kodu, klasa definiuje również funkcji identity `operator()` zwraca jej argument *po lewej stronie*.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<Narzędzia >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[\<utility>](../standard-library/utility.md)<br/>
