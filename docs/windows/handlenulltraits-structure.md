---
title: Handlenulltraits — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/27/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits::Close
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits::GetInvalidValue
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits::Close method
- Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits::GetInvalidValue method
ms.assetid: 88a29a14-c516-40cb-a0ca-ee897a668623
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1060d28e35a52e2a8c5c550664d36d8272628526
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2018
ms.locfileid: "49161739"
---
# <a name="handlenulltraits-structure"></a>HANDLENullTraits — Struktura

Definiuje typowe cechy niezainicjowany uchwyt.

## <a name="syntax"></a>Składnia

```cpp
struct HANDLENullTraits;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

Nazwa   | Opis
------ | ---------------------
`Type` | Synonim dla dojście.

### <a name="public-methods"></a>Metody publiczne

Nazwa                                                  | Opis
----------------------------------------------------- | -----------------------------
[HANDLENullTraits::Close](#close)                     | Zamyka określone dojście.
[HANDLENullTraits::GetInvalidValue](#getinvalidvalue) | Reprezentuje nieprawidłowego dojścia.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`HANDLENullTraits`

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::HandleTraits

## <a name="close"></a>HANDLENullTraits::Close

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

## <a name="getinvalidvalue"></a>HANDLENullTraits::GetInvalidValue

Reprezentuje nieprawidłowego dojścia.

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca `nullptr`.
