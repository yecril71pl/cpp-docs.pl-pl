---
title: Klasa IPropertyPage2Impl | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IPropertyPage2Impl
- ATLCTL/ATL::IPropertyPage2Impl
- ATLCTL/ATL::IPropertyPage2Impl::EditProperty
dev_langs: C++
helpviewer_keywords:
- property pages
- IPropertyPage2 ATL implementation
- IPropertyPage2Impl class
ms.assetid: e89fbe90-203a-47f0-a5de-23616697e1ce
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 40cdaeef31226cf47dcf4beb08f11242932578c6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ipropertypage2impl-class"></a>Klasa IPropertyPage2Impl
Ta klasa implementuje **IUnknown** i dziedziczy Domyślna implementacja [IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md).  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template<class T>  
class IPropertyPage2Impl : public IPropertyPageImpl<T>
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Z klasą pochodną `IPropertyPage2Impl`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IPropertyPage2Impl::EditProperty](#editproperty)|Określa, które właściwości kontrolki otrzyma fokus, po aktywowaniu stronę właściwości. Zwraca implementację ATL **E_NOTIMPL**.|  
  
## <a name="remarks"></a>Uwagi  
 [IPropertyPage2](http://msdn.microsoft.com/library/windows/desktop/ms683996) rozszerza interfejs [IPropertyPage](http://msdn.microsoft.com/library/windows/desktop/ms691246) przez dodanie `EditProperty` metody. Ta metoda umożliwia klientowi wybierz konkretną właściwością w obiekcie strony właściwości.  
  
 Klasa `IPropertyPage2Impl` po prostu zwraca **E_NOTIMPL** dla **IPropertyPage2::EditProperty**. Jednak dziedziczy Domyślna implementacja [IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md) i implementuje **IUnknown** , wysyłając informacje o do zrzutu kompilacje urządzenia podczas debugowania.  
  
 Po utworzeniu strony właściwości zwykle jest pochodną klasy `IPropertyPageImpl`. Zapewnienie dodatkowego pomocy technicznej dla **IPropertyPage2**, należy zmodyfikować definicję klasy i zastąpić `EditProperty` metody.  
  
 **Innych pokrewnych artykułach** [ALT — samouczek](../../atl/active-template-library-atl-tutorial.md), [tworzenie Projekt ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `IPropertyPage`  
  
 [IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)  
  
 `IPropertyPage2Impl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlctl.h  
  
##  <a name="editproperty"></a>IPropertyPage2Impl::EditProperty  
 Określa, które właściwości kontrolki otrzyma fokus, po aktywowaniu stronę właściwości.  
  
```
HRESULT EditProperty(DISPID dispID);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **E_NOTIMPL**.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IPropertyPage2::EditProperty](http://msdn.microsoft.com/library/windows/desktop/ms690353) w systemie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md)   
 [Klasa ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
