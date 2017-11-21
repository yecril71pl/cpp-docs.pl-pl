---
title: Klasa CComPolyObject | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComPolyObject
- ATLCOM/ATL::CComPolyObject
- ATLCOM/ATL::CComPolyObject::CComPolyObject
- ATLCOM/ATL::CComPolyObject::AddRef
- ATLCOM/ATL::CComPolyObject::CreateInstance
- ATLCOM/ATL::CComPolyObject::FinalConstruct
- ATLCOM/ATL::CComPolyObject::FinalRelease
- ATLCOM/ATL::CComPolyObject::QueryInterface
- ATLCOM/ATL::CComPolyObject::Release
- ATLCOM/ATL::CComPolyObject::m_contained
dev_langs: C++
helpviewer_keywords:
- aggregate objects [C++], in ATL
- aggregation [C++], ATL objects
- CComPolyObject class
ms.assetid: eaf67c18-e855-48ca-9b15-f1df3106121b
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 49945127d726c1a83ed01f70dee2190622a4c68d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ccompolyobject-class"></a>Klasa CComPolyObject
Ta klasa implementuje **IUnknown** zagregowane lub nieagregowane w obiekcie.  
  
## <a name="syntax"></a>Składnia  
  
```
template<class contained>  
class CComPolyObject : public IUnknown,
      public CComObjectRootEx<contained::_ThreadModel::ThreadModelNoCS>
```  
  
