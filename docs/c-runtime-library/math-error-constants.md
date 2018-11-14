---
title: Stałe błędów matematycznych
ms.date: 11/04/2016
f1_keywords:
- _PLOSS
- _UNDERFLOW
- _TLOSS
- _SING
- _DOMAIN
- _OVERFLOW
helpviewer_keywords:
- _TLOSS constant
- _SING constant
- PLOSS constant
- UNDERFLOW constant
- _UNDERFLOW constant
- _OVERFLOW constant
- DOMAIN constant
- OVERFLOW constant
- TLOSS constant
- SING constant
- _DOMAIN constant
- _PLOSS constant
- math error constants
ms.assetid: 4be933a6-674e-45a5-8ac9-090023542f5b
ms.openlocfilehash: f51d9a3a28118d922f81a44e31c9abc610645f13
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2018
ms.locfileid: "51524998"
---
# <a name="math-error-constants"></a>Stałe błędów matematycznych

## <a name="syntax"></a>Składnia

```

#include <math.h>
```

## <a name="remarks"></a>Uwagi

Procedury matematyczne biblioteki wykonawczej może generować stałe błędów matematycznych.

Te błędy, poniżej opisano odpowiadają typów wyjątków zdefiniowanych w MATEMATYCE. Godz. i są zwracane przez `_matherr` działać, jeśli wystąpi błąd matematyczny.

|Stała|Znaczenie|
|--------------|-------------|
|`_DOMAIN`|Argument funkcji jest spoza domeny funkcji.|
|`_OVERFLOW`|Wynik jest za duży, aby mogły być reprezentowane w zwracanego typu funkcji.|
|`_PLOSS`|Częściowe utrata znaczenia wystąpił.|
|`_SING`|Argument singularity: argument funkcji ma nieprawidłową wartość. (Na przykład, wartość 0 jest przekazywany do funkcji, która wymaga wartość różną od zera.)|
|`_TLOSS`|Całkowita utrata znaczenia wystąpił.|
|`_UNDERFLOW`|Wynik jest za mały, aby mogły być reprezentowane.|

## <a name="see-also"></a>Zobacz też

[_matherr](../c-runtime-library/reference/matherr.md)<br/>
[Stałe globalne](../c-runtime-library/global-constants.md)