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
ms.openlocfilehash: c04e53789fd737b12ca10ef2c279a05fb43f5925
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212998"
---
# <a name="handletraits-structure"></a>HANDLETraits — Struktura

Definiuje typowe cechy dojścia.

## <a name="syntax"></a>Składnia

```cpp
struct HANDLETraits;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

Nazwa   | Opis
------ | ---------------------
`Type` | Synonim dla UCHWYTu.

### <a name="public-methods"></a>Metody publiczne

Nazwa                                              | Opis
------------------------------------------------- | -----------------------------
[HANDLETraits:: Close](#close)                     | Zamyka określone dojście.
[HANDLETraits:: GetInvalidValue —](#getinvalidvalue) | Reprezentuje nieprawidłowe dojście.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`HANDLETraits`

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers. h

**Przestrzeń nazw:** Microsoft:: WRL:: otoki:: HandleTraits

## <a name="handletraitsclose"></a><a name="close"></a>HANDLETraits:: Close

Zamyka określone dojście.

```cpp
inline static bool Close(
   _In_ Type h
);
```

### <a name="parameters"></a>Parametry

*c*<br/>
Uchwyt do zamknięcia.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli dojście *h* zostało zamknięte pomyślnie; w przeciwnym razie **`false`** .

## <a name="handletraitsgetinvalidvalue"></a><a name="getinvalidvalue"></a>HANDLETraits:: GetInvalidValue —

Reprezentuje nieprawidłowe dojście.

```cpp
inline static HANDLE GetInvalidValue();
```

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca INVALID_HANDLE_VALUE. (INVALID_HANDLE_VALUE jest definiowana przez system Windows).
