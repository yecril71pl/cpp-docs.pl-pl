---
title: Klasa IPersistStreamInitImpl | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
helpviewer_keywords:
- IPersistStreamInit ATL implementation
- IPersistStreamInitImpl class
- streams, ATL
ms.assetid: ef217c3c-020f-4cf8-871e-ef68e57865b8
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 34208bb376f374f72bf3eb88ead6e10b2f1a7c20
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ipersiststreaminitimpl-class"></a>Klasa IPersistStreamInitImpl
Ta klasa implementuje **IUnknown** i udostępnia domyślną implementację elementu [IPersistStreamInit](http://msdn.microsoft.com/library/windows/desktop/ms682273) interfejsu.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template<class T>  
class ATL_NO_VTABLE IPersistStreamInitImpl 
   : public IPersistStreamInit
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Z klasą pochodną `IPersistStreamInitImpl`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IPersistStreamInitImpl::GetClassID](#getclassid)|Pobiera identyfikator CLSID obiektu.|  
|[IPersistStreamInitImpl::GetSizeMax](#getsizemax)|Pobiera rozmiar strumienia potrzebnych do zapisania danych obiektu. Zwraca implementację ATL **E_NOTIMPL**.|  
|[IPersistStreamInitImpl::InitNew](#initnew)|Inicjuje nowo utworzony obiekt.|  
|[IPersistStreamInitImpl::IsDirty](#isdirty)|Sprawdza, czy dane obiektu zostały zmienione od ostatniego zapisu.|  
|[IPersistStreamInitImpl::Load](#load)|Ładuje właściwości obiektu z określonego strumienia.|  
|[IPersistStreamInitImpl::Save](#save)|Zapisuje właściwości obiektu do określonego strumienia.|  
  
## <a name="remarks"></a>Uwagi  
 [IPersistStreamInit](http://msdn.microsoft.com/library/windows/desktop/ms682273) interfejs umożliwia klientowi żądania, że obiekt załadowanie i zapisanie jej trwałych danych do jednego strumienia. Klasa `IPersistStreamInitImpl` udostępnia domyślną implementację tego interfejsu i implementuje **IUnknown** , wysyłając informacje o do zrzutu kompilacje urządzenia podczas debugowania.  
  
 **Innych pokrewnych artykułach** [ALT — samouczek](../../atl/active-template-library-atl-tutorial.md), [tworzenie Projekt ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `IPersistStreamInit`  
  
 `IPersistStreamInitImpl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  
  
##  <a name="getclassid"></a>IPersistStreamInitImpl::GetClassID  
 Pobiera identyfikator CLSID obiektu.  
  
```
STDMETHOD(GetClassID)(CLSID* pClassID);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [metody IPersist::GetClassID](http://msdn.microsoft.com/library/windows/desktop/ms688664) w systemie Windows SDK.  
  
##  <a name="getsizemax"></a>IPersistStreamInitImpl::GetSizeMax  
 Pobiera rozmiar strumienia potrzebnych do zapisania danych obiektu.  
  
```
STDMETHOD(GetSizeMax)(ULARGE_INTEGER FAR* pcbSize);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **E_NOTIMPL**.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IPersistStreamInit::GetSizeMax](http://msdn.microsoft.com/library/windows/desktop/ms687287) w systemie Windows SDK.  
  
##  <a name="initnew"></a>IPersistStreamInitImpl::InitNew  
 Inicjuje nowo utworzony obiekt.  
  
```
STDMETHOD(InitNew)();
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IPersistStreamInit::InitNew](http://msdn.microsoft.com/library/windows/desktop/ms690234) w systemie Windows SDK.  
  
##  <a name="isdirty"></a>IPersistStreamInitImpl::IsDirty  
 Sprawdza, czy dane obiektu zostały zmienione od ostatniego zapisu.  
  
```
STDMETHOD(IsDirty)();
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IPersistStreamInit::IsDirty](http://msdn.microsoft.com/library/windows/desktop/ms680092) w systemie Windows SDK.  
  
##  <a name="load"></a>IPersistStreamInitImpl::Load  
 Ładuje właściwości obiektu z określonego strumienia.  
  
```
STDMETHOD(Load)(LPSTREAM pStm);
```  
  
### <a name="remarks"></a>Uwagi  
 ATL używa mapę właściwości obiektu do pobrania tych informacji.  
  
 Zobacz [IPersistStreamInit::Load](http://msdn.microsoft.com/library/windows/desktop/ms680730) w systemie Windows SDK.  
  
##  <a name="save"></a>IPersistStreamInitImpl::Save  
 Zapisuje właściwości obiektu do określonego strumienia.  
  
```
STDMETHOD(Save)(LPSTREAM pStm, BOOL fClearDirty);
```  
  
### <a name="remarks"></a>Uwagi  
 ATL używa mapę właściwości obiektu do przechowywania tych informacji.  
  
 Zobacz [IPersistStreamInit::Save](http://msdn.microsoft.com/library/windows/desktop/ms694439) w systemie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontenery i strumienie](http://msdn.microsoft.com/library/windows/desktop/aa380352)   
 [Przegląd klas](../../atl/atl-class-overview.md)
