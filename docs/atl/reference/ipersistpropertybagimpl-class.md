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
ms.openlocfilehash: 09b0acfc1fc1f9147a6acbe8bbfe66016dc0b54b
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43201705"
---
# <a name="ipersistpropertybagimpl-class"></a>Klasa IPersistPropertyBagImpl
Ta klasa implementuje `IUnknown` i zezwala na obiekt zapisać właściwości zbioru właściwości dostarczonych przez klienta.  
  
> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class T>  
class ATL_NO_VTABLE IPersistPropertyBagImpl : public IPersistPropertyBag
```  
  
#### <a name="parameters"></a>Parametry  
 *T*  
 Z klasą pochodną `IPersistPropertyBagImpl`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IPersistPropertyBagImpl::GetClassID](#getclassid)|Pobiera identyfikator CLSID obiektu.|  
|[IPersistPropertyBagImpl::InitNew](#initnew)|Inicjuje nowo utworzony obiekt. Implementacja biblioteki ATL, zwraca wartość S_OK.|  
|[IPersistPropertyBagImpl::Load](#load)|Ładuje właściwości obiektu ze zbioru właściwości dostarczonych przez klienta.|  
|[IPersistPropertyBagImpl::Save](#save)|Zapisuje właściwości obiektu do zbioru właściwości dostarczonych przez klienta.|  
  
## <a name="remarks"></a>Uwagi  
 [IPersistPropertyBag](https://msdn.microsoft.com/library/aa768205.aspx) interfejs umożliwia obiekt zapisać właściwości zbioru właściwości dostarczonych przez klienta. Klasa `IPersistPropertyBagImpl` udostępnia domyślną implementację tego interfejsu i implementuje `IUnknown` , wysyłając informacje o do zrzutu kompilacji urządzenia podczas debugowania.  
  
 `IPersistPropertyBag` działa w połączeniu z [IPropertyBag](https://msdn.microsoft.com/library/aa768196.aspx) i [IErrorLog](https://msdn.microsoft.com/library/aa768231.aspx). Te ostatnie dwa interfejsy muszą być zaimplementowane przez klienta. Za pomocą `IPropertyBag`, klient zapisuje i ładuje poszczególne właściwości obiektu. Za pomocą `IErrorLog`, zarówno klienta, jak i obiekt zgłosić wszystkich wykrytych błędów.  
  
 **Powiązane artykuły** [ALT — samouczek](../../atl/active-template-library-atl-tutorial.md), [Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md)  
  
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
 Zobacz [IPersist::GetClassID](/windows/desktop/api/objidl/nf-objidl-ipersist-getclassid) w Windows SDK.  
  
##  <a name="initnew"></a>  IPersistPropertyBagImpl::InitNew  
 Inicjuje nowo utworzony obiekt.  
  
```
STDMETHOD(InitNew)();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IPersistPropertyBag::InitNew](https://msdn.microsoft.com/library/aa768204.aspx) w Windows SDK.  
  
##  <a name="load"></a>  IPersistPropertyBagImpl::Load  
 Ładuje właściwości obiektu ze zbioru właściwości dostarczonych przez klienta.  
  
```
STDMETHOD(Load)(LPPROPERTYBAG pPropBag, LPERRORLOG pErrorLog);
```  
  
### <a name="remarks"></a>Uwagi  
 ATL używa map właściwości obiektu do pobrania tych informacji.  
  
 Zobacz [IPersistPropertyBag::Load](https://msdn.microsoft.com/library/aa768206.aspx) w Windows SDK.  
  
##  <a name="save"></a>  IPersistPropertyBagImpl::Save  
 Zapisuje właściwości obiektu do zbioru właściwości dostarczonych przez klienta.  
  
```
STDMETHOD(Save)(
    LPPROPERTYBAG pPropBag,
    BOOL fClearDirty,
    BOOL fSaveAllProperties);
```  
  
### <a name="remarks"></a>Uwagi  
 ATL używa map właściwości obiektu do przechowywania tych informacji. Domyślnie ta metoda zapisuje wszystkie właściwości, bez względu na wartość *fSaveAllProperties*.  
  
 Zobacz [IPersistPropertyBag::Save](https://msdn.microsoft.com/library/aa768207.aspx) w Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [BEGIN_PROP_MAP](property-map-macros.md#begin_prop_map)   
 [Klasa — Przegląd](../../atl/atl-class-overview.md)
