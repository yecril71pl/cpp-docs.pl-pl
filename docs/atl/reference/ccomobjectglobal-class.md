---
title: Klasa CComObjectGlobal | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComObjectGlobal
- ATLCOM/ATL::CComObjectGlobal
- ATLCOM/ATL::CComObjectGlobal::CComObjectGlobal
- ATLCOM/ATL::CComObjectGlobal::AddRef
- ATLCOM/ATL::CComObjectGlobal::QueryInterface
- ATLCOM/ATL::CComObjectGlobal::Release
- ATLCOM/ATL::CComObjectGlobal::m_hResFinalConstruct
dev_langs:
- C++
helpviewer_keywords:
- CComObjectGlobal class
ms.assetid: 79bdee55-66e4-4536-b5b3-bdf09f78b9a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3614962d3bebada0c63b7fe804b52efaa965c6a9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32362446"
---
# <a name="ccomobjectglobal-class"></a>Klasa CComObjectGlobal
Ta klasa zarządza liczebności referencyjnej na moduł zawierający Twoje `Base` obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```
template<class Base>
class CComObjectGlobal : public Base
```  
  
#### <a name="parameters"></a>Parametry  
 `Base`  
 Pochodne klasy, [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) lub [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), jak również od innych interfejsu mają być obsługiwane w obiekcie.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComObjectGlobal::CComObjectGlobal](#ccomobjectglobal)|Konstruktor.|  
|[CComObjectGlobal:: ~ CComObjectGlobal](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComObjectGlobal::AddRef](#addref)|Implementuje globalnym `AddRef`.|  
|[CComObjectGlobal::QueryInterface](#queryinterface)|Implementuje globalnym `QueryInterface`.|  
|[CComObjectGlobal::Release](#release)|Implementuje globalnym **wersji**.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComObjectGlobal::m_hResFinalConstruct](#m_hresfinalconstruct)|Zawiera **HRESULT** zwrócony podczas tworzenia `CComObjectGlobal` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 `CComObjectGlobal` zarządza liczebności referencyjnej na moduł zawierający Twoje `Base` obiektu. `CComObjectGlobal` gwarantuje, że obiekt nie zostaną usunięte, tak długo, jak moduł nie jest zwalniany. Obiektu tylko zostaną usunięte, gdy liczba odwołań na cały moduł przechodzi od zera.  
  
 Na przykład za pomocą `CComObjectGlobal`, fabrykę klas mogą zawierać wspólnej obiekt globalny, który jest współużytkowany przez wszystkich klientów.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `Base`  
  
 `CComObjectGlobal`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  
  
##  <a name="addref"></a>  CComObjectGlobal::AddRef  
 Zwiększa liczbę odwołanie do obiektu o 1.  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość, która może być przydatne w przypadku diagnostyki i testowania.  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie `AddRef` wywołania **_Module::Lock**, gdzie **_Module** jest globalne wystąpienie [ccommodule —](../../atl/reference/ccommodule-class.md) lub klasą pochodną go.  
  
##  <a name="ccomobjectglobal"></a>  CComObjectGlobal::CComObjectGlobal  
 Konstruktor. Wywołania `FinalConstruct` , a następnie ustawia [m_hResFinalConstruct](#m_hresfinalconstruct) do `HRESULT` zwrócony przez `FinalConstruct`.  
  
```
CComObjectGlobal(void* = NULL));
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli nie ma pochodzi z klasy podstawowej [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md), należy podać własne `FinalConstruct` metody. Wywołania destruktora `FinalRelease`.  
  
##  <a name="dtor"></a>  CComObjectGlobal:: ~ CComObjectGlobal  
 Destruktor.  
  
```
CComObjectGlobal();
```  
  
### <a name="remarks"></a>Uwagi  
 Zwalnia wszystkie przydzielone zasoby i wywołania [FinalRelease](ccomobjectrootex-class.md#finalrelease).  
  
##  <a name="m_hresfinalconstruct"></a>  CComObjectGlobal::m_hResFinalConstruct  
 Zawiera `HRESULT` z wywołaniem `FinalConstruct` podczas budowy `CComObjectGlobal` obiektu.  
  
```
HRESULT m_hResFinalConstruct;
```  
  
##  <a name="queryinterface"></a>  CComObjectGlobal::QueryInterface  
 Pobiera wskaźnik na wskaźnik żądanego interfejsu.  
  
```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```  
  
### <a name="parameters"></a>Parametry  
 `iid`  
 [in] Identyfikator GUID żądanego interfejsu.  
  
 `ppvObject`  
 [out] Wskaźnik do wskaźnika interfejsu identyfikowany przez identyfikator iid, lub **NULL** Jeśli nie można odnaleźć interfejsu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 `QueryInterface` Obsługuje tylko interfejsy COM tabeli mapy.  
  
##  <a name="release"></a>  CComObjectGlobal::Release  
 Zmniejsza odwołanie liczba obiektu o 1.  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 W kompilacjach do debugowania **wersji** zwróci wartość, która może być przydatne w przypadku diagnostyki i testowania. W kompilacjach do debugowania z systemem innym niż **wersji** zawsze zwraca wartość 0.  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie **wersji** wywołania **_Module::Unlock**, gdzie **_Module** jest globalne wystąpienie [ccommodule —](../../atl/reference/ccommodule-class.md) lub klasą pochodną go.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CComObjectStack](../../atl/reference/ccomobjectstack-class.md)   
 [Klasa CComAggObject](../../atl/reference/ccomaggobject-class.md)   
 [Element CComObject — klasa](../../atl/reference/ccomobject-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
