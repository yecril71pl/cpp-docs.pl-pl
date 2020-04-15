---
title: VerifyInheritanceHelper — Struktura
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::VerifyInheritanceHelper
- implements/Microsoft::WRL::Details::VerifyInheritanceHelper::Verify
helpviewer_keywords:
- Microsoft::WRL::Details::VerifyInheritanceHelper structure
- Microsoft::WRL::Details::VerifyInheritanceHelper::Verify method
ms.assetid: 8a48a702-0f71-4807-935b-8311f0a7a8b6
ms.openlocfilehash: 3650cfb70ffc12572b3965534eff4e1f2ecb2cf5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374231"
---
# <a name="verifyinheritancehelper-structure"></a>VerifyInheritanceHelper — Struktura

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

## <a name="syntax"></a>Składnia

```cpp
template <typename I, typename Base>
struct VerifyInheritanceHelper;

template <typename I>
struct VerifyInheritanceHelper<I, Nil>;
```

### <a name="parameters"></a>Parametry

*I*<br/>
Typ.

*Podstawowej*<br/>
Inny typ.

## <a name="remarks"></a>Uwagi

Sprawdza, czy jeden interfejs pochodzi z innego interfejsu.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

Nazwa                                       | Opis
------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------
[VerifyInheritanceHelper::Verify VerifyInheritanceHelper::Verify VerifyInheritanceHelper::Verify VerifyIn](#verify) | Testuje dwa interfejsy określone przez bieżące parametry szablonu i określa, czy jeden interfejs jest pochodną drugiego.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`VerifyInheritanceHelper`

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Obszar nazw:** Microsoft::WRL::Dszczegóły

## <a name="verifyinheritancehelperverify"></a><a name="verify"></a>VerifyInheritanceHelper::Verify VerifyInheritanceHelper::Verify VerifyInheritanceHelper::Verify VerifyIn

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
static void Verify();
```

### <a name="remarks"></a>Uwagi

Testuje dwa interfejsy określone przez bieżące parametry szablonu i określa, czy jeden interfejs jest pochodną drugiego.

Błąd jest emitowany, jeśli jeden interfejs nie pochodzi od drugiego.
