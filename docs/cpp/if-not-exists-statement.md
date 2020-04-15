---
title: __if_not_exists — Instrukcja
ms.date: 11/04/2016
f1_keywords:
- __if_not_exists_cpp
helpviewer_keywords:
- __if_not_exists keyword [C++]
ms.assetid: a2f322d4-e96f-4a32-954e-4323d20c6e32
ms.openlocfilehash: 1118f9fcca525b2b2d5869fb507ee974d2b0d28f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374137"
---
# <a name="__if_not_exists-statement"></a>__if_not_exists — Instrukcja

Instrukcja **__if_not_exists** sprawdza, czy określony identyfikator istnieje. Jeśli identyfikator nie istnieje, wykonywany jest określony blok instrukcji.

## <a name="syntax"></a>Składnia

```
__if_not_exists ( identifier ) {
statements
};
```

#### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Identyfikator*|Identyfikator, którego istnienie chcesz przetestować.|
|*Instrukcji*|Co najmniej jedna instrukcja do wykonania, jeśli *identyfikator* nie istnieje.|

## <a name="remarks"></a>Uwagi

> [!CAUTION]
> Aby osiągnąć najbardziej wiarygodne wyniki, należy użyć **__if_not_exists** instrukcji w następujących ograniczeniach.

- Zastosuj **instrukcję __if_not_exists** tylko do typów prostych, a nie szablonów.

- Zastosuj **__if_not_exists** instrukcji do identyfikatorów zarówno wewnątrz, jak i na zewnątrz klasy. Nie należy stosować **instrukcji __if_not_exists** do zmiennych lokalnych.

- Instrukcja **__if_not_exists** należy używać tylko w treści funkcji. Poza treścią **funkcji, __if_not_exists** instrukcja może testować tylko w pełni zdefiniowane typy.

- Podczas testowania funkcji przeciążonych, nie można przetestować dla określonej formy przeciążenia.

Uzupełnieniem **oświadczenia __if_not_exists** jest oświadczenie [__if_exists.](../cpp/if-exists-statement.md)

## <a name="example"></a>Przykład

Na przykład dotyczące **używania __if_not_exists**, zobacz [__if_exists Instrukcji](../cpp/if-exists-statement.md).

## <a name="see-also"></a>Zobacz też

[Instrukcje wyboru](../cpp/selection-statements-cpp.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[__if_exists, instrukcja](../cpp/if-exists-statement.md)
