---
title: Klasa CComCachedTearOffObject | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComCachedTearOffObject
- ATLCOM/ATL::CComCachedTearOffObject
- ATLCOM/ATL::CComCachedTearOffObject::CComCachedTearOffObject
- ATLCOM/ATL::CComCachedTearOffObject::AddRef
- ATLCOM/ATL::CComCachedTearOffObject::FinalConstruct
- ATLCOM/ATL::CComCachedTearOffObject::FinalRelease
- ATLCOM/ATL::CComCachedTearOffObject::QueryInterface
- ATLCOM/ATL::CComCachedTearOffObject::Release
- ATLCOM/ATL::CComCachedTearOffObject::m_contained
dev_langs:
- C++
helpviewer_keywords:
- cache, ATL cached tear-off objects
- CComCachedTearOffObject class
ms.assetid: ae19507d-a1de-4dbc-a988-da9f75a50c95
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d1072faed01033bec9fec127318334f8a61ac29e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32362885"
---
# <a name="ccomcachedtearoffobject-class"></a>Klasa CComCachedTearOffObject
Ta klasa implementuje [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) oderwania interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```
template
 <class contained>
class CComCachedTearOffObject : public
    IUnknown,
public CComObjectRootEx<contained
 ::_ThreadModel::ThreadModelNoCS>
```  
  
