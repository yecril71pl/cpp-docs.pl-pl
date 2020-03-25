---
title: CloakedIid — Struktura
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::CloakedIid
helpviewer_keywords:
- CloakedIid structure
ms.assetid: 82e0e377-ca3a-46bc-b850-ae2c46c15bb5
ms.openlocfilehash: 1cc9e79384bbf4aae44199c2f35331e3afd8fd8f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214113"
---
# <a name="cloakediid-structure"></a>CloakedIid — Struktura

Wskazuje `RuntimeClass`, `Implements` i `ChainInterfaces` szablonów, których określony interfejs nie jest dostępny na liście IID.

## <a name="syntax"></a>Składnia

```cpp
template<typename T>
struct CloakedIid : T;
```

#### <a name="parameters"></a>Parametry

*&*<br/>
Interfejs, który jest ukryty (zamaskowany).

## <a name="remarks"></a>Uwagi

Poniżej przedstawiono przykład sposobu użycia **CloakedIid —** : `struct MyRuntimeClass : RuntimeClass<CloakedIid<IMyCloakedInterface>> {}`.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`T`

`CloakedIid`

## <a name="requirements"></a>Wymagania

**Nagłówek:** implementuje. h

**Przestrzeń nazw:** Microsoft:: WRL

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL, przestrzeń nazw](microsoft-wrl-namespace.md)
