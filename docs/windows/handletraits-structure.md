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
ms.openlocfilehash: 4dd2cde62d36c46926e703e6fb649e2ae4ef7811
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50590076"
---
# <a name="handletraits-structure"></a>HANDLETraits — Struktura

Definiuje typowe cechy dojście.

## <a name="syntax"></a>Składnia

```cpp
struct HANDLETraits;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

Nazwa   | Opis
------ | ---------------------
`Type` | Synonim dla dojście.

### <a name="public-methods"></a>Metody publiczne

Nazwa                                              | Opis
------------------------------------------------- | -----------------------------
[HANDLETraits::Close](#close)                     | Zamyka określone dojście.
[HANDLETraits::GetInvalidValue](#getinvalidvalue) | Reprezentuje nieprawidłowego dojścia.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`HANDLETraits`

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::HandleTraits

## <a name="close"></a>HANDLETraits::Close

Zamyka określone dojście.

```cpp
inline static bool Close(
   _In_ Type h
);
```

### <a name="parameters"></a>Parametry

*h*<br/>
Dojście do zamknięcia.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli obsługi *h* zamknięta pomyślnie; w przeciwnym razie **false**.

## <a name="getinvalidvalue"></a>HANDLETraits::GetInvalidValue

Reprezentuje nieprawidłowego dojścia.

```cpp
inline static HANDLE GetInvalidValue();
```

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca INVALID_HANDLE_VALUE. (INVALID_HANDLE_VALUE jest definiowany przez Windows).
