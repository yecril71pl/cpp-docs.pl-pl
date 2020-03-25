---
title: __if_not_exists — Instrukcja
ms.date: 11/04/2016
f1_keywords:
- __if_not_exists_cpp
helpviewer_keywords:
- __if_not_exists keyword [C++]
ms.assetid: a2f322d4-e96f-4a32-954e-4323d20c6e32
ms.openlocfilehash: 7372ac127a7b4dd5c05d58cfecca25f87690b0ae
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178192"
---
# <a name="__if_not_exists-statement"></a>__if_not_exists — Instrukcja

Instrukcja **__if_not_exists** testuje, czy określony identyfikator istnieje. Jeśli identyfikator nie istnieje, zostanie wykonany określony blok instrukcji.

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
>  Aby uzyskać najbardziej niezawodne wyniki, użyj instrukcji **__if_not_exists** w ramach następujących ograniczeń.

- Zastosuj instrukcję **__if_not_exists** tylko do typów prostych, a nie szablonów.

- Zastosuj instrukcję **__if_not_exists** do identyfikatorów zarówno wewnątrz, jak i poza klasą. Nie stosuj instrukcji **__if_not_exists** do zmiennych lokalnych.

- Użyj instrukcji **__if_not_exists** tylko w treści funkcji. Poza treścią funkcji, instrukcja **__if_not_exists** może testować tylko w pełni zdefiniowane typy.

- Podczas testowania dla przeciążonych funkcji nie można testować pod kątem określonej formy przeciążenia.

Uzupełnienie instrukcji **__if_not_exists** jest instrukcją [__if_exists](../cpp/if-exists-statement.md) .

## <a name="example"></a>Przykład

Aby zapoznać się z przykładem dotyczącym używania **__if_not_exists**, zobacz [__if_exists instrukcji](../cpp/if-exists-statement.md).

## <a name="see-also"></a>Zobacz też

[Instrukcje wyboru](../cpp/selection-statements-cpp.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[__if_exists, instrukcja](../cpp/if-exists-statement.md)
