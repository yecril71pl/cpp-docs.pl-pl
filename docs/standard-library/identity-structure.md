---
title: identity — Struktura
ms.date: 11/04/2016
f1_keywords:
- utility/std::identity
helpviewer_keywords:
- identity class
- identity structure
ms.assetid: 990756fd-7969-4b39-ad7e-0878e8dac8fd
ms.openlocfilehash: 49b2c1eb3ca03f9bf9199bdbca49348866ff0a7e
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246161"
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

*po lewej stronie*\
Wartość do identyfikacji.

## <a name="remarks"></a>Uwagi

Klasa zawiera definicję typu publicznego `type`, która jest taka sama jak wartość parametru szablonu typu. Jest używana w połączeniu z funkcją szablonu [do przodu](../standard-library/utility-functions.md#forward) to upewnić się, że parametr funkcji żądanego typu.

Zgodność z starszego kodu, klasa definiuje również funkcji identity `operator()` zwraca jej argument *po lewej stronie*.