#### <a name="parameters"></a>Parametry  
 `contained`  
 Pochodne klasy oderwania, `CComTearOffObjectBase` i interfejsy ma obiekt oderwania do obsługi.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComCachedTearOffObject::CComCachedTearOffObject](#ccomcachedtearoffobject)|Konstruktor.|  
|[CComCachedTearOffObject:: ~ CComCachedTearOffObject](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComCachedTearOffObject::AddRef](#addref)|Zwiększa liczbę odwołania dla `CComCachedTearOffObject` obiektu.|  
|[CComCachedTearOffObject::FinalConstruct](#finalconstruct)|Wywołania `m_contained::FinalConstruct` (metoda oderwania klasy).|  
|[CComCachedTearOffObject::FinalRelease](#finalrelease)|Wywołania `m_contained::FinalRelease` (metoda oderwania klasy).|  
|[CComCachedTearOffObject::QueryInterface](#queryinterface)|Zwraca wskaźnik do `IUnknown` z `CComCachedTearOffObject` obiekt, lub do żądanego interfejsu w klasie oderwania (klasa `contained`).|  
|[CComCachedTearOffObject::Release](#release)|Zmniejsza liczba odwołanie o `CComCachedTearOffObject` obiektu i niszczy go, jeśli liczba odwołań wynosi 0.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComCachedTearOffObject::m_contained](#m_contained)|A `CComContainedObject` obiektu pochodzi od klasy oderwania (klasa `contained`).|  
  
## <a name="remarks"></a>Uwagi  
 `CComCachedTearOffObject` implementuje [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) oderwania interfejsu. Ta klasa różni się od `CComTearOffObject` w tym `CComCachedTearOffObject` ma własną **IUnknown**, niezależnie od właściciela obiektu **IUnknown** (właścicielem jest obiekt, dla którego oderwania jest tworzony). `CComCachedTearOffObject` zachowuje własną odwołania liczba na jego **IUnknown** i usuwana po jego liczba odwołań wynosi zero. Jednak po wykonaniu zapytania dla każdego z jego oderwania interfejsy, liczba odwołań obiektu właściciela **IUnknown** jest zwiększany.  
  
 Jeśli `CComCachedTearOffObject` implementacja oderwania jest już utworzone i interfejs oderwania zostanie zapytany o ponownie, same obiektów `CComCachedTearOffObject` obiekt zostanie ponownie użyty. Natomiast jeśli oderwania interfejs implementowany przez `CComTearOffObject` ponownie zostanie zapytany o za pośrednictwem obiektu właściciela innego `CComTearOffObject` będzie można utworzyć wystąpienia.  
  
 Klasa właściciel musi implementować `FinalRelease` i wywołanie **wersji** w pamięci podręcznej **IUnknown** dla `CComCachedTearOffObject`, który będzie zmniejszyć jego liczba odwołań. Spowoduje to `CComCachedTearOffObject`w `FinalRelease` można wywołać i usuwania oderwania.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `CComObjectRootBase`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IUnknown`  
  
 `CComCachedTearOffObject`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  
  
##  <a name="addref"></a>  CComCachedTearOffObject::AddRef  
 Zwiększa liczbę odwołanie z `CComCachedTearOffObject` obiektu o 1.  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość, która może być przydatne w przypadku diagnostyki i testowania.  
  
##  <a name="ccomcachedtearoffobject"></a>  CComCachedTearOffObject::CComCachedTearOffObject  
 Konstruktor.  
  
```
CComCachedTearOffObject(void* pv);
```  
  
### <a name="parameters"></a>Parametry  
 `pv`  
 [in] Wskaźnik do **IUnknown** z `CComCachedTearOffObject`.  
  
### <a name="remarks"></a>Uwagi  
 Inicjuje `CComContainedObject` — członek, [m_contained](#m_contained).  
  
##  <a name="dtor"></a>  CComCachedTearOffObject:: ~ CComCachedTearOffObject  
 Destruktor.  
  
```
~CComCachedTearOffObject();
```  
  
### <a name="remarks"></a>Uwagi  
 Zwalnia wszystkie przydzielone zasoby i wywołania [FinalRelease](#finalrelease).  
  
##  <a name="finalconstruct"></a>  CComCachedTearOffObject::FinalConstruct  
 Wywołania **m_contained::FinalConstruct** utworzyć `m_contained`, `CComContainedObject` <  `contained`> umożliwiają dostęp do interfejsu zaimplementowany przez klasę oderwania obiektu.  
  
```
HRESULT FinalConstruct();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
##  <a name="finalrelease"></a>  CComCachedTearOffObject::FinalRelease  
 Wywołania **m_contained::FinalRelease** zwolnienia `m_contained`, `CComContainedObject` <  `contained`> obiektu.  
  
```
void FinalRelease();
```  
  
##  <a name="m_contained"></a>  CComCachedTearOffObject::m_contained  
 A [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) obiektu pochodzi od klasy oderwania.  
  
```
CcomContainedObject <contained> m_contained;
```     
  
### <a name="parameters"></a>Parametry  
 `contained`  
 [in] Pochodne klasy oderwania, `CComTearOffObjectBase` i interfejsy ma obiekt oderwania do obsługi.  
  
### <a name="remarks"></a>Uwagi  
 Metody `m_contained` dziedziczy umożliwiają dostęp do interfejsu oderwania w klasie oderwania za pośrednictwem pamięci podręcznej oderwania obiektu `QueryInterface`, `FinalConstruct`, i `FinalRelease`.  
  
##  <a name="queryinterface"></a>  CComCachedTearOffObject::QueryInterface  
 Pobiera wskaźnik do żądanego interfejsu.  
  
```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```  
  
### <a name="parameters"></a>Parametry  
 `iid`  
 [in] Identyfikator GUID żądanego interfejsu.  
  
 `ppvObject`  
 [out] Wskaźnik do wskaźnika interfejsu identyfikowane przez `iid`, lub **NULL** Jeśli nie można odnaleźć interfejsu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli jest żądany interfejs **IUnknown**, zwraca wskaźnik do `CComCachedTearOffObject`na własnych **IUnknown** i zwiększa liczbę odwołań. W przeciwnym razie zapytania dla interfejsu na przy użyciu klasy oderwania [InternalQueryInterface](ccomobjectrootex-class.md#internalqueryinterface) odziedziczone metody `CComObjectRootEx`.  

  
##  <a name="release"></a>  CComCachedTearOffObject::Release  
 Zmniejsza odwołanie liczba 1 i, jeśli liczba odwołań wynosi 0, usuwa `CComCachedTearOffObject` obiektu.  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 W kompilacjach do debugowania nie zawsze zwraca wartość 0. W kompilacjach debugowania zwraca wartość, która może być przydatne w przypadku diagnostyki lub testowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CComTearOffObject](../../atl/reference/ccomtearoffobject-class.md)   
 [Klasa CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
