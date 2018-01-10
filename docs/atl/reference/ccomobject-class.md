---
title: Element CComObject klasy | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComObject
- ATLCOM/ATL::CComObject
- ATLCOM/ATL::CComObject::CComObject
- ATLCOM/ATL::CComObject::AddRef
- ATLCOM/ATL::CComObject::CreateInstance
- ATLCOM/ATL::CComObject::QueryInterface
- ATLCOM/ATL::CComObject::Release
dev_langs: C++
helpviewer_keywords: CComObject class
ms.assetid: e2b6433b-6349-4749-b4bc-acbd7a22c8b0
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 27da00e09ca88cc06b8bafed8f8601dac756fd34
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ccomobject-class"></a>Element CComObject — klasa
Ta klasa implementuje **IUnknown** dla obiekt nieagregowane.  
  
## <a name="syntax"></a>Składnia  
  
```
template<class Base>  
class CComObject : public Base
```  
  
#### <a name="parameters"></a>Parametry  
 `Base`  
 Pochodne klasy, [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) lub [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), jak również od innych interfejsów mają być obsługiwane w obiekcie.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComObject::CComObject](#ccomobject)|Konstruktor.|  
|[Element CComObject:: ~ element CComObject](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComObject::AddRef](#addref)|Zwiększa liczbę odwołanie do obiektu.|  
|[CComObject::CreateInstance](#createinstance)|(Statyczny) Tworzy nową `CComObject` obiektu.|  
|[CComObject::QueryInterface](#queryinterface)|Pobiera wskaźnik do żądanego interfejsu.|  
|[CComObject::Release](#release)|Zmniejsza liczba odwołanie do obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 `CComObject`implementuje [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) dla obiekt nieagregowane. Jednak wywołań `QueryInterface`, `AddRef`, i **wersji** mają delegowane do `CComObjectRootEx`.  
  
 Aby uzyskać więcej informacji o korzystaniu z `CComObject`, zapoznaj się z artykułem [podstawy ATL obiektów COM](../../atl/fundamentals-of-atl-com-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `Base`  
  
 `CComObject`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  
  
##  <a name="addref"></a>CComObject::AddRef  
 Zwiększa liczbę odwołanie do obiektu.  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Ta funkcja zwraca nowy licznik zwiększany odwołanie do obiektu. Ta wartość może być przydatne w przypadku diagnostyki lub testowania.  
  
##  <a name="ccomobject"></a>CComObject::CComObject  
 Konstruktor zwiększa liczbę blokad modułu.  
  
```
CComObject(void* = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 **void\***  
 [in] Ten parametr nienazwany nie jest używany. Istnieje dla symetrycznego z innymi **CCom***XXX*`Object`*XXX* konstruktorów.  
  
### <a name="remarks"></a>Uwagi  
 Zmniejsza destruktora go.  
  
 Jeśli `CComObject`-obiektu pochodnego pomyślnie jest tworzony przy użyciu **nowe** operatora, liczba początkowa odwołania to 0. Aby ustawić liczbę odwołań do poprawnej wartości (1), wywoływania [AddRef](#addref) funkcji.  
  
##  <a name="dtor"></a>Element CComObject:: ~ element CComObject  
 Destruktor.  
  
```
CComObject();
```  
  
### <a name="remarks"></a>Uwagi  
 Zwalnia wszystkie przydzielone zasoby, wywołania [FinalRelease](ccomobjectrootex-class.md#finalrelease), i zmniejsza liczbę blokad modułu.  

  
##  <a name="createinstance"></a>CComObject::CreateInstance  
 Ta funkcja statyczna służy do tworzenia nowego **element CComObject <** `Base`  **>**  obiektu bez ponoszenia dodatkowych nakładów [wywołanie funkcji CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615).  
  
```
static HRESULT WINAPI CreateInstance(CComObject<Base>** pp);
```  
  
### <a name="parameters"></a>Parametry  
 `pp`  
 [out] Wskaźnik do **element CComObject <** `Base`  **>**  wskaźnika. Jeśli `CreateInstance` zakończy się niepowodzeniem, `pp` ustawiono **NULL**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Obiekt zwrócony ma liczebności referencyjnej równej zero, dlatego wywołania `AddRef` natychmiast, następnie użyć **wersji** zwolnienia odwołania na wskaźnik do obiektu, gdy wszystko będzie gotowe.  
  
 Jeśli nie wymagają bezpośredni dostęp do obiektu, ale mimo to chcesz utworzyć nowy obiekt bez ponoszenia dodatkowych nakładów `CoCreateInstance`, użyj [CComCoClass::CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance) zamiast tego.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_COM#38](../../atl/codesnippet/cpp/ccomobject-class_1.h)]  
  
 [!code-cpp[NVC_ATL_COM#39](../../atl/codesnippet/cpp/ccomobject-class_2.cpp)]  
  
##  <a name="queryinterface"></a>CComObject::QueryInterface  
 Pobiera wskaźnik do żądanego interfejsu.  
  
```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>  
HRESULT STDMETHODCALLTYPE QueryInterface(Q** pp);
```  
  
### <a name="parameters"></a>Parametry  
 `iid`  
 [in] Identyfikator żądanego interfejsu.  
  
 `ppvObject`  
 [out] Wskaźnik do wskaźnika interfejsu identyfikowane przez `iid`. Jeśli obiekt nie obsługuje ten interfejs `ppvObject` ustawiono **NULL**.  
  
 `pp`  
 [out] Wskaźnik do wskaźnika interfejsu identyfikowanych według typu `Q`. Jeśli obiekt nie obsługuje ten interfejs `pp` ustawiono **NULL**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
##  <a name="release"></a>CComObject::Release  
 Zmniejsza liczba odwołanie do obiektu.  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Ta funkcja zwraca liczby nowych zmniejszany odwołanie do obiektu. W kompilacjach debugowania zwracana wartość może być przydatne w przypadku diagnostyki lub testowania. W kompilacjach do debugowania z systemem innym niż **wersji** zawsze zwraca wartość 0.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CComAggObject](../../atl/reference/ccomaggobject-class.md)   
 [Klasa CComPolyObject](../../atl/reference/ccompolyobject-class.md)   
 [DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable)   
 [DECLARE_NOT_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_not_aggregatable)   
 [Przegląd klas](../../atl/atl-class-overview.md)
