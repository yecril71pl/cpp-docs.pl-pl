---
title: Klasa CComObjectNoLock | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComObjectNoLock
- ATLCOM/ATL::CComObjectNoLock
- ATLCOM/ATL::CComObjectNoLock::CComObjectNoLock
- ATLCOM/ATL::CComObjectNoLock::AddRef
- ATLCOM/ATL::CComObjectNoLock::QueryInterface
- ATLCOM/ATL::CComObjectNoLock::Release
dev_langs: C++
helpviewer_keywords: CComObjectNoLock class
ms.assetid: 288c6506-7da8-4127-8d58-7f4bd779539a
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4a85a238d17fe279359a73d3c740406c15b92c34
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ccomobjectnolock-class"></a>Klasa CComObjectNoLock
Ta klasa implementuje **IUnknown** dla obiekt nieagregowane, ale nie nie przyrostu liczbę blokad modułu w konstruktorze.  
  
## <a name="syntax"></a>Składnia  
  
```
template<class Base>  
class CComObjectNoLock : public Base
```  
  
#### <a name="parameters"></a>Parametry  
 `Base`  
 Pochodne klasy, [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) lub [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), jak również od innych interfejsu mają być obsługiwane w obiekcie.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComObjectNoLock::CComObjectNoLock](#ccomobjectnolock)|Konstruktor.|  
|[CComObjectNoLock:: ~ CComObjectNoLock](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComObjectNoLock::AddRef](#addref)|Zwiększa liczbę odwołanie do obiektu.|  
|[CComObjectNoLock::QueryInterface](#queryinterface)|Zwraca wskaźnik do żądanego interfejsu.|  
|[CComObjectNoLock::Release](#release)|Zmniejsza liczba odwołanie do obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 `CComObjectNoLock`przypomina [element CComObject](../../atl/reference/ccomobject-class.md) w tym implementuje [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) dla obiekt nieagregowane; jednak `CComObjectNoLock` jest liczba przyrostu blokady modułu w konstruktorze.  
  
 ATL używa `CComObjectNoLock` wewnętrznie dla fabryki klas. Ogólnie rzecz biorąc nie użyjesz tej klasy bezpośrednio.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `Base`  
  
 `CComObjectNoLock`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  
  
##  <a name="addref"></a>CComObjectNoLock::AddRef  
 Zwiększa liczbę odwołanie do obiektu.  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość, która może być przydatne w przypadku diagnostyki lub testowania.  
  
##  <a name="ccomobjectnolock"></a>CComObjectNoLock::CComObjectNoLock  
 Konstruktor. W odróżnieniu od [element CComObject](../../atl/reference/ccomobject-class.md), nie zwiększa liczbę blokad modułu.  
  
```
CComObjectNoLock(void* = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 **void\***  
 [in] Ten parametr nienazwany nie jest używany. Istnieje dla symetrycznego z innymi **CCom***XXX*`Object`*XXX* konstruktorów.  
  
##  <a name="dtor"></a>CComObjectNoLock:: ~ CComObjectNoLock  
 Destruktor.  
  
```
~CComObjectNoLock();
```  
  
### <a name="remarks"></a>Uwagi  
 Zwalnia wszystkie przydzielone zasoby i wywołania [FinalRelease](ccomobjectrootex-class.md#finalrelease).  

  
##  <a name="queryinterface"></a>CComObjectNoLock::QueryInterface  
 Pobiera wskaźnik do żądanego interfejsu.  
  
```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```  
  
### <a name="parameters"></a>Parametry  
 `iid`  
 [in] Identyfikator żądanego interfejsu.  
  
 `ppvObject`  
 [out] Wskaźnik do wskaźnika interfejsu identyfikowane przez `iid`. Jeśli obiekt nie obsługuje ten interfejs `ppvObject` ustawiono **NULL**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
##  <a name="release"></a>CComObjectNoLock::Release  
 Zmniejsza liczba odwołanie do obiektu.  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 W kompilacjach do debugowania **wersji** zwróci wartość, która może być przydatne w przypadku diagnostyki lub testowania. W kompilacjach do debugowania z systemem innym niż **wersji** zawsze zwraca wartość 0.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../../atl/atl-class-overview.md)
