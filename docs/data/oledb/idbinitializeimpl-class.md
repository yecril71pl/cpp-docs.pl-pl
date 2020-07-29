---
title: IDBInitializeImpl — Klasa
ms.date: 11/04/2016
f1_keywords:
- ATL.IDBInitializeImpl<T>
- ATL::IDBInitializeImpl<T>
- IDBInitializeImpl
- ATL::IDBInitializeImpl
- ATL.IDBInitializeImpl
- IDBInitializeImpl.IDBInitializeImpl
- IDBInitializeImpl::IDBInitializeImpl
- Initialize
- IDBInitializeImpl::Initialize
- IDBInitializeImpl.Initialize
- IDBInitializeImpl.Uninitialize
- Uninitialize
- IDBInitializeImpl::Uninitialize
- ATL::IDBInitializeImpl::m_dwStatus
- IDBInitializeImpl.m_dwStatus
- ATL.IDBInitializeImpl.m_dwStatus
- IDBInitializeImpl::m_dwStatus
- IDBInitializeImpl<T>::m_dwStatus
- ATL.IDBInitializeImpl<T>.m_dwStatus
- ATL::IDBInitializeImpl<T>::m_dwStatus
- m_dwStatus
- ATL::IDBInitializeImpl<T>::m_pCUtlPropInfo
- m_pCUtlPropInfo
- IDBInitializeImpl::m_pCUtlPropInfo
- ATL.IDBInitializeImpl.m_pCUtlPropInfo
- IDBInitializeImpl<T>::m_pCUtlPropInfo
- IDBInitializeImpl.m_pCUtlPropInfo
- ATL::IDBInitializeImpl::m_pCUtlPropInfo
helpviewer_keywords:
- IDBInitializeImpl class
- IDBInitializeImpl constructor
- Initialize method
- Uninitialize method
- m_dwStatus
- m_pCUtlPropInfo
ms.assetid: e4182f81-0443-44f5-a0d3-e7e075d6f883
ms.openlocfilehash: 511d67586a7adc2b26cc6acbdf39beff78f9c38a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218328"
---
# <a name="idbinitializeimpl-class"></a>IDBInitializeImpl — Klasa

Dostarcza implementację interfejsu [IDBInitialize](/previous-versions/windows/desktop/ms713706(v=vs.85)) .

## <a name="syntax"></a>Składnia

```cpp
template <class T>
class ATL_NO_VTABLE IDBInitializeImpl : public IDBInitialize
```

### <a name="parameters"></a>Parametry

*T*<br/>
Klasa, która pochodzi od `IDBInitializeImpl` .

## <a name="requirements"></a>Wymagania

**Nagłówek:** ATLDB. h

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[IDBInitializeImpl](#idbinitializeimpl)|Konstruktor.|

### <a name="interface-methods"></a>Metody interfejsu

|||
|-|-|
|[Initialize](#initialize)|Uruchamia dostawcę.|
|[Uninitialize](#uninitialize)|Powoduje zatrzymanie dostawcy.|

### <a name="data-members"></a>Elementy członkowskie danych

|||
|-|-|
|[m_dwStatus](#dwstatus)|Flagi źródła danych.|
|[m_pCUtlPropInfo](#pcutlpropinfo)|Wskaźnik do implementacji informacji o właściwościach bazy danych.|

## <a name="remarks"></a>Uwagi

Obowiązkowy interfejs dla obiektów źródła danych i opcjonalny interfejs w modułach wyliczających.

## <a name="idbinitializeimplidbinitializeimpl"></a><a name="idbinitializeimpl"></a>IDBInitializeImpl:: IDBInitializeImpl

Konstruktor.

### <a name="syntax"></a>Składnia

```cpp
IDBInitializeImpl();
```

### <a name="remarks"></a>Uwagi

Inicjuje wszystkie elementy członkowskie danych.

## <a name="idbinitializeimplinitialize"></a><a name="initialize"></a>IDBInitializeImpl:: Initialize

Inicjuje obiekt źródła danych przez przygotowanie jego obsługi właściwości.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD(Initialize)(void);
```

### <a name="remarks"></a>Uwagi

Zobacz [IDBInitialize:: Initialize](/previous-versions/windows/desktop/ms718026(v=vs.85)) w *dokumentacji programisty OLE DB*.

## <a name="idbinitializeimpluninitialize"></a><a name="uninitialize"></a>IDBInitializeImpl:: Uninitialize

Umieszcza obiekt źródła danych w stanie niezainicjowanym przez zwolnienie zasobów wewnętrznych, takich jak obsługa właściwości.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD(Uninitialize)(void);
```

### <a name="remarks"></a>Uwagi

Zobacz [IDBInitialize:: Uninitialize](/previous-versions/windows/desktop/ms719648(v=vs.85)) w *dokumentacji programisty OLE DB*.

## <a name="idbinitializeimplm_dwstatus"></a><a name="dwstatus"></a>IDBInitializeImpl:: m_dwStatus

Flagi źródła danych.

### <a name="syntax"></a>Składnia

```cpp
DWORD m_dwStatus;
```

### <a name="remarks"></a>Uwagi

Te flagi określają lub wskazują stan różnych atrybutów dla obiektu źródła danych. Zawiera co najmniej jedną z następujących **`enum`** wartości:

```cpp
enum DATASOURCE_FLAGS {
    DSF_MASK_INIT     = 0xFFFFF00F,
    DSF_PERSIST_DIRTY = 0x00000001,
    DSF_INITIALIZED   = 0x00000010,
};
```

|||
|-|-|
|`DSF_MASK_INIT`|Maska umożliwiająca przywrócenie niezainicjowanego stanu.|
|`DSF_PERSIST_DIRTY`|Ustaw, jeśli obiekt źródła danych wymaga trwałości (oznacza to, że zmiany zostały wprowadzone).|
|`DSF_INITIALIZED`|Ustaw, jeśli źródło danych zostało zainicjowane.|

## <a name="idbinitializeimplm_pcutlpropinfo"></a><a name="pcutlpropinfo"></a>IDBInitializeImpl:: m_pCUtlPropInfo

Wskaźnik do obiektu implementacji dla informacji o właściwościach bazy danych.

### <a name="syntax"></a>Składnia

```cpp
CUtlPropInfo< T >* m_pCUtlPropInfo;
```

## <a name="see-also"></a>Zobacz także

[Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
