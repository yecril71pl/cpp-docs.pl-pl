---
title: Klasa CAtlAutoThreadModule | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAtlAutoThreadModule
- atlbase/ATL::CAtlAutoThreadModule
dev_langs:
- C++
helpviewer_keywords:
- CAtlAutoThreadModule class
ms.assetid: 3be834aa-55ef-403e-94ae-41979691b15f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 882a32b1a9f08f3fd07f1d53d508b101c5500f5d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46037063"
---
# <a name="catlautothreadmodule-class"></a>Klasa CAtlAutoThreadModule

Ta klasa implementuje serwer COM wątków w puli, model przedziału.

> [!IMPORTANT]
> Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
class CAtlAutoThreadModule : public CAtlAutoThreadModuleT<CAtlAutoThreadModule>
```

## <a name="remarks"></a>Uwagi

`CAtlAutoThreadModule` pochodzi od klasy [CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md) i implementuje serwer COM wątków w puli, model przedziału. `CAtlAutoThreadModule` używa [CComApartment](../../atl/reference/ccomapartment-class.md) Zarządzanie apartament dla każdego wątku w module.

Należy użyć [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) makra w definicji klasy do obiektu, aby określić [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) jako fabryki klas. Następnie należy dodać jedno wystąpienie klasy pochodzącej od `CAtlAutoThreadModuleT` takich jak `CAtlAutoThreadModule`. Na przykład:

`CAtlAutoThreadModule _AtlAutoModule; // name is immaterial.`

> [!NOTE]
> Ta klasa zastępuje przestarzałe [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md) klasy.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IAtlAutoThreadModule`

[CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)

`CAtlAutoThreadModule`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

## <a name="see-also"></a>Zobacz też

[Klasa CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)<br/>
[Klasa IAtlAutoThreadModule](../../atl/reference/iatlautothreadmodule-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)<br/>
[Klasy modułów](../../atl/atl-module-classes.md)
