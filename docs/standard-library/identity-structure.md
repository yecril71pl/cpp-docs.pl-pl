---
title: Identity — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- utility/std::identity
dev_langs:
- C++
helpviewer_keywords:
- identity class
- identity structure
ms.assetid: 990756fd-7969-4b39-ad7e-0878e8dac8fd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f065f7c00d3853d00c1063cd5b2838ec6d1d27b4
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38953000"
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
