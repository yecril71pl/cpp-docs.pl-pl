---
title: Klasa IRunnableObjectImpl
ms.date: 11/04/2016
f1_keywords:
- IRunnableObjectImpl
- ATLCTL/ATL::IRunnableObjectImpl
- ATLCTL/ATL::IRunnableObjectImpl::GetRunningClass
- ATLCTL/ATL::IRunnableObjectImpl::IsRunning
- ATLCTL/ATL::IRunnableObjectImpl::LockRunning
- ATLCTL/ATL::IRunnableObjectImpl::Run
- ATLCTL/ATL::IRunnableObjectImpl::SetContainedObject
helpviewer_keywords:
- containers, running controls
- IRunnableObjectImpl class
- IRunnableObject, ATL implementation
- controls [ATL], running
- controls [C++], container running in ATL
ms.assetid: 305c7c3b-889e-49dd-aca1-34379c1b9931
ms.openlocfilehash: 44b1e0ae1b72a40b45abe0650eb69a279b5a84d1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62200342"
---
# <a name="irunnableobjectimpl-class"></a>Klasa IRunnableObjectImpl

Ta klasa implementuje `IUnknown` i udostępnia domyślną implementację elementu [IRunnableObject](/windows/desktop/api/objidl/nn-objidl-irunnableobject) interfejsu.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
template<class T>
class IRunnableObjectImpl
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Z klasą pochodną `IRunnableObjectImpl`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IRunnableObjectImpl::GetRunningClass](#getrunningclass)|Zwraca identyfikator CLSID formantu uruchomione. Implementacja biblioteki ATL Ustawia identyfikator CLSID GUID_NULL i zwraca wartość E_UNEXPECTED.|
|[IRunnableObjectImpl::IsRunning](#isrunning)|Określa, czy kontrolka jest uruchomiona. Implementacja biblioteki ATL, zwraca wartość PRAWDA.|
|[IRunnableObjectImpl::LockRunning](#lockrunning)|Formant jest blokowany w stanie uruchomienia. Implementacja biblioteki ATL, zwraca wartość S_OK.|
|[IRunnableObjectImpl::Run](#run)|Wymusza na uruchomienie tego formantu. Implementacja biblioteki ATL, zwraca wartość S_OK.|
|[IRunnableObjectImpl::SetContainedObject](#setcontainedobject)|Wskazuje, że formant jest osadzony. Implementacja biblioteki ATL, zwraca wartość S_OK.|

## <a name="remarks"></a>Uwagi

[IRunnableObject](/windows/desktop/api/objidl/nn-objidl-irunnableobject) interfejs umożliwia kontenera określić, czy formant jest uruchomiona, wymusić, aby uruchomić lub go zablokować w stanie uruchomienia. Klasa `IRunnableObjectImpl` udostępnia domyślną implementację tego interfejsu i implementuje `IUnknown` , wysyłając informacje o do zrzutu kompilacji urządzenia podczas debugowania.

**Powiązane artykuły** [ALT — samouczek](../../atl/active-template-library-atl-tutorial.md), [Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IRunnableObject`

`IRunnableObjectImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlctl.h

##  <a name="getrunningclass"></a>  IRunnableObjectImpl::GetRunningClass

Zwraca identyfikator CLSID formantu uruchomione.

```
HRESULT GetRunningClass(LPCLSID lpClsid);
```

### <a name="return-value"></a>Wartość zwracana

Ustawia implementację ATL \* *lpClsid* GUID_NULL i zwraca wartość E_UNEXPECTED.

### <a name="remarks"></a>Uwagi

Zobacz [IRunnableObject::GetRunningClass](/windows/desktop/api/objidl/nf-objidl-irunnableobject-getrunningclass) w Windows SDK.

##  <a name="isrunning"></a>  IRunnableObjectImpl::IsRunning

Określa, czy kontrolka jest uruchomiona.

```
virtual BOOL IsRunning();
```

### <a name="return-value"></a>Wartość zwracana

Implementacja biblioteki ATL, zwraca wartość PRAWDA.

### <a name="remarks"></a>Uwagi

Zobacz [IRunnableObject::IsRunning](/windows/desktop/api/objidl/nf-objidl-irunnableobject-isrunning) w Windows SDK.

##  <a name="lockrunning"></a>  IRunnableObjectImpl::LockRunning

Formant jest blokowany w stanie uruchomienia.

```
HRESULT LockRunning(BOOL fLock, BOOL fLastUnlockCloses);
```

### <a name="return-value"></a>Wartość zwracana

Implementacja biblioteki ATL, zwraca wartość S_OK.

### <a name="remarks"></a>Uwagi

Zobacz [IRunnableObject::LockRunning](/windows/desktop/api/objidl/nf-objidl-irunnableobject-lockrunning) w Windows SDK.

##  <a name="run"></a>  IRunnableObjectImpl::Run

Wymusza na uruchomienie tego formantu.

```
HRESULT Run(LPBINDCTX lpbc);
```

### <a name="return-value"></a>Wartość zwracana

Implementacja biblioteki ATL, zwraca wartość S_OK.

### <a name="remarks"></a>Uwagi

Zobacz [IRunnableObject::Run](/windows/desktop/api/objidl/nf-objidl-irunnableobject-run) w Windows SDK.

##  <a name="setcontainedobject"></a>  IRunnableObjectImpl::SetContainedObject

Wskazuje, że formant jest osadzony.

```
HRESULT SetContainedObject(BOOL fContained);
```

### <a name="return-value"></a>Wartość zwracana

Implementacja biblioteki ATL, zwraca wartość S_OK.

### <a name="remarks"></a>Uwagi

Zobacz [IRunnableObject::SetContainedObject](/windows/desktop/api/objidl/nf-objidl-irunnableobject-setcontainedobject) w Windows SDK.

## <a name="see-also"></a>Zobacz także

[Klasa CComControl](../../atl/reference/ccomcontrol-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
