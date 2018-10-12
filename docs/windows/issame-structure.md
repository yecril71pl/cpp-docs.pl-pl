---
title: Issame — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::IsSame
- internal/Microsoft::WRL::Details::IsSame::value
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Details::IsSame structure
- Microsoft::WRL::Details::IsSame::value constant
ms.assetid: 1eddbc3f-3cc5-434f-8495-e4477e1f868e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2af59860016835f8e8dfddc9d0a77204ff866bd3
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2018
ms.locfileid: "49161856"
---
# <a name="issame-structure"></a>IsSame — Struktura

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
template <typename T1, typename T2>
struct IsSame;

template <typename T1>
struct IsSame<T1, T1>;
```

### <a name="parameters"></a>Parametry

*T1*<br/>
Typ.

*T2*<br/>
Innego typu.

## <a name="remarks"></a>Uwagi

Testy, czy jeden określony typ jest taki sam jak inny określony typ.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constants"></a>Publiczne stałe

Nazwa                    | Opis
----------------------- | --------------------------------------------------
[IsSame::value](#value) | Wskazuje, czy jeden typ jest taki sam jak inny.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IsSame`

## <a name="requirements"></a>Wymagania

**Nagłówek:** internal.h

**Namespace:** Microsoft::wrl:: details

## <a name="value"></a>IsSame::value

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
template <typename T1, typename T2>
struct IsSame
{
    static const bool value = false;
};

template <typename T1>
struct IsSame<T1, T1>
{
    static const bool value = true;
};
```

### <a name="remarks"></a>Uwagi

Wskazuje, czy jeden typ jest taki sam jak inny.

`value` jest **true** Jeśli parametry szablonu są takie same, i **false** Jeśli parametry szablonu są różne.
