---
title: __if_not_exists — Instrukcja
ms.date: 11/04/2016
f1_keywords:
- __if_not_exists_cpp
helpviewer_keywords:
- __if_not_exists keyword [C++]
ms.assetid: a2f322d4-e96f-4a32-954e-4323d20c6e32
ms.openlocfilehash: 3e0eb550830a1689d440e3b471759a98f1eef0ca
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87187260"
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

|Parametr|Opis|
|---------------|-----------------|
|*identyfikatora*|Identyfikator, którego istnienie ma zostać przetestowane.|
|*zatwierdzeni*|Jedna lub więcej instrukcji do wykonania, jeśli *Identyfikator* nie istnieje.|

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

## <a name="see-also"></a>Zobacz także

[Instrukcje wyboru](../cpp/selection-statements-cpp.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[Instrukcja __if_exists](../cpp/if-exists-statement.md)
