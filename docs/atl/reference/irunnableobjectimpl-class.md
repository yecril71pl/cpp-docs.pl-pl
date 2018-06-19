---
title: Klasa IRunnableObjectImpl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IRunnableObjectImpl
- ATLCTL/ATL::IRunnableObjectImpl
- ATLCTL/ATL::IRunnableObjectImpl::GetRunningClass
- ATLCTL/ATL::IRunnableObjectImpl::IsRunning
- ATLCTL/ATL::IRunnableObjectImpl::LockRunning
- ATLCTL/ATL::IRunnableObjectImpl::Run
- ATLCTL/ATL::IRunnableObjectImpl::SetContainedObject
dev_langs:
- C++
helpviewer_keywords:
- containers, running controls
- IRunnableObjectImpl class
- IRunnableObject, ATL implementation
- controls [ATL], running
- controls [C++], container running in ATL
ms.assetid: 305c7c3b-889e-49dd-aca1-34379c1b9931
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a08fec0fd38e30729c9131def1831e5e5d8f633e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32364118"
---
# <a name="irunnableobjectimpl-class"></a>Klasa IRunnableObjectImpl
Ta klasa implementuje **IUnknown** i udostępnia domyślną implementację elementu [IRunnableObject](http://msdn.microsoft.com/library/windows/desktop/ms692783) interfejsu.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template<class T>  
class IRunnableObjectImpl
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Z klasą pochodną `IRunnableObjectImpl`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IRunnableObjectImpl::GetRunningClass](#getrunningclass)|Zwraca identyfikator CLSID uruchomionych formantu. Implementacja ATL Ustawia identyfikator CLSID `GUID_NULL` i zwraca **E_UNEXPECTED**.|  
|[IRunnableObjectImpl::IsRunning](#isrunning)|Określa, czy formant jest uruchomiony. Zwraca implementację ATL **TRUE**.|  
|[IRunnableObjectImpl::LockRunning](#lockrunning)|Formant jest blokowany w stanie uruchomienia. Zwraca implementację ATL `S_OK`.|  
|[IRunnableObjectImpl::Run](#run)|Wymusza na uruchomienie tego formantu. Zwraca implementację ATL `S_OK`.|  
|[IRunnableObjectImpl::SetContainedObject](#setcontainedobject)|Wskazuje, że kontrolka jest osadzony. Zwraca implementację ATL `S_OK`.|  
  
## <a name="remarks"></a>Uwagi  
 [IRunnableObject](http://msdn.microsoft.com/library/windows/desktop/ms692783) interfejs umożliwia kontenera ustalić, czy formant jest uruchomiony, wymusić uruchomienia lub go zablokować w stanie uruchomienia. Klasa `IRunnableObjectImpl` udostępnia domyślną implementację tego interfejsu i implementuje **IUnknown** , wysyłając informacje o do zrzutu kompilacje urządzenia podczas debugowania.  
  
 **Innych pokrewnych artykułach** [ALT — samouczek](../../atl/active-template-library-atl-tutorial.md), [tworzenie Projekt ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `IRunnableObject`  
  
 `IRunnableObjectImpl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlctl.h  
  
##  <a name="getrunningclass"></a>  IRunnableObjectImpl::GetRunningClass  
 Zwraca identyfikator CLSID uruchomionych formantu.  
  
```
HRESULT GetRunningClass(LPCLSID lpClsid);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Ustawia implementację ATL \* *lpClsid* do `GUID_NULL` i zwraca **E_UNEXPECTED**.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IRunnableObject::GetRunningClass](http://msdn.microsoft.com/library/windows/desktop/ms693734) w systemie Windows SDK.  
  
##  <a name="isrunning"></a>  IRunnableObjectImpl::IsRunning  
 Określa, czy formant jest uruchomiony.  
  
```
virtual BOOL IsRunning();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca implementację ATL **TRUE**.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IRunnableObject::IsRunning](http://msdn.microsoft.com/library/windows/desktop/ms678496) w systemie Windows SDK.  
  
##  <a name="lockrunning"></a>  IRunnableObjectImpl::LockRunning  
 Formant jest blokowany w stanie uruchomienia.  
  
```
HRESULT LockRunning(BOOL fLock, BOOL fLastUnlockCloses);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca implementację ATL `S_OK`.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IRunnableObject::LockRunning](http://msdn.microsoft.com/library/windows/desktop/ms693361) w systemie Windows SDK.  
  
##  <a name="run"></a>  IRunnableObjectImpl::Run  
 Wymusza na uruchomienie tego formantu.  
  
```
HRESULT Run(LPBINDCTX lpbc);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca implementację ATL `S_OK`.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IRunnableObject::Run](http://msdn.microsoft.com/library/windows/desktop/ms694517) w systemie Windows SDK.  
  
##  <a name="setcontainedobject"></a>  IRunnableObjectImpl::SetContainedObject  
 Wskazuje, że kontrolka jest osadzony.  
  
```
HRESULT SetContainedObject(BOOL fContained);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca implementację ATL `S_OK`.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IRunnableObject::SetContainedObject](http://msdn.microsoft.com/library/windows/desktop/ms693710) w systemie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CComControl](../../atl/reference/ccomcontrol-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
