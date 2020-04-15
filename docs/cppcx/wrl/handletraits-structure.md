---
title: HANDLETraits — Struktura
ms.date: 09/27/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits::Close
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits::GetInvalidValue
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits structure
- Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits::Close method
- Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits::GetInvalidValue method
ms.assetid: 22963e88-d857-4624-9182-7c986daff722
ms.openlocfilehash: 604098cd3289722767117910d6e44e272dcb8b77
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371447"
---
# <a name="handletraits-structure"></a>HANDLETraits — Struktura

Definiuje wspólne cechy uchwytu.

## <a name="syntax"></a>Składnia

```cpp
struct HANDLETraits;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne typedefs

Nazwa   | Opis
------ | ---------------------
`Type` | Synonim handle.

### <a name="public-methods"></a>Metody publiczne

Nazwa                                              | Opis
------------------------------------------------- | -----------------------------
[HANDLETraits::Zamknij](#close)                     | Zamyka określony uchwyt.
[HANDLETraits::GetInvalidValue](#getinvalidvalue) | Reprezentuje nieprawidłowy dojście.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`HANDLETraits`

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Obszar nazw:** Microsoft::WRL::Otoki::HandleTraits

## <a name="handletraitsclose"></a><a name="close"></a>HANDLETraits::Zamknij

Zamyka określony uchwyt.

```cpp
inline static bool Close(
   _In_ Type h
);
```

### <a name="parameters"></a>Parametry

*H*<br/>
Uchwyt do zamknięcia.

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli uchwyt *h* zamknięty pomyślnie; w przeciwnym razie **false**.

## <a name="handletraitsgetinvalidvalue"></a><a name="getinvalidvalue"></a>HANDLETraits::GetInvalidValue

Reprezentuje nieprawidłowy dojście.

```cpp
inline static HANDLE GetInvalidValue();
```

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca INVALID_HANDLE_VALUE. (INVALID_HANDLE_VALUE jest zdefiniowany przez system Windows).
