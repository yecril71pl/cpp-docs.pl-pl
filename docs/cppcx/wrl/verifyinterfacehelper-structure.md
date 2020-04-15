---
title: VerifyInterfaceHelper — Struktura
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::VerifyInterfaceHelper
- implements/Microsoft::WRL::Details::VerifyInterfaceHelper::Verify
helpviewer_keywords:
- Microsoft::WRL::Details::VerifyInterfaceHelper structure
- Microsoft::WRL::Details::VerifyInterfaceHelper::Verify method
ms.assetid: ea95b641-199a-4fdf-964b-186b40cb3ba7
ms.openlocfilehash: 09c2cc7e08e2dc0e8df42c64d285c37627c5925a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374245"
---
# <a name="verifyinterfacehelper-structure"></a>VerifyInterfaceHelper — Struktura

Obsługuje infrastrukturę biblioteki szablonów środowiska wykonawczego systemu Windows W++ i nie jest przeznaczona do użycia bezpośrednio z kodu.

## <a name="syntax"></a>Składnia

```cpp
template <bool isWinRTInterface, typename I>
struct VerifyInterfaceHelper;

template <typename I>
struct VerifyInterfaceHelper<false, I>;
```

### <a name="parameters"></a>Parametry

*I*<br/>
Interfejs do weryfikacji.

*isWinRTInterface*

## <a name="remarks"></a>Uwagi

Sprawdza, czy interfejs określony przez parametr szablonu spełnia określone wymagania.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

Nazwa                                            | Opis
----------------------------------------------- | ---------------------------------------------------------------------------------------------------
[VerifyInterfaceHelper::Verify, metoda](#verify) | Sprawdza, czy interfejs określony przez bieżący parametr szablonu spełnia określone wymagania.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`VerifyInterfaceHelper`

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Obszar nazw:** Microsoft::WRL::Dszczegóły

## <a name="verifyinterfacehelperverify"></a><a name="verify"></a>VerifyInterfaceHelper::VerifyInterfaceHelper::Verify VerifyInterfaceHelper::Verify VerifyInterface

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
static void Verify();
```

### <a name="remarks"></a>Uwagi

Sprawdza, czy interfejs określony przez bieżący parametr szablonu spełnia określone wymagania.
