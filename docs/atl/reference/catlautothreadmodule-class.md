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
ms.openlocfilehash: 9c89d142254909591ebd01bfa859be5488cbfaf6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32356621"
---
# <a name="catlautothreadmodule-class"></a>Klasa CAtlAutoThreadModule
Ta klasa implementuje wątków w puli, modelu typu apartment serwer COM.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
class CAtlAutoThreadModule : public CAtlAutoThreadModuleT<CAtlAutoThreadModule>
```  
  
## <a name="remarks"></a>Uwagi  
 `CAtlAutoThreadModule` pochodną [CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md) i implementuje wątków w puli, modelu typu apartment serwer COM. `CAtlAutoThreadModule` używa [CComApartment](../../atl/reference/ccomapartment-class.md) do zarządzania apartamentu dla każdego wątku w module.  
  
 Należy użyć [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) makra w definicji klasy do obiektu, aby określić [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) jako fabryki klasy. Następnie należy dodać jedno wystąpienie klasy pochodzącej od `CAtlAutoThreadModuleT` takich jak `CAtlAutoThreadModule`. Na przykład:  
  
 `CAtlAutoThreadModule _AtlAutoModule; // name is immaterial.`  
  
> [!NOTE]
>  Ta klasa zastępuje przestarzałe [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md) klasy.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `IAtlAutoThreadModule`  
  
 [CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)  
  
 `CAtlAutoThreadModule`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlbase.h  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)   
 [Klasa IAtlAutoThreadModule](../../atl/reference/iatlautothreadmodule-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)   
 [Klasy modułów](../../atl/atl-module-classes.md)
