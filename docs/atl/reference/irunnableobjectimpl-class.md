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
ms.openlocfilehash: 2843c0c25a5c104ffbdff72255ac5d85cf53b1ee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329443"
---
# <a name="irunnableobjectimpl-class"></a>Klasa IRunnableObjectImpl

Ta klasa `IUnknown` implementuje i zapewnia domyślną implementację interfejsu [IRunnableObject.](/windows/win32/api/objidl/nn-objidl-irunnableobject)

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
template<class T>
class IRunnableObjectImpl
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Twoja klasa, pochodząca od `IRunnableObjectImpl`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IRunnableObjectImpl::GetRunningClass](#getrunningclass)|Zwraca CLSID uruchomionego formantu. Implementacja ATL ustawia CLSID do GUID_NULL i zwraca E_UNEXPECTED.|
|[IRunnableObjectImpl::IsRunning](#isrunning)|Określa, czy formant jest uruchomiony. Implementacja ATL zwraca wartość TRUE.|
|[IRunnableObjectImpl::LockRunning](#lockrunning)|Blokuje formant w stanie uruchomionym. Implementacja ATL zwraca S_OK.|
|[IRunnableObjectImpl::Uruchom](#run)|Wymusza uruchomienie formantu. Implementacja ATL zwraca S_OK.|
|[IRunnableObjectImpl::SetContainedObject](#setcontainedobject)|Wskazuje, że formant jest osadzony. Implementacja ATL zwraca S_OK.|

## <a name="remarks"></a>Uwagi

Interfejs [IRunnableObject](/windows/win32/api/objidl/nn-objidl-irunnableobject) umożliwia kontenerowi określenie, czy formant jest uruchomiony, wymusić jego uruchomienie lub zablokować go w stanie uruchomionym. Klasa `IRunnableObjectImpl` zapewnia domyślną implementację tego `IUnknown` interfejsu i implementuje przez wysyłanie informacji do urządzenia zrzutu w kompilacjach debugowania.

**Podobne artykuły** [ATL Tutorial](../../atl/active-template-library-atl-tutorial.md), Tworzenie projektu [ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IRunnableObject`

`IRunnableObjectImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlctl.h

## <a name="irunnableobjectimplgetrunningclass"></a><a name="getrunningclass"></a>IRunnableObjectImpl::GetRunningClass

Zwraca CLSID uruchomionego formantu.

```
HRESULT GetRunningClass(LPCLSID lpClsid);
```

### <a name="return-value"></a>Wartość zwracana

Implementacja ATL \* ustawia *lpClsid* do GUID_NULL i zwraca E_UNEXPECTED.

### <a name="remarks"></a>Uwagi

Zobacz [IRunnableObject::GetRunningClass](/windows/win32/api/objidl/nf-objidl-irunnableobject-getrunningclass) w windows SDK.

## <a name="irunnableobjectimplisrunning"></a><a name="isrunning"></a>IRunnableObjectImpl::IsRunning

Określa, czy formant jest uruchomiony.

```
virtual BOOL IsRunning();
```

### <a name="return-value"></a>Wartość zwracana

Implementacja ATL zwraca wartość TRUE.

### <a name="remarks"></a>Uwagi

Zobacz [IRunnableObject::IsRunning](/windows/win32/api/objidl/nf-objidl-irunnableobject-isrunning) w windows SDK.

## <a name="irunnableobjectimpllockrunning"></a><a name="lockrunning"></a>IRunnableObjectImpl::LockRunning

Blokuje formant w stanie uruchomionym.

```
HRESULT LockRunning(BOOL fLock, BOOL fLastUnlockCloses);
```

### <a name="return-value"></a>Wartość zwracana

Implementacja ATL zwraca S_OK.

### <a name="remarks"></a>Uwagi

Zobacz [IRunnableObject::LockRunning](/windows/win32/api/objidl/nf-objidl-irunnableobject-lockrunning) w windows SDK.

## <a name="irunnableobjectimplrun"></a><a name="run"></a>IRunnableObjectImpl::Uruchom

Wymusza uruchomienie formantu.

```
HRESULT Run(LPBINDCTX lpbc);
```

### <a name="return-value"></a>Wartość zwracana

Implementacja ATL zwraca S_OK.

### <a name="remarks"></a>Uwagi

Zobacz [IRunnableObject::Uruchom](/windows/win32/api/objidl/nf-objidl-irunnableobject-run) w windows SDK.

## <a name="irunnableobjectimplsetcontainedobject"></a><a name="setcontainedobject"></a>IRunnableObjectImpl::SetContainedObject

Wskazuje, że formant jest osadzony.

```
HRESULT SetContainedObject(BOOL fContained);
```

### <a name="return-value"></a>Wartość zwracana

Implementacja ATL zwraca S_OK.

### <a name="remarks"></a>Uwagi

Zobacz [IRunnableObject::SetContainedObject](/windows/win32/api/objidl/nf-objidl-irunnableobject-setcontainedobject) w zestawie Windows SDK.

## <a name="see-also"></a>Zobacz też

[Klasa CComControl](../../atl/reference/ccomcontrol-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
