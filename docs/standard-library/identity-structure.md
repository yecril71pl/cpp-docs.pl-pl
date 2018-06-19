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
ms.openlocfilehash: 83180020c20f78c16af0b1b33bada91936b6af9b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33844409"
---
# <a name="identity-structure"></a>identity — Struktura

Struktury, zapewniająca definicją typu jako parametru szablonu.

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
|`left`|Wartość do identyfikacji.|

## <a name="remarks"></a>Uwagi

Klasa zawiera definicję typu publicznego `type`, który jest taki sam jak typ parametru szablonu. Jest on używany w połączeniu z funkcją szablonu [do przodu](../standard-library/utility-functions.md#forward) aby upewnić się, że parametr funkcji ma żądanego typu.

Zgodność ze starszego kodu, klasa definiuje również funkcji identity `operator()` zwraca jej argument `left`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<narzędzie >

**Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[\<utility>](../standard-library/utility.md)<br/>
