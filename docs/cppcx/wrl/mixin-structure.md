---
title: MixIn — Struktura
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::MixIn
helpviewer_keywords:
- MixIn structure
ms.assetid: 47e2df9b-3a2e-4ae8-8ba3-b1fd3aa73566
ms.openlocfilehash: d0306f4c497dd26e782b1ef2c012cb7d348db07f
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58787545"
---
# <a name="mixin-structure"></a>MixIn — Struktura

Zapewnia, że klasy środowiska uruchomieniowego pochodzi od klasy interfejsów Windows Runtime, jeśli istnieje, a następnie klasycznych interfejsów COM.

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
Typ pochodzący od [implementuje](implements-structure.md) struktury.

*MixInType*<br/>
Typ podstawowy.

*hasImplements*<br/>
**wartość true,** Jeśli *MixInType* jest pochodną bieżąca implementacja parametru typu podstawowego; **false** inaczej.

## <a name="remarks"></a>Uwagi

Jeśli klasa jest pochodną klasy COM, interfejsów i środowiska wykonawczego Windows, lista deklaracji klasy, najpierw musi zawierać żadnych interfejsów Windows Runtime, a następnie wszelkie Klasyczny model COM, interfejsów. **MixIn** gwarantuje, że interfejsy są określone w poprawnej kolejności.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`MixIn`

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL, przestrzeń nazw](microsoft-wrl-namespace.md)