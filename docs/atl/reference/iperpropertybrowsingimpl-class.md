---
title: Klasa IPerPropertyBrowsingImpl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IPerPropertyBrowsingImpl
- ATLCTL/ATL::IPerPropertyBrowsingImpl
- ATLCTL/ATL::IPerPropertyBrowsingImpl::GetDisplayString
- ATLCTL/ATL::IPerPropertyBrowsingImpl::GetPredefinedStrings
- ATLCTL/ATL::IPerPropertyBrowsingImpl::GetPredefinedValue
- ATLCTL/ATL::IPerPropertyBrowsingImpl::MapPropertyToPage
dev_langs:
- C++
helpviewer_keywords:
- IPerPropertyBrowsingImpl class
- property pages, accessing information
- IPerPropertyBrowsing, ATL implementation
ms.assetid: 0b1a9be3-d242-4767-be69-663a21e4b728
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2d9fffd6151405eaf53e99f770281139d7664b01
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32364911"
---
# <a name="iperpropertybrowsingimpl-class"></a>Klasa IPerPropertyBrowsingImpl
Ta klasa implementuje **IUnknown** i umożliwia klientom dostęp do informacji na stronach właściwości obiektu.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```

template <class T>
class ATL_NO_VTABLE IPerPropertyBrowsingImpl :
    public IPerPropertyBrowsing
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Z klasą pochodną `IPerPropertyBrowsingImpl`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IPerPropertyBrowsingImpl::GetDisplayString](#getdisplaystring)|Pobiera ciąg opisujący danej właściwości.|  
|[IPerPropertyBrowsingImpl::GetPredefinedStrings](#getpredefinedstrings)|Pobiera tablicę ciągów odpowiadających wartościom akceptujących dla danej właściwości.|  
|[IPerPropertyBrowsingImpl::GetPredefinedValue](#getpredefinedvalue)|Pobiera **VARIANT** zawierające wartości właściwości identyfikowane przez dany identyfikator DISPID. Identyfikator DISPID jest skojarzony z nazwą ciągu pobierane z `GetPredefinedStrings`. Zwraca implementację ATL **E_NOTIMPL**.|  
|[IPerPropertyBrowsingImpl::MapPropertyToPage](#mappropertytopage)|Pobiera identyfikator CLSID strony właściwości skojarzone z danej właściwości.|  
  
## <a name="remarks"></a>Uwagi  
 [IPerPropertyBrowsing](http://msdn.microsoft.com/library/windows/desktop/ms678432) interfejs umożliwia klientom dostęp do informacji na stronach właściwości obiektu. Klasa `IPerPropertyBrowsingImpl` udostępnia domyślną implementację tego interfejsu i implementuje **IUnknown** , wysyłając informacje o do zrzutu kompilacje urządzenia podczas debugowania.  
  
> [!NOTE]
>  Jeśli używasz programu Microsoft Access jako aplikacji kontenera, musi pochodzić z klasy `IPerPropertyBrowsingImpl`. W przeciwnym razie dostęp nie zostanie załadowany formantu.  
  
 **Innych pokrewnych artykułach** [ALT — samouczek](../../atl/active-template-library-atl-tutorial.md), [tworzenie Projekt ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `IPerPropertyBrowsing`  
  
 `IPerPropertyBrowsingImpl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlctl.h  
  
##  <a name="getdisplaystring"></a>  IPerPropertyBrowsingImpl::GetDisplayString  
 Pobiera ciąg opisujący danej właściwości.  
  
```
STDMETHOD(GetDisplayString)(
    DISPID dispID,
    BSTR* pBstr);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IPerPropertyBrowsing::GetDisplayString](http://msdn.microsoft.com/library/windows/desktop/ms688734) w systemie Windows SDK.  
  
##  <a name="getpredefinedstrings"></a>  IPerPropertyBrowsingImpl::GetPredefinedStrings  
 Wypełnia każdej macierzy z elementami zero.  
  
```
STDMETHOD(GetPredefinedStrings)(
    DISPID dispID,
    CALPOLESTR* pCaStringsOut,
    CADWORD* pCaCookiesOut);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Implementacja na ATL [GetPredefinedValue](#getpredefinedvalue) zwraca **E_NOTIMPL**.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IPerPropertyBrowsing::GetPredefinedStrings](http://msdn.microsoft.com/library/windows/desktop/ms679724) w systemie Windows SDK.  
  
##  <a name="getpredefinedvalue"></a>  IPerPropertyBrowsingImpl::GetPredefinedValue  
 Pobiera **VARIANT** zawierające wartości właściwości identyfikowane przez dany identyfikator DISPID. Identyfikator DISPID jest skojarzony z nazwą ciągu pobierane z `GetPredefinedStrings`.  
  
```
STDMETHOD(GetPredefinedValue)(
    DISPID dispID,
    DWORD dwCookie,
    VARIANT* pVarOut);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **E_NOTIMPL**.  
  
### <a name="remarks"></a>Uwagi  
 Implementacja na ATL [GetPredefinedStrings](#getpredefinedstrings) pobiera nie odpowiednie ciągi.  
  
 Zobacz [IPerPropertyBrowsing::GetPredefinedValue](http://msdn.microsoft.com/library/windows/desktop/ms690401) w systemie Windows SDK.  
  
##  <a name="mappropertytopage"></a>  IPerPropertyBrowsingImpl::MapPropertyToPage  
 Pobiera identyfikator CLSID strony właściwości skojarzone z określonej właściwości.  
  
```
STDMETHOD(MapPropertyToPage)(
    DISPID dispID,
    CLSID* pClsid);
```  
  
### <a name="remarks"></a>Uwagi  
 ATL używa obiektu właściwości mapy w celu uzyskania tych informacji.  
  
 Zobacz [IPerPropertyBrowsing::MapPropertyToPage](http://msdn.microsoft.com/library/windows/desktop/ms694476) w systemie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)   
 [Klasa ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
