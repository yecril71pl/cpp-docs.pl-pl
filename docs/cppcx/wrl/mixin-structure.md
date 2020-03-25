---
title: MixIn — Struktura
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::MixIn
helpviewer_keywords:
- MixIn structure
ms.assetid: 47e2df9b-3a2e-4ae8-8ba3-b1fd3aa73566
ms.openlocfilehash: b302d6e08e401a24b465508d5ddabcae8b16bd8f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213697"
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

*Pozyskiwan*<br/>
Typ pochodzący od struktury [implementującej](implements-structure.md) .

*MixInType*<br/>
Typ podstawowy.

*hasImplements*<br/>
**wartość true** , jeśli *MixInType* jest pochodną bieżącej implementacji typu podstawowego; w przeciwnym razie **zwraca wartość false** .

## <a name="remarks"></a>Uwagi

Jeśli klasa jest pochodną zarówno środowisko wykonawcze systemu Windows, jak i interfejsów COM, lista deklaracji klasy musi najpierw wyświetlić wszystkie interfejsy środowisko wykonawcze systemu Windows, a następnie wszystkie klasyczne interfejsy COM. **Domieszki** gwarantuje, że interfejsy są określone w poprawnej kolejności.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`MixIn`

## <a name="requirements"></a>Wymagania

**Nagłówek:** implementuje. h

**Przestrzeń nazw:** Microsoft:: WRL

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL, przestrzeń nazw](microsoft-wrl-namespace.md)
