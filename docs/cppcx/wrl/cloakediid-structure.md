---
title: CloakedIid — Struktura
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::CloakedIid
helpviewer_keywords:
- CloakedIid structure
ms.assetid: 82e0e377-ca3a-46bc-b850-ae2c46c15bb5
ms.openlocfilehash: 10dc2af1897147045382e8463b6602fa015fc899
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59033726"
---
# <a name="cloakediid-structure"></a>CloakedIid — Struktura

Wskazuje, aby `RuntimeClass`, `Implements` i `ChainInterfaces` określonego interfejsu nie jest dostępny na liście IID szablonów.

## <a name="syntax"></a>Składnia

```cpp
template<typename T>
struct CloakedIid : T;
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Interfejs który jest ukryty (osłonięty).

## <a name="remarks"></a>Uwagi

Poniżej przedstawiono przykładowy sposób **cloakediid —** służy: `struct MyRuntimeClass : RuntimeClass<CloakedIid<IMyCloakedInterface>> {}`.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`T`

`CloakedIid`

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz także

[Microsoft::WRL, przestrzeń nazw](microsoft-wrl-namespace.md)