---
title: Klasa IPersistPropertyBagImpl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IPersistPropertyBagImpl
- ATLCOM/ATL::IPersistPropertyBagImpl
- ATLCOM/ATL::IPersistPropertyBagImpl::GetClassID
- ATLCOM/ATL::IPersistPropertyBagImpl::InitNew
- ATLCOM/ATL::IPersistPropertyBagImpl::Load
- ATLCOM/ATL::IPersistPropertyBagImpl::Save
dev_langs:
- C++
helpviewer_keywords:
- IPersistPropertyBagImpl class
ms.assetid: 712af24d-99f8-40f2-9811-53b3ff6e5b19
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 41d26b84fd4c113120afefd572caed8ab27214c8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ipersistpropertybagimpl-class"></a>Klasa IPersistPropertyBagImpl
Ta klasa implementuje **IUnknown** i umożliwia obiekt, aby zapisać właściwości zbioru właściwości dostarczonych przez klienta.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class T>  
class ATL_NO_VTABLE IPersistPropertyBagImpl : public IPersistPropertyBag
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Z klasą pochodną `IPersistPropertyBagImpl`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IPersistPropertyBagImpl::GetClassID](#getclassid)|Pobiera identyfikator CLSID obiektu.|  
|[IPersistPropertyBagImpl::InitNew](#initnew)|Inicjuje nowo utworzony obiekt. Zwraca implementację ATL `S_OK`.|  
|[IPersistPropertyBagImpl::Load](#load)|Ładuje właściwości obiektu ze zbioru właściwości dostarczonych przez klienta.|  
|[IPersistPropertyBagImpl::Save](#save)|Zapisuje właściwości obiektu do zbioru właściwości dostarczonych przez klienta.|  
  
## <a name="remarks"></a>Uwagi  
 [IPersistPropertyBag](https://msdn.microsoft.com/library/aa768205.aspx) interfejs umożliwiający obiekt, aby zapisać właściwości zbioru właściwości dostarczonych przez klienta. Klasa `IPersistPropertyBagImpl` udostępnia domyślną implementację tego interfejsu i implementuje **IUnknown** , wysyłając informacje o do zrzutu kompilacje urządzenia podczas debugowania.  
  
 **IPersistPropertyBag** działa w połączeniu z [IPropertyBag](https://msdn.microsoft.com/library/aa768196.aspx) i [IErrorLog](https://msdn.microsoft.com/library/aa768231.aspx). Te ostatnie dwa interfejsy musi być implementowana przez klienta. Za pomocą `IPropertyBag`, klient jest zapisywany i ładuje poszczególnych właściwości obiektu. Za pomocą **IErrorLog**, zarówno obiekt, jak i klienta może raportować napotkano błędy.  
  
 **Innych pokrewnych artykułach** [ALT — samouczek](../../atl/active-template-library-atl-tutorial.md), [tworzenie Projekt ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `IPersistPropertyBag`  
  
 `IPersistPropertyBagImpl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  
  
##  <a name="getclassid"></a>  IPersistPropertyBagImpl::GetClassID  
 Pobiera identyfikator CLSID obiektu.  
  
```
STDMETHOD(GetClassID)(CLSID* pClassID);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [metody IPersist::GetClassID](http://msdn.microsoft.com/library/windows/desktop/ms688664) w systemie Windows SDK.  
  
##  <a name="initnew"></a>  IPersistPropertyBagImpl::InitNew  
 Inicjuje nowo utworzony obiekt.  
  
```
STDMETHOD(InitNew)();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK`.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IPersistPropertyBag::InitNew](https://msdn.microsoft.com/library/aa768204.aspx) w systemie Windows SDK.  
  
##  <a name="load"></a>  IPersistPropertyBagImpl::Load  
 Ładuje właściwości obiektu ze zbioru właściwości dostarczonych przez klienta.  
  
```
STDMETHOD(Load)(LPPROPERTYBAG pPropBag, LPERRORLOG pErrorLog);
```  
  
### <a name="remarks"></a>Uwagi  
 ATL używa mapę właściwości obiektu do pobrania tych informacji.  
  
 Zobacz [IPersistPropertyBag::Load](https://msdn.microsoft.com/library/aa768206.aspx) w systemie Windows SDK.  
  
##  <a name="save"></a>  IPersistPropertyBagImpl::Save  
 Zapisuje właściwości obiektu do zbioru właściwości dostarczonych przez klienta.  
  
```
STDMETHOD(Save)(
    LPPROPERTYBAG pPropBag,
    BOOL fClearDirty,
    BOOL fSaveAllProperties);
```  
  
### <a name="remarks"></a>Uwagi  
 ATL używa mapę właściwości obiektu do przechowywania tych informacji. Domyślnie ta metoda zapisuje wszystkie właściwości, niezależnie od wartości *fSaveAllProperties*.  
  
 Zobacz [IPersistPropertyBag::Save](https://msdn.microsoft.com/library/aa768207.aspx) w systemie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [BEGIN_PROP_MAP](property-map-macros.md#begin_prop_map)   
 [Przegląd klas](../../atl/atl-class-overview.md)
