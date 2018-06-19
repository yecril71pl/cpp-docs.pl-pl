---
title: Klasa CComAggObject | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComAggObject
- ATLCOM/ATL::CComAggObject
- ATLCOM/ATL::CComAggObject::CComAggObject
- ATLCOM/ATL::CComAggObject::AddRef
- ATLCOM/ATL::CComAggObject::CreateInstance
- ATLCOM/ATL::CComAggObject::FinalConstruct
- ATLCOM/ATL::CComAggObject::FinalRelease
- ATLCOM/ATL::CComAggObject::QueryInterface
- ATLCOM/ATL::CComAggObject::Release
- ATLCOM/ATL::CComAggObject::m_contained
dev_langs:
- C++
helpviewer_keywords:
- aggregate objects [C++], in ATL
- aggregation [C++], ATL objects
- CComAggObject class
ms.assetid: 7aa90d69-d399-477b-880d-e2cdf0ef7881
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 426a01c1957b276174b8b36884605b69dd501de8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32364222"
---
# <a name="ccomaggobject-class"></a>Klasa CComAggObject
Ta klasa implementuje [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) interfejs dla obiekt zagregowanych. Zgodnie z definicją zagregowane obiekt znajduje się w obiekcie zewnętrznym. `CComAggObject` Klasy jest podobna do [element CComObject klasy](../../atl/reference/ccomobject-class.md), ale jego udostępnia interfejs, który jest bezpośrednio dostępny dla klientów zewnętrznych.  
  
## <a name="syntax"></a>Składnia  
  
```
template<class contained>  
class CComAggObject : public IUnknown, 
   public CComObjectRootEx<contained::_ThreadModel::ThreadModelNoCS>
```  
  
