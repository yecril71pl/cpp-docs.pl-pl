---
title: HANDLENullTraits — Struktura
ms.date: 09/27/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits::Close
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits::GetInvalidValue
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits::Close method
- Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits::GetInvalidValue method
ms.assetid: 88a29a14-c516-40cb-a0ca-ee897a668623
ms.openlocfilehash: 41e06cc50f36a077a34d992c416a543e5bf9b593
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371476"
---
# <a name="handlenulltraits-structure"></a>HANDLENullTraits — Struktura

Definiuje wspólne cechy niezainicjowanego uchwytu.

## <a name="syntax"></a>Składnia

```cpp
struct HANDLENullTraits;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne typedefs

Nazwa   | Opis
------ | ---------------------
`Type` | Synonim handle.

### <a name="public-methods"></a>Metody publiczne

Nazwa                                                  | Opis
----------------------------------------------------- | -----------------------------
[HANDLENullTraits::Zamknij](#close)                     | Zamyka określony uchwyt.
[HANDLENullTraits::GetInvalidValue](#getinvalidvalue) | Reprezentuje nieprawidłowy dojście.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`HANDLENullTraits`

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Obszar nazw:** Microsoft::WRL::Otoki::HandleTraits

## <a name="handlenulltraitsclose"></a><a name="close"></a>HANDLENullTraits::Zamknij

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

## <a name="handlenulltraitsgetinvalidvalue"></a><a name="getinvalidvalue"></a>HANDLENullTraits::GetInvalidValue

Reprezentuje nieprawidłowy dojście.

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca wartość `nullptr`.