#### <a name="parameters"></a>Parametry  
 `contained`  
 Pochodne klasy, [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) lub [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), jak również od innych interfejsów mają być obsługiwane w obiekcie.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComPolyObject::CComPolyObject](#ccompolyobject)|Konstruktor.|  
|[CComPolyObject:: ~ CComPolyObject](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComPolyObject::AddRef](#addref)|Zwiększa liczbę odwołanie do obiektu.|  
|[CComPolyObject::CreateInstance](#createinstance)|(Statyczny) Służy do tworzenia nowego **CComPolyObject <** `contained`  **>**  obiektu bez ponoszenia dodatkowych nakładów [wywołanie funkcji CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615).|  
|[CComPolyObject::FinalConstruct](#finalconstruct)|Wykonuje końcowego inicjowania elementu `m_contained`.|  
|[CComPolyObject::FinalRelease](#finalrelease)|Wykonuje końcowego zniszczenie `m_contained`.|  
|[CComPolyObject::QueryInterface](#queryinterface)|Pobiera wskaźnik do żądanego interfejsu.|  
|[CComPolyObject::Release](#release)|Zmniejsza liczba odwołanie do obiektu.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComPolyObject::m_contained](#m_contained)|Obiekty delegowane **IUnknown** odwołuje się do nieznanego zewnętrzne, jeśli obiekt jest agregowana w lub do **IUnknown** obiektu, jeśli obiekt nie jest agregowany.|  
  
## <a name="remarks"></a>Uwagi  
 `CComPolyObject`implementuje [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) zagregowane lub nieagregowane w obiekcie.  
  
 Gdy wystąpienie klasy `CComPolyObject` utworzeniu wartość zewnętrznego zaznaczono opcję nieznane. Jeśli jest **NULL**, **IUnknown** jest zaimplementowany dla obiekt nieagregowane. Jeśli nie jest zewnętrzna nieznany **NULL**, **IUnknown** jest zaimplementowany dla obiekt zagregowanych.  
  
 Zaletą używania `CComPolyObject` jest uniknąć oba mających [CComAggObject](../../atl/reference/ccomaggobject-class.md) i [element CComObject](../../atl/reference/ccomobject-class.md) w module obsługi zagregowane i nieagregowane przypadkach. Pojedynczy `CComPolyObject` obiektu obsługuje w obu przypadkach. Oznacza to, że tylko jedna kopia vtable i jedną kopię funkcji istnieje w module. Jeśli Twoje vtable jest duży, to znacznie zmniejszyć rozmiar modułu użytkownika. Jednak jeśli Twoje vtable jest mały, za pomocą `CComPolyObject` może spowodować nieco większy rozmiar modułu, ponieważ nie jest zoptymalizowana dla obiekt zagregowane lub nieagregowane są `CComAggObject` i `CComObject`.  
  
 Jeśli `DECLARE_POLY_AGGREGATABLE` makro jest określona w definicji klasy do obiektu, `CComPolyObject` będzie służyć do tworzenia obiektu. `DECLARE_POLY_AGGREGATABLE`będą automatycznie deklarowane Jeśli używasz Kreator projektu ATL do utworzenia pełnej kontroli lub sterowania w programie Internet Explorer.  
  
 Jeśli zagregowane, `CComPolyObject` obiekt ma własną **IUnknown**, niezależnie od obiektu zewnętrznego **IUnknown**i obsługuje licznika odwołania. `CComPolyObject`używa [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) delegować do zewnętrznego nieznany.  
  
 Aby uzyskać więcej informacji na temat agregacji, zobacz artykuł [podstawy ATL obiektów COM](../../atl/fundamentals-of-atl-com-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `CComObjectRootBase`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IUnknown`  
  
 `CComPolyObject`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  
  
##  <a name="addref"></a>CComPolyObject::AddRef  
 Zwiększa liczbę odwołanie do obiektu.  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość, która może być przydatne w przypadku diagnostyki lub testowania.  
  
##  <a name="ccompolyobject"></a>CComPolyObject::CComPolyObject  
 Konstruktor.  
  
```
CComPolyObject(void* pv);
```  
  
### <a name="parameters"></a>Parametry  
 `pv`  
 [in] Wskaźnik do nieznanego zewnętrznego, jeśli obiekt ma być połączone, lub **NULL** Jeśli obiektu, jeśli obiekt nie jest agregowany.  
  
### <a name="remarks"></a>Uwagi  
 Inicjuje `CComContainedObject` członka danych [m_contained](#m_contained)i zwiększa liczbę blokad modułu.  
  
 Destruktor zmniejsza liczbę blokad modułu.  
  
##  <a name="dtor"></a>CComPolyObject:: ~ CComPolyObject  
 Destruktor.  
  
```
~CComPolyObject();
```  
  
### <a name="remarks"></a>Uwagi  
 Zwalnia wszystkie przydzielone zasoby, wywołania [FinalRelease](#finalrelease), i zmniejsza liczbę blokad modułu.  
  
##  <a name="createinstance"></a>CComPolyObject::CreateInstance  
 Służy do tworzenia nowego **CComPolyObject <** `contained`  **>**  obiektu bez ponoszenia dodatkowych nakładów [wywołanie funkcji CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615).  
  
```
static HRESULT WINAPI CreateInstance(  
    LPUNKNOWN pUnkOuter, 
    CComPolyObject<contained>** pp);
```  
  
### <a name="parameters"></a>Parametry  
 `pp`  
 [out] Wskaźnik do **CComPolyObject <** `contained`  **>**  wskaźnika. Jeśli `CreateInstance` zakończy się niepowodzeniem, `pp` ustawiono **NULL**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Obiekt zwrócony ma liczebności referencyjnej równej zero, dlatego wywołania `AddRef` natychmiast, następnie użyć **wersji** zwolnienia odwołania na wskaźnik do obiektu, gdy wszystko będzie gotowe.  
  
 Jeśli nie wymagają bezpośredni dostęp do obiektu, ale mimo to chcesz utworzyć nowy obiekt bez ponoszenia dodatkowych nakładów `CoCreateInstance`, użyj [CComCoClass::CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance) zamiast tego.  
  
##  <a name="finalconstruct"></a>CComPolyObject::FinalConstruct  
 Wywołuje się w końcowym etapie konstrukcji obiektu, ta metoda wykonuje wszelkie końcowe inicjowanie na [m_contained](#m_contained) element członkowski danych.  
  
```
HRESULT FinalConstruct();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
##  <a name="finalrelease"></a>CComPolyObject::FinalRelease  
 Wywoływana podczas zniszczeniem obiektu, ta metoda zwalnia [m_contained](#m_contained) element członkowski danych.  
  
```
void FinalRelease();
```  
  
##  <a name="m_contained"></a>CComPolyObject::m_contained  
 A [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) obiektu pochodzi od klasy.  
  
```
CComContainedObject<contained> m_contained;
```  
  
### <a name="parameters"></a>Parametry  
 `contained`  
 [in] Pochodne klasy, [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) lub [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), jak również od innych interfejsów mają być obsługiwane w obiekcie.  
  
### <a name="remarks"></a>Uwagi  
 **IUnknown** połączenia za pośrednictwem `m_contained` mają delegowane do nieznanego zewnętrzne, jeśli obiekt jest agregowana lub do **IUnknown** tego obiektu, jeśli obiekt nie jest agregowany.  
  
##  <a name="queryinterface"></a>CComPolyObject::QueryInterface  
 Pobiera wskaźnik do żądanego interfejsu.  
  
```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>  
HRESULT QueryInterface(Q** pp);
```  
  
### <a name="parameters"></a>Parametry  
 `Q`  
 Interfejs COM.  
  
 `iid`  
 [in] Identyfikator żądanego interfejsu.  
  
 `ppvObject`  
 [out] Wskaźnik do wskaźnika interfejsu identyfikowane przez `iid`. Jeśli obiekt nie obsługuje ten interfejs `ppvObject` ustawiono **NULL**.  
  
 `pp`  
 [out] Wskaźnik do interfejsu identyfikowane przez **__uuidof(Q)**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Zagregowane obiektu, jeśli jest żądany interfejs **IUnknown**, `QueryInterface` zwraca wskaźnik do zagregowanych obiektu własnych **IUnknown** i zwiększa liczbę odwołań. W przeciwnym razie ta metoda zapytania dla interfejsu za pomocą `CComContainedObject` członka danych [m_contained](#m_contained).  
  
##  <a name="release"></a>CComPolyObject::Release  
 Zmniejsza liczba odwołanie do obiektu.  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 W kompilacjach do debugowania **wersji** zwróci wartość, która może być przydatne w przypadku diagnostyki lub testowania. W kompilacjach nondebug **wersji** zawsze zwraca wartość 0.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)   
 [DECLARE_POLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_poly_aggregatable)   
 [Przegląd klas](../../atl/atl-class-overview.md)
