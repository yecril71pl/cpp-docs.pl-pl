---
title: Idbinitializeimpl — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.IDBInitializeImpl<T>
- ATL::IDBInitializeImpl<T>
- IDBInitializeImpl
- ATL::IDBInitializeImpl
- ATL.IDBInitializeImpl
- IDBInitializeImpl.IDBInitializeImpl
- IDBInitializeImpl
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
dev_langs:
- C++
helpviewer_keywords:
- IDBInitializeImpl class
- IDBInitializeImpl constructor
- Initialize method
- Uninitialize method
- m_dwStatus
- m_pCUtlPropInfo
ms.assetid: e4182f81-0443-44f5-a0d3-e7e075d6f883
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f59619db743d8f8d08b2a202e992cdfcd532e1e8
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2018
ms.locfileid: "42464565"
---
# <a name="idbinitializeimpl-class"></a>IDBInitializeImpl — Klasa
Udostępnia implementację na potrzeby [IDBInitialize](/previous-versions/windows/desktop/ms713706\(v=vs.85\)) interfejsu.  
  
## <a name="syntax"></a>Składnia

```cpp
template <class T>  
class ATL_NO_VTABLE IDBInitializeImpl : public IDBInitialize  
```  
  
### <a name="parameters"></a>Parametry  
 *T*  
 Z klasą pochodną `IDBInitializeImpl`.  

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[IDBInitializeImpl](#idbinitializeimpl)|Konstruktor.|  
  
### <a name="interface-methods"></a>Metody interfejsu  
  
|||  
|-|-|  
|[Initialize](#initialize)|Uruchamia dostawcę.|  
|[Odinicjalizuj](#uninitialize)|Zatrzymuje dostawcy.|  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|||  
|-|-|  
|[m_dwStatus](#dwstatus)|Flagi źródła danych.|  
|[m_pCUtlPropInfo](#pcutlpropinfo)|Wskaźnik do implementacji właściwości bazy danych.|  
  
## <a name="remarks"></a>Uwagi  
 Obowiązkowego interfejsu na obiekty źródła danych i opcjonalnie interfejsu na modułach wyliczających.  

## <a name="idbinitializeimpl"></a> IDBInitializeImpl::IDBInitializeImpl
Konstruktor.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
IDBInitializeImpl();  
```  
  
### <a name="remarks"></a>Uwagi  
 Inicjuje wszystkie elementy członkowskie danych. 
  
## <a name="initialize"></a> IDBInitializeImpl::Initialize
Inicjuje obiekt źródła danych, przygotowywania jego obsługa właściwości.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
STDMETHOD(Initialize)(void);  
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IDBInitialize::Initialize](/previous-versions/windows/desktop/ms718026\(v=vs.85\)) w *OLE DB Podręcznik programisty*. 

## <a name="uninitialize"></a> IDBInitializeImpl::Uninitialize
Umieszcza dane źródła obiektu w stanie niezainicjowanym przy zwalnianiu zasobów wewnętrznych, takich jak obsługa właściwości.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
STDMETHOD(Uninitialize)(void);  
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IDBInitialize::Uninitialize](/previous-versions/windows/desktop/ms719648\(v=vs.85\)) w *OLE DB Podręcznik programisty*.

## <a name="dwstatus"></a> IDBInitializeImpl::m_dwStatus
Flagi źródła danych.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
DWORD m_dwStatus;  
```  
  
### <a name="remarks"></a>Uwagi  
 Te flagi określić lub wskazuje stan różnych atrybutów dla obiektu źródła danych. Zawiera co najmniej jeden z następujących **wyliczenia** wartości:  
  
```cpp  
enum DATASOURCE_FLAGS {  
    DSF_MASK_INIT     = 0xFFFFF00F,  
    DSF_PERSIST_DIRTY = 0x00000001,  
    DSF_INITIALIZED   = 0x00000010,  
};  
```  
  
|||  
|-|-|  
|`DSF_MASK_INIT`|Maskę, aby włączyć Przywracanie niezainicjowanego stanu.|  
|`DSF_PERSIST_DIRTY`|Ustaw, jeśli obiekt źródła danych wymaga trwałości (to znaczy, jeśli wprowadzono zmiany).|  
|`DSF_INITIALIZED`|Ustaw, jeśli źródło danych zostało zainicjowane.|  

## <a name="pcutlpropinfo"></a> IDBInitializeImpl::m_pCUtlPropInfo
Wskaźnik do obiektu implementacji, aby uzyskać informacje o właściwościach bazy danych.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
CUtlPropInfo< T >* m_pCUtlPropInfo;  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)