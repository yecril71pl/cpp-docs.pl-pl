---
title: __if_not_exists — Instrukcja
ms.date: 11/04/2016
f1_keywords:
- __if_not_exists_cpp
helpviewer_keywords:
- __if_not_exists keyword [C++]
ms.assetid: a2f322d4-e96f-4a32-954e-4323d20c6e32
ms.openlocfilehash: e99fcee440bd69eabafec693df99d347f3aee828
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/18/2020
ms.locfileid: "88560286"
---
# <a name="__if_not_exists-statement"></a>__if_not_exists — Instrukcja

**`__if_not_exists`** Instrukcja testuje, czy określony identyfikator istnieje. Jeśli identyfikator nie istnieje, zostanie wykonany określony blok instrukcji.

## <a name="syntax"></a>Składnia

```
__if_not_exists ( identifier ) {
statements
};
```

#### <a name="parameters"></a>Parametry

*identyfikatora*\
Identyfikator, którego istnienie ma zostać przetestowane.

*zatwierdzeni*\
Jedna lub więcej instrukcji do wykonania, jeśli *Identyfikator* nie istnieje.

## <a name="remarks"></a>Uwagi

> [!CAUTION]
> Aby uzyskać najbardziej niezawodne wyniki, użyj **`__if_not_exists`** instrukcji w ramach następujących ograniczeń.

- Zastosuj **`__if_not_exists`** instrukcję tylko do typów prostych, a nie szablonów.

- Zastosuj **`__if_not_exists`** instrukcję do identyfikatorów zarówno wewnątrz, jak i poza klasą. Nie stosuj **`__if_not_exists`** instrukcji do zmiennych lokalnych.

- Użyj **`__if_not_exists`** instrukcji tylko w treści funkcji. Poza treścią funkcji, **`__if_not_exists`** instrukcja może testować tylko w pełni zdefiniowane typy.

- Podczas testowania dla przeciążonych funkcji nie można testować pod kątem określonej formy przeciążenia.

Uzupełnienie **`__if_not_exists`** instrukcji jest instrukcją [__if_exists](../cpp/if-exists-statement.md) .

## <a name="example"></a>Przykład

Aby zapoznać się z przykładem sposobu użycia **`__if_not_exists`** , zobacz [__if_exists instrukcji](../cpp/if-exists-statement.md).

## <a name="see-also"></a>Zobacz też

[Instrukcje wyboru](../cpp/selection-statements-cpp.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[Instrukcja __if_exists](../cpp/if-exists-statement.md)
