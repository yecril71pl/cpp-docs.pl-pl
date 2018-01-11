---
title: Klasa IPersistStorageImpl | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IPersistStorageImpl
- ATLCOM/ATL::IPersistStorageImpl
- ATLCOM/ATL::IPersistStorageImpl::GetClassID
- ATLCOM/ATL::IPersistStorageImpl::HandsOffStorage
- ATLCOM/ATL::IPersistStorageImpl::InitNew
- ATLCOM/ATL::IPersistStorageImpl::IsDirty
- ATLCOM/ATL::IPersistStorageImpl::Load
- ATLCOM/ATL::IPersistStorageImpl::Save
- ATLCOM/ATL::IPersistStorageImpl::SaveCompleted
dev_langs: C++
helpviewer_keywords:
- storage, ATL
- IPersistStorageImpl class
ms.assetid: d652f02c-239c-47c7-9a50-3e9fc3014fff
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0bb02425c906a9d468d53691469dd7e418afcad3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ipersiststorageimpl-class"></a>Klasa IPersistStorageImpl
Ta klasa implementuje [IPersistStorage](http://msdn.microsoft.com/library/windows/desktop/ms679731) interfejsu.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class T>  
class ATL_NO_VTABLE IPersistStorageImpl : public IPersistStorage
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Z klasą pochodną `IPersistStorageImpl`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IPersistStorageImpl::GetClassID](#getclassid)|Pobiera identyfikator CLSID obiektu.|  
|[IPersistStorageImpl::HandsOffStorage](#handsoffstorage)|Powoduje, że obiekt do zwolnienie wszystkich obiektów magazynu oraz trybu HandsOff. Zwraca implementację ATL `S_OK`.|  
|[IPersistStorageImpl::InitNew](#initnew)|Inicjuje nowego magazynu.|  
|[IPersistStorageImpl::IsDirty](#isdirty)|Sprawdza, czy dane obiektu zostały zmienione od ostatniego zapisu.|  
|[IPersistStorageImpl::Load](#load)|Ładuje właściwości obiektu z określonym magazynu.|  
|[IPersistStorageImpl::Save](#save)|Zapisuje określony magazyn właściwości obiektu.|  
|[IPersistStorageImpl::SaveCompleted](#savecompleted)|Powiadamia obiekt powraca do trybu normalnego można zapisać do jego obiektu magazynu. Zwraca implementację ATL `S_OK`.|  
  
## <a name="remarks"></a>Uwagi  
 `IPersistStorageImpl`implementuje [IPersistStorage](http://msdn.microsoft.com/library/windows/desktop/ms679731) interfejsu, co pozwala klientowi żądanie obciążenia obiektu i zapisz jego przy użyciu magazynu danych.  
  
 Implementacja tej klasy wymaga klasy `T` aby implementacja `IPersistStreamInit` dostępne za pośrednictwem interfejsu `QueryInterface`. Zwykle oznacza to, że klasa `T` powinien pochodzić od [IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md), podaj wpis dotyczący `IPersistStreamInit` w [mapy COM](http://msdn.microsoft.com/library/ead2a1e3-334d-44ad-bb1f-b94bb14c2333)i użyj [mapę właściwości](http://msdn.microsoft.com/library/bfe30be6-62c3-4dc2-bd49-21ef96f15427) do opisywania tej klasy danych.  
  
 **Innych pokrewnych artykułach** [ALT — samouczek](../../atl/active-template-library-atl-tutorial.md), [tworzenie Projekt ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `IPersistStorage`  
  
 `IPersistStorageImpl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  
  
##  <a name="getclassid"></a>IPersistStorageImpl::GetClassID  
 Pobiera identyfikator CLSID obiektu.  
  
```
STDMETHOD(GetClassID)(CLSID* pClassID);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [metody IPersist::GetClassID](http://msdn.microsoft.com/library/windows/desktop/ms688664) w systemie Windows SDK.  
  
##  <a name="handsoffstorage"></a>IPersistStorageImpl::HandsOffStorage  
 Powoduje, że obiekt do zwolnienie wszystkich obiektów magazynu oraz trybu HandsOff.  
  
```
STDMETHOD(HandsOffStorage)(void);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK`.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IPersistStorage::HandsOffStorage](http://msdn.microsoft.com/library/windows/desktop/ms679742) w systemie Windows SDK.  
  
##  <a name="initnew"></a>IPersistStorageImpl::InitNew  
 Inicjuje nowego magazynu.  
  
```
STDMETHOD(InitNew)(IStorage*);
```  
  
### <a name="remarks"></a>Uwagi  
 Implementacja ATL deleguje do [IPersistStreamInit](http://msdn.microsoft.com/library/windows/desktop/ms682273) interfejsu.  
  
 Zobacz [IPersistStorage:InitNew](http://msdn.microsoft.com/library/windows/desktop/ms687194) w systemie Windows SDK.  
  
##  <a name="isdirty"></a>IPersistStorageImpl::IsDirty  
 Sprawdza, czy dane obiektu zostały zmienione od ostatniego zapisu.  
  
```
STDMETHOD(IsDirty)(void);
```  
  
### <a name="remarks"></a>Uwagi  
 Implementacja ATL deleguje do [IPersistStreamInit](http://msdn.microsoft.com/library/windows/desktop/ms682273) interfejsu.  
  
 Zobacz [IPersistStorage:IsDirty](http://msdn.microsoft.com/library/windows/desktop/ms683910) w systemie Windows SDK.  
  
##  <a name="load"></a>IPersistStorageImpl::Load  
 Ładuje właściwości obiektu z określonym magazynu.  
  
```
STDMETHOD(Load)(IStorage* pStorage);
```  
  
### <a name="remarks"></a>Uwagi  
 Implementacja ATL deleguje do [IPersistStreamInit](http://msdn.microsoft.com/library/windows/desktop/ms682273) interfejsu. **Obciążenia** używa strumienia o nazwie "Zawartość" można pobrać danych obiektu. [Zapisać](#save) metoda tworzy pierwotnie tego strumienia.  
  
 Zobacz [IPersistStorage:Load](http://msdn.microsoft.com/library/windows/desktop/ms680557) w systemie Windows SDK.  
  
##  <a name="save"></a>IPersistStorageImpl::Save  
 Zapisuje określony magazyn właściwości obiektu.  
  
```
STDMETHOD(Save)(IStorage* pStorage, BOOL fSameAsLoad);
```  
  
### <a name="remarks"></a>Uwagi  
 Implementacja ATL deleguje do [IPersistStreamInit](http://msdn.microsoft.com/library/windows/desktop/ms682273) interfejsu. Podczas **zapisać** jest pierwszym wywołaniu tworzy strumień o nazwie "Zawartość" w magazynie określonym. Ten strumień jest następnie używany w wywołaniach nowsze **zapisać** i w wywołaniach [obciążenia](#load).  
  
 Zobacz [IPersistStorage:Save](http://msdn.microsoft.com/library/windows/desktop/ms680680) w systemie Windows SDK.  
  
##  <a name="savecompleted"></a>IPersistStorageImpl::SaveCompleted  
 Powiadamia obiekt powraca do trybu normalnego można zapisać do jego obiektu magazynu.  
  
```
STDMETHOD(SaveCompleted)(IStorage*);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK`.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IPersistStorage:SaveCompleted](http://msdn.microsoft.com/library/windows/desktop/ms679713) w systemie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontenery i strumienie](http://msdn.microsoft.com/library/windows/desktop/aa380352)   
 [Klasa IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md)   
 [Klasa IPersistPropertyBagImpl](../../atl/reference/ipersistpropertybagimpl-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
