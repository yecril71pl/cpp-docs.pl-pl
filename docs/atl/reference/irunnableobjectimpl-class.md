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
ms.openlocfilehash: 6b1af7c21c6f5028ad6d3a228cb22650fa3cef42
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495669"
---
# <a name="irunnableobjectimpl-class"></a>Klasa IRunnableObjectImpl

Ta klasa implementuje `IUnknown` i udostępnia domyślną implementację interfejsu [IRunnableObject](/windows/win32/api/objidl/nn-objidl-irunnableobject) .

> [!IMPORTANT]
>  Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```
template<class T>
class IRunnableObjectImpl
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Klasa, która pochodzi od `IRunnableObjectImpl`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IRunnableObjectImpl::GetRunningClass](#getrunningclass)|Zwraca identyfikator CLSID uruchomionej kontrolki. Implementacja ATL ustawia identyfikator CLSID na GUID_NULL i zwraca E_UNEXPECTED.|
|[IRunnableObjectImpl:: IsRunning](#isrunning)|Określa, czy kontrolka jest uruchomiona. Implementacja ATL zwraca wartość TRUE.|
|[IRunnableObjectImpl::LockRunning](#lockrunning)|Blokuje formant w stanie uruchomienia. Implementacja ATL zwraca S_OK.|
|[IRunnableObjectImpl:: Run](#run)|Wymusza uruchomienie formantu. Implementacja ATL zwraca S_OK.|
|[IRunnableObjectImpl::SetContainedObject](#setcontainedobject)|Wskazuje, że formant jest osadzony. Implementacja ATL zwraca S_OK.|

## <a name="remarks"></a>Uwagi

Interfejs [IRunnableObject](/windows/win32/api/objidl/nn-objidl-irunnableobject) umożliwia kontenerowi określenie, czy kontrolka jest uruchomiona, wymuszenie jej uruchomienia lub zablokowanie jej w stanie uruchomionym. Klasa `IRunnableObjectImpl` zapewnia domyślną implementację tego interfejsu i implementuje `IUnknown` przez wysyłanie informacji do urządzenia zrzutu w kompilacjach debugowania.

**Powiązane artykuły** [Samouczek ATL](../../atl/active-template-library-atl-tutorial.md), [Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IRunnableObject`

`IRunnableObjectImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlctl. h

##  <a name="getrunningclass"></a>IRunnableObjectImpl::GetRunningClass

Zwraca identyfikator CLSID uruchomionej kontrolki.

```
HRESULT GetRunningClass(LPCLSID lpClsid);
```

### <a name="return-value"></a>Wartość zwracana

Implementacja ATL ustawia \* *lpClsid* na GUID_NULL i zwraca E_UNEXPECTED.

### <a name="remarks"></a>Uwagi

Zobacz [IRunnableObject:: GetRunningClass](/windows/win32/api/objidl/nf-objidl-irunnableobject-getrunningclass) w Windows SDK.

##  <a name="isrunning"></a>IRunnableObjectImpl:: IsRunning

Określa, czy kontrolka jest uruchomiona.

```
virtual BOOL IsRunning();
```

### <a name="return-value"></a>Wartość zwracana

Implementacja ATL zwraca wartość TRUE.

### <a name="remarks"></a>Uwagi

Zobacz [IRunnableObject::](/windows/win32/api/objidl/nf-objidl-irunnableobject-isrunning) isdziałanie w Windows SDK.

##  <a name="lockrunning"></a>IRunnableObjectImpl::LockRunning

Blokuje formant w stanie uruchomienia.

```
HRESULT LockRunning(BOOL fLock, BOOL fLastUnlockCloses);
```

### <a name="return-value"></a>Wartość zwracana

Implementacja ATL zwraca S_OK.

### <a name="remarks"></a>Uwagi

Zobacz [IRunnableObject:: LockRunning](/windows/win32/api/objidl/nf-objidl-irunnableobject-lockrunning) w Windows SDK.

##  <a name="run"></a>IRunnableObjectImpl:: Run

Wymusza uruchomienie formantu.

```
HRESULT Run(LPBINDCTX lpbc);
```

### <a name="return-value"></a>Wartość zwracana

Implementacja ATL zwraca S_OK.

### <a name="remarks"></a>Uwagi

Zobacz [IRunnableObject:: Run](/windows/win32/api/objidl/nf-objidl-irunnableobject-run) w Windows SDK.

##  <a name="setcontainedobject"></a>IRunnableObjectImpl:: setzawierałobject

Wskazuje, że formant jest osadzony.

```
HRESULT SetContainedObject(BOOL fContained);
```

### <a name="return-value"></a>Wartość zwracana

Implementacja ATL zwraca S_OK.

### <a name="remarks"></a>Uwagi

Zobacz [IRunnableObject::](/windows/win32/api/objidl/nf-objidl-irunnableobject-setcontainedobject) setzawierałobject w Windows SDK.

## <a name="see-also"></a>Zobacz także

[Klasa CComControl](../../atl/reference/ccomcontrol-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
