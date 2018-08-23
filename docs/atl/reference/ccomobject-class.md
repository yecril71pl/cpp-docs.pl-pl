---
title: Klasa CComObject | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComObject
- ATLCOM/ATL::CComObject
- ATLCOM/ATL::CComObject::CComObject
- ATLCOM/ATL::CComObject::AddRef
- ATLCOM/ATL::CComObject::CreateInstance
- ATLCOM/ATL::CComObject::QueryInterface
- ATLCOM/ATL::CComObject::Release
dev_langs:
- C++
helpviewer_keywords:
- CComObject class
ms.assetid: e2b6433b-6349-4749-b4bc-acbd7a22c8b0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4be126af9228312fa5fd4430e4f477f037d31df8
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2018
ms.locfileid: "42466236"
---
# <a name="ccomobject-class"></a>Klasa CComObject
Ta klasa implementuje `IUnknown` nieagregowane obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```
template<class Base>  
class CComObject : public Base
```  
  
#### <a name="parameters"></a>Parametry  
 *podstawowy*  
 Z klasą pochodną [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) lub [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), jak również od innych interfejsów, które chcesz obsługiwać obiektu.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComObject::CComObject](#ccomobject)|Konstruktor.|  
|[CComObject::~CComObject](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComObject::AddRef](#addref)|Zwiększa liczbę odwołań do obiektu.|  
|[CComObject::CreateInstance](#createinstance)|(Statyczny) Tworzy nową `CComObject` obiektu.|  
|[CComObject::QueryInterface](#queryinterface)|Pobiera wskaźnik do żądanego interfejsu.|  
|[CComObject::Release](#release)|Dekrementuje liczbę odwołań do obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 `CComObject` implementuje [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) nieagregowane obiektu. Jednak wywołania `QueryInterface`, `AddRef`, i `Release` są delegowane `CComObjectRootEx`.  
  
 Aby uzyskać więcej informacji o korzystaniu z `CComObject`, zapoznaj się z artykułem [podstawy ATL obiektów COM](../../atl/fundamentals-of-atl-com-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `Base`  
  
 `CComObject`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  
  
##  <a name="addref"></a>  CComObject::AddRef  
 Zwiększa liczbę odwołań do obiektu.  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Ta funkcja zwraca nowy licznik odwołań zwiększona w obiekcie. Ta wartość może być przydatne w przypadku diagnostyki lub testowania aplikacji.  
  
##  <a name="ccomobject"></a>  CComObject::CComObject  
 Konstruktor zwiększa liczbę blokad modułu.  
  
```
CComObject(void* = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 **Void\***  
 [in] Ten parametr nienazwany nie jest używany. Istnieje symetrii z innymi **CCom *** XXX*`Object`*XXX* konstruktorów.  
  
### <a name="remarks"></a>Uwagi  
 Dekrementuje destruktor go.  
  
 Jeśli `CComObject`— obiekt pochodnej pomyślnie jest tworzony przy użyciu **nowe** operatora, licznik odwołań początkowy to 0. Aby ustawić liczbę odwołań do prawidłowego wartość (1), wywoływania [AddRef](#addref) funkcji.  
  
##  <a name="dtor"></a>  CComObject::~CComObject  
 Destruktor.  
  
```
CComObject();
```  
  
### <a name="remarks"></a>Uwagi  
 Zwalnia wszystkie przydzielone zasoby, wywołania [FinalRelease](ccomobjectrootex-class.md#finalrelease), oraz liczbę blokad modułu zmniejsza.  

  
##  <a name="createinstance"></a>  CComObject::CreateInstance  
 Ta funkcja statyczna służy do tworzenia nowego **CComObject <** `Base` **>** obiektu, bez konieczności [CoCreateInstance](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance).  
  
```
static HRESULT WINAPI CreateInstance(CComObject<Base>** pp);
```  
  
### <a name="parameters"></a>Parametry  
 *strony*  
 [out] Wskaźnik do **CComObject <** `Base` **>** wskaźnika. Jeśli `CreateInstance` zakończy się niepowodzeniem, *pp* ma wartość NULL.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowe wartości HRESULT.  
  
### <a name="remarks"></a>Uwagi  
 Zwrócony obiekt ma liczebności referencyjnej równej zero, więc wywołanie `AddRef` natychmiast, następnie użyć `Release` zwolnienie odwołania na wskaźnik do obiektu, gdy wszystko będzie gotowe.  
  
 Jeśli nie potrzebujesz bezpośredni dostęp do obiektu, ale mimo to chcesz utworzyć nowy obiekt bez konieczności `CoCreateInstance`, użyj [CComCoClass::CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance) zamiast tego.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_COM#38](../../atl/codesnippet/cpp/ccomobject-class_1.h)]  
  
 [!code-cpp[NVC_ATL_COM#39](../../atl/codesnippet/cpp/ccomobject-class_2.cpp)]  
  
##  <a name="queryinterface"></a>  CComObject::QueryInterface  
 Pobiera wskaźnik do żądanego interfejsu.  
  
```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>  
HRESULT STDMETHODCALLTYPE QueryInterface(Q** pp);
```  
  
### <a name="parameters"></a>Parametry  
 *IID*  
 [in] Identyfikator interfejsu żądanej.  
  
 *ppvObject*  
 [out] Wskaźnik do wskaźnika interfejsu identyfikowane przez *iid*. Jeśli obiekt nie obsługuje ten interfejs *ppvObject* ma wartość NULL.  
  
 *strony*  
 [out] Wskaźnik do wskaźnika interfejsu identyfikowanych według typu `Q`. Jeśli obiekt nie obsługuje ten interfejs *pp* ma wartość NULL.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowe wartości HRESULT.  
  
##  <a name="release"></a>  CComObject::Release  
 Dekrementuje liczbę odwołań do obiektu.  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Ta funkcja zwraca nowy licznik odwołań wraz z przydzielaniem obiektu. W kompilacjach debugowania zwracana wartość może być użyteczna, diagnostykę lub testowania. W kompilacjach nieprzeznaczonych do debugowania `Release` zawsze zwraca wartość 0.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CComAggObject](../../atl/reference/ccomaggobject-class.md)   
 [Klasa CComPolyObject](../../atl/reference/ccompolyobject-class.md)   
 [DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable)   
 [DECLARE_NOT_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_not_aggregatable)   
 [Klasa — Przegląd](../../atl/atl-class-overview.md)