#### <a name="parameters"></a>Parametry  
 `contained`  
 Pochodne klasy, [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) lub [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), jak również od innych interfejsów mają być obsługiwane w obiekcie.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComAggObject::CComAggObject](#ccomaggobject)|Konstruktor.|  
|[CComAggObject:: ~ CComAggObject](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComAggObject::AddRef](#addref)|Zwiększa liczbę odwołanie zagregowane obiektu.|  
|[CComAggObject::CreateInstance](#createinstance)|Ta funkcja statyczna służy do tworzenia nowego **CComAggObject <** `contained` **>** obiektu bez ponoszenia dodatkowych nakładów [wywołanie funkcji CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615).|  
|[CComAggObject::FinalConstruct](#finalconstruct)|Wykonuje końcowego inicjowania elementu `m_contained`.|  
|[CComAggObject::FinalRelease](#finalrelease)|Wykonuje końcowego zniszczenie `m_contained`.|  
|[CComAggObject::QueryInterface](#queryinterface)|Pobiera wskaźnik do żądanego interfejsu.|  
|[CComAggObject::Release](#release)|Zmniejsza odwołanie liczba zagregowane obiektu.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComAggObject::m_contained](#m_contained)|Obiekty delegowane `IUnknown` wywołań zewnętrznego nieznany.|  
  
## <a name="remarks"></a>Uwagi  
 `CComAggObject` implementuje [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) dla obiekt zagregowanych. `CComAggObject` ma własną **IUnknown** interfejs, niezależnie od obiektu zewnętrznego **IUnknown** interfejs, a także obsługuje licznika odwołania.  
  
 Aby uzyskać więcej informacji na temat agregacji, zobacz artykuł [podstawy ATL obiektów COM](../../atl/fundamentals-of-atl-com-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `CComObjectRootBase`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IUnknown`  
  
 `CComAggObject`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  
  
##  <a name="addref"></a>  CComAggObject::AddRef  
 Zwiększa liczbę odwołanie zagregowane obiektu.  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość, która może być przydatne w przypadku diagnostyki lub testowania.  
  
##  <a name="ccomaggobject"></a>  CComAggObject::CComAggObject  
 Konstruktor.  
  
```
CComAggObject(void* pv);
```  
  
### <a name="parameters"></a>Parametry  
 `pv`  
 [in] Nieznany zewnętrzne.  
  
### <a name="remarks"></a>Uwagi  
 Inicjuje `CComContainedObject` — członek, [m_contained](#m_contained)i zwiększa liczbę blokad modułu.  
  
 Destruktor zmniejsza liczbę blokad modułu.  
  
##  <a name="dtor"></a>  CComAggObject:: ~ CComAggObject  
 Destruktor.  
  
```
~CComAggObject();
```  
  
### <a name="remarks"></a>Uwagi  
 Zwalnia wszystkie przydzielone zasoby, wywołania [FinalRelease](#finalrelease), i zmniejsza liczbę blokad modułu.  
  
##  <a name="createinstance"></a>  CComAggObject::CreateInstance  
 Ta funkcja statyczna służy do tworzenia nowego **CComAggObject <** `contained` **>** obiektu bez ponoszenia dodatkowych nakładów [wywołanie funkcji CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615).  
  
```
static HRESULT WINAPI CreateInstance(
    LPUNKNOWN pUnkOuter,
    CComAggObject<contained>** pp);
```  
  
### <a name="parameters"></a>Parametry  
 `pp`  
 [out] Wskaźnik do **CComAggObject\<*** zawarte* **>** wskaźnika. Jeśli `CreateInstance` zakończy się niepowodzeniem, `pp` ustawiono **NULL**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Obiekt zwrócony ma liczebności referencyjnej równej zero, dlatego wywołania `AddRef` natychmiast, następnie użyć **wersji** zwolnienia odwołania na wskaźnik do obiektu, gdy wszystko będzie gotowe.  
  
 Jeśli nie wymagają bezpośredni dostęp do obiektu, ale mimo to chcesz utworzyć nowy obiekt bez ponoszenia dodatkowych nakładów `CoCreateInstance`, użyj [CComCoClass::CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance) zamiast tego.  
  
##  <a name="finalconstruct"></a>  CComAggObject::FinalConstruct  
 Wywołuje się w końcowym etapie konstrukcji obiektu, ta metoda wykonuje wszelkie końcowe inicjowanie na [m_contained](#m_contained) elementu członkowskiego.  
  
```
HRESULT FinalConstruct();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
##  <a name="finalrelease"></a>  CComAggObject::FinalRelease  
 Wywoływana podczas zniszczeniem obiektu, ta metoda zwalnia [m_contained](#m_contained) elementu członkowskiego.  
  
```
void FinalRelease();
```  
  
##  <a name="m_contained"></a>  CComAggObject::m_contained  
 A [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) obiektu pochodzi od klasy.  
  
```
CComContainedObject<contained> m_contained;
```  
  
### <a name="parameters"></a>Parametry  
 `contained`  
 [in] Pochodne klasy, [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) lub [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), jak również od innych interfejsów mają być obsługiwane w obiekcie.  
  
### <a name="remarks"></a>Uwagi  
 Wszystkie **IUnknown** połączenia za pośrednictwem `m_contained` mają delegowane do nieznanego zewnętrzne.  
  
##  <a name="queryinterface"></a>  CComAggObject::QueryInterface  
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
  
### <a name="remarks"></a>Uwagi  
 Jeśli jest żądany interfejs **IUnknown**, `QueryInterface` zwraca wskaźnik do zagregowanych obiektu własnych **IUnknown** i zwiększa liczbę odwołań. W przeciwnym razie ta metoda zapytania dla interfejsu za pomocą `CComContainedObject` — członek, [m_contained](#m_contained).  
  
##  <a name="release"></a>  CComAggObject::Release  
 Zmniejsza odwołanie liczba zagregowane obiektu.  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 W kompilacjach do debugowania **wersji** zwróci wartość, która może być przydatne w przypadku diagnostyki lub testowania. W kompilacjach do debugowania z systemem innym niż **wersji** zawsze zwraca wartość 0.  
  
## <a name="see-also"></a>Zobacz też  
 [Element CComObject — klasa](../../atl/reference/ccomobject-class.md)   
 [Klasa CComPolyObject](../../atl/reference/ccompolyobject-class.md)   
 [DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable)   
 [DECLARE_ONLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_only_aggregatable)   
 [DECLARE_NOT_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_not_aggregatable)   
 [Przegląd klas](../../atl/atl-class-overview.md)
