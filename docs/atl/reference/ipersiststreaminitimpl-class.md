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
ms.openlocfilehash: f71ed0ca185d7806c12ce089589ce4fad7a26e61
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43202619"
---
# <a name="ipersiststreaminitimpl-class"></a>Klasa IPersistStreamInitImpl
Ta klasa implementuje `IUnknown` i udostępnia domyślną implementację elementu [IPersistStreamInit](/windows/desktop/api/ocidl/nn-ocidl-ipersiststreaminit) interfejsu.  
  
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
 [IPersistStreamInit](/windows/desktop/api/ocidl/nn-ocidl-ipersiststreaminit) interfejs umożliwia klientowi żądanie czy obiekt ładuje i zapisuje jego trwałych danych na jednym strumień. Klasa `IPersistStreamInitImpl` udostępnia domyślną implementację tego interfejsu i implementuje `IUnknown` , wysyłając informacje o do zrzutu kompilacji urządzenia podczas debugowania.  
  
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
 Zobacz [IPersist::GetClassID](/windows/desktop/api/objidl/nf-objidl-ipersist-getclassid) w Windows SDK.  
  
##  <a name="getsizemax"></a>  IPersistStreamInitImpl::GetSizeMax  
 Pobiera rozmiar strumienia potrzebnych do zapisania danych obiektu.  
  
```
STDMETHOD(GetSizeMax)(ULARGE_INTEGER FAR* pcbSize);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca E_NOTIMPL.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IPersistStreamInit::GetSizeMax](/windows/desktop/api/ocidl/nf-ocidl-ipersiststreaminit-getsizemax) w Windows SDK.  
  
##  <a name="initnew"></a>  IPersistStreamInitImpl::InitNew  
 Inicjuje nowo utworzony obiekt.  
  
```
STDMETHOD(InitNew)();
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IPersistStreamInit::InitNew](/windows/desktop/api/ocidl/nf-ocidl-ipersiststreaminit-initnew) w Windows SDK.  
  
##  <a name="isdirty"></a>  IPersistStreamInitImpl::IsDirty  
 Sprawdza, czy danych obiektu został zmieniony od ostatniego zapisu.  
  
```
STDMETHOD(IsDirty)();
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IPersistStreamInit::IsDirty](/windows/desktop/api/ocidl/nf-ocidl-ipersiststreaminit-isdirty) w Windows SDK.  
  
##  <a name="load"></a>  IPersistStreamInitImpl::Load  
 Ładuje właściwości obiektu z określonego strumienia.  
  
```
STDMETHOD(Load)(LPSTREAM pStm);
```  
  
### <a name="remarks"></a>Uwagi  
 ATL używa map właściwości obiektu do pobrania tych informacji.  
  
 Zobacz [IPersistStreamInit::Load](/windows/desktop/api/ocidl/nf-ocidl-ipersiststreaminit-load) w Windows SDK.  
  
##  <a name="save"></a>  IPersistStreamInitImpl::Save  
 Zapisuje właściwości obiektu do określonego strumienia.  
  
```
STDMETHOD(Save)(LPSTREAM pStm, BOOL fClearDirty);
```  
  
### <a name="remarks"></a>Uwagi  
 ATL używa map właściwości obiektu do przechowywania tych informacji.  
  
 Zobacz [IPersistStreamInit::Save](/windows/desktop/api/ocidl/nf-ocidl-ipersiststreaminit-save) w Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontenery i strumienie](/windows/desktop/Stg/storages-and-streams)   
 [Klasa — Przegląd](../../atl/atl-class-overview.md)
