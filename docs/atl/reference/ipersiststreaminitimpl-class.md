---
title: Klasa IPersistStreamInitImpl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IPersistStreamInitImpl
- ATLCOM/ATL::IPersistStreamInitImpl
- ATLCOM/ATL::IPersistStreamInitImpl::GetClassID
- ATLCOM/ATL::IPersistStreamInitImpl::GetSizeMax
- ATLCOM/ATL::IPersistStreamInitImpl::InitNew
- ATLCOM/ATL::IPersistStreamInitImpl::IsDirty
- ATLCOM/ATL::IPersistStreamInitImpl::Load
- ATLCOM/ATL::IPersistStreamInitImpl::Save
dev_langs:
- C++
helpviewer_keywords:
- IPersistStreamInit ATL implementation
- IPersistStreamInitImpl class
- streams, ATL
ms.assetid: ef217c3c-020f-4cf8-871e-ef68e57865b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b862d6b0fc99184232621432ec1c2a1027f8a9d5
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37881506"
---
# <a name="ipersiststreaminitimpl-class"></a>Klasa IPersistStreamInitImpl
Ta klasa implementuje `IUnknown` i udostępnia domyślną implementację elementu [IPersistStreamInit](http://msdn.microsoft.com/library/windows/desktop/ms682273) interfejsu.  
  
> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template<class T>  
class ATL_NO_VTABLE IPersistStreamInitImpl 
   : public IPersistStreamInit
```  
  
#### <a name="parameters"></a>Parametry  
 *T*  
 Z klasą pochodną `IPersistStreamInitImpl`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IPersistStreamInitImpl::GetClassID](#getclassid)|Pobiera identyfikator CLSID obiektu.|  
|[IPersistStreamInitImpl::GetSizeMax](#getsizemax)|Pobiera rozmiar strumienia potrzebnych do zapisania danych obiektu. Implementacja biblioteki ATL zwraca E_NOTIMPL.|  
|[IPersistStreamInitImpl::InitNew](#initnew)|Inicjuje nowo utworzony obiekt.|  
|[IPersistStreamInitImpl::IsDirty](#isdirty)|Sprawdza, czy danych obiektu został zmieniony od ostatniego zapisu.|  
|[IPersistStreamInitImpl::Load](#load)|Ładuje właściwości obiektu z określonego strumienia.|  
|[IPersistStreamInitImpl::Save](#save)|Zapisuje właściwości obiektu do określonego strumienia.|  
  
## <a name="remarks"></a>Uwagi  
 [IPersistStreamInit](http://msdn.microsoft.com/library/windows/desktop/ms682273) interfejs umożliwia klientowi żądanie czy obiekt ładuje i zapisuje jego trwałych danych na jednym strumień. Klasa `IPersistStreamInitImpl` udostępnia domyślną implementację tego interfejsu i implementuje `IUnknown` , wysyłając informacje o do zrzutu kompilacji urządzenia podczas debugowania.  
  
 **Powiązane artykuły** [ALT — samouczek](../../atl/active-template-library-atl-tutorial.md), [Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `IPersistStreamInit`  
  
 `IPersistStreamInitImpl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  
  
##  <a name="getclassid"></a>  IPersistStreamInitImpl::GetClassID  
 Pobiera identyfikator CLSID obiektu.  
  
```
STDMETHOD(GetClassID)(CLSID* pClassID);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IPersist::GetClassID](http://msdn.microsoft.com/library/windows/desktop/ms688664) w Windows SDK.  
  
##  <a name="getsizemax"></a>  IPersistStreamInitImpl::GetSizeMax  
 Pobiera rozmiar strumienia potrzebnych do zapisania danych obiektu.  
  
```
STDMETHOD(GetSizeMax)(ULARGE_INTEGER FAR* pcbSize);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca E_NOTIMPL.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IPersistStreamInit::GetSizeMax](http://msdn.microsoft.com/library/windows/desktop/ms687287) w Windows SDK.  
  
##  <a name="initnew"></a>  IPersistStreamInitImpl::InitNew  
 Inicjuje nowo utworzony obiekt.  
  
```
STDMETHOD(InitNew)();
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IPersistStreamInit::InitNew](http://msdn.microsoft.com/library/windows/desktop/ms690234) w Windows SDK.  
  
##  <a name="isdirty"></a>  IPersistStreamInitImpl::IsDirty  
 Sprawdza, czy danych obiektu został zmieniony od ostatniego zapisu.  
  
```
STDMETHOD(IsDirty)();
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IPersistStreamInit::IsDirty](http://msdn.microsoft.com/library/windows/desktop/ms680092) w Windows SDK.  
  
##  <a name="load"></a>  IPersistStreamInitImpl::Load  
 Ładuje właściwości obiektu z określonego strumienia.  
  
```
STDMETHOD(Load)(LPSTREAM pStm);
```  
  
### <a name="remarks"></a>Uwagi  
 ATL używa map właściwości obiektu do pobrania tych informacji.  
  
 Zobacz [IPersistStreamInit::Load](http://msdn.microsoft.com/library/windows/desktop/ms680730) w Windows SDK.  
  
##  <a name="save"></a>  IPersistStreamInitImpl::Save  
 Zapisuje właściwości obiektu do określonego strumienia.  
  
```
STDMETHOD(Save)(LPSTREAM pStm, BOOL fClearDirty);
```  
  
### <a name="remarks"></a>Uwagi  
 ATL używa map właściwości obiektu do przechowywania tych informacji.  
  
 Zobacz [IPersistStreamInit::Save](http://msdn.microsoft.com/library/windows/desktop/ms694439) w Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontenery i strumienie](http://msdn.microsoft.com/library/windows/desktop/aa380352)   
 [Klasa — Przegląd](../../atl/atl-class-overview.md)
