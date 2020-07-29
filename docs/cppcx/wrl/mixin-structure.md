---
title: MixIn — Struktura
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::MixIn
helpviewer_keywords:
- MixIn structure
ms.assetid: 47e2df9b-3a2e-4ae8-8ba3-b1fd3aa73566
ms.openlocfilehash: cfa03706bc6030b337009f7228466a26e242aa6b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221539"
---
# <a name="mixin-structure"></a>MixIn — Struktura

Zapewnia, że Klasa środowiska uruchomieniowego pochodzi z interfejsów środowisko wykonawcze systemu Windows, jeśli istnieje, a następnie do klasycznych interfejsów COM.

## <a name="syntax"></a>Składnia

```cpp
template<
    typename Derived,
    typename MixInType,
    bool hasImplements = __is_base_of(Details::ImplementsBase, MixInType)
>
struct MixIn;
```

### <a name="parameters"></a>Parametry

*Pochodne*<br/>
Typ pochodzący od struktury [implementującej](implements-structure.md) .

*MixInType*<br/>
Typ podstawowy.

*hasImplements*<br/>
**`true`** Jeśli *MixInType* jest pochodną bieżącej implementacji typu podstawowego; **`false`** w przeciwnym razie.

## <a name="remarks"></a>Uwagi

Jeśli klasa jest pochodną zarówno środowisko wykonawcze systemu Windows, jak i interfejsów COM, lista deklaracji klasy musi najpierw wyświetlić wszystkie interfejsy środowisko wykonawcze systemu Windows, a następnie wszystkie klasyczne interfejsy COM. **Domieszki** gwarantuje, że interfejsy są określone w poprawnej kolejności.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`MixIn`

## <a name="requirements"></a>Wymagania

**Nagłówek:** implementuje. h

**Przestrzeń nazw:** Microsoft:: WRL

## <a name="see-also"></a>Zobacz także

[Microsoft:: WRL, przestrzeń nazw](microsoft-wrl-namespace.md)
