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
ms.openlocfilehash: c37a0eb74fd65b3d349d5b8b7c792fbaf7d1ac9a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398085"
---
# <a name="verifyinheritancehelper-structure"></a>VerifyInheritanceHelper — Struktura

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

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

*Base*<br/>
Innego typu.

## <a name="remarks"></a>Uwagi

Sprawdza, czy jeden interfejs jest tworzony na podstawie innego interfejsu.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

Nazwa                                       | Opis
------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------
[VerifyInheritanceHelper::Verify](#verify) | Testuje dwa interfejsy, które są określone przez bieżący parametry szablonu i określa, czy jeden interfejs jest tworzony na podstawie innych.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`VerifyInheritanceHelper`

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Namespace:** Microsoft::WRL::Details

## <a name="verify"></a>VerifyInheritanceHelper::Verify

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
static void Verify();
```

### <a name="remarks"></a>Uwagi

Testuje dwa interfejsy, które są określone przez bieżący parametry szablonu i określa, czy jeden interfejs jest tworzony na podstawie innych.

Błąd jest emitowane, jeśli jeden interfejs nie pochodzi od innych.
