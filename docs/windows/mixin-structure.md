---
title: Mixin — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::MixIn
dev_langs:
- C++
helpviewer_keywords:
- MixIn structure
ms.assetid: 47e2df9b-3a2e-4ae8-8ba3-b1fd3aa73566
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1b6aa9b8e27aa4eaf3e581db59f2c9d2c7201d39
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46386800"
---
# <a name="mixin-structure"></a>MixIn — Struktura

Zapewnia, że klasy środowiska uruchomieniowego pochodzi od klasy interfejsów Windows Runtime, jeśli istnieje, a następnie klasycznych interfejsów COM.

## <a name="syntax"></a>Składnia

```cpp
template<
   typename Derived,
   typename MixInType,
   bool hasImplements = __is_base_of(Details::ImplementsBase,
   MixInType)  
>
struct MixIn;
```

### <a name="parameters"></a>Parametry

*Pochodne*<br/>
Typ pochodzący od [implementuje](../windows/implements-structure.md) struktury.

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

[Microsoft::WRL, przestrzeń nazw](../windows/microsoft-wrl-namespace.md)