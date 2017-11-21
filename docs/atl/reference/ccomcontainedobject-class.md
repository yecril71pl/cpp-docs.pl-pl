---
title: Klasa CComContainedObject | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComContainedObject
- ATLCOM/ATL::CComContainedObject
- ATLCOM/ATL::CComContainedObject::CComContainedObject
- ATLCOM/ATL::CComContainedObject::AddRef
- ATLCOM/ATL::CComContainedObject::GetControllingUnknown
- ATLCOM/ATL::CComContainedObject::QueryInterface
- ATLCOM/ATL::CComContainedObject::Release
dev_langs: C++
helpviewer_keywords:
- aggregate objects [C++], in ATL
- aggregation [C++], ATL objects
- CComContainedObject class
ms.assetid: e8616b41-c200-47b8-bf2c-fb9f713ebdad
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8fed68d788403a0c2a822d7e47f50b08d409bbf2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ccomcontainedobject-class"></a>Klasa CComContainedObject
Ta klasa implementuje [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) przez delegowanie do obiektu właściciela **IUnknown**.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template<class Base>  
class CComContainedObject : public Base
```  
  
#### <a name="parameters"></a>Parametry  
 `Base`  
 Pochodne klasy, [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) lub [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md).  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComContainedObject::CComContainedObject](#ccomcontainedobject)|Konstruktor. Inicjuje element członkowski wskaźnik do obiektu właściciela `IUnknown`.|  
|[CComContainedObject:: ~ CComContainedObject](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComContainedObject::AddRef](#addref)|Zwiększa liczbę odwołanie do obiektu właściciela.|  
|[CComContainedObject::GetControllingUnknown](#getcontrollingunknown)|Pobiera obiekt właściciela `IUnknown`.|  
|[CComContainedObject::QueryInterface](#queryinterface)|Pobiera wskaźnik do interfejsu żądana właściciela obiektu.|  
|[CComContainedObject::Release](#release)|Zmniejsza liczba odwołanie do obiektu właściciela.|  
  
## <a name="remarks"></a>Uwagi  
 ATL używa `CComContainedObject` w klasach [CComAggObject](../../atl/reference/ccomaggobject-class.md), [CComPolyObject](../../atl/reference/ccompolyobject-class.md), i [CComCachedTearOffObject](../../atl/reference/ccomcachedtearoffobject-class.md). `CComContainedObject`implementuje [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) przez delegowanie do obiektu właściciela **IUnknown**. (Właścicielem jest obiekt zewnętrzne agregacji lub obiekt, dla której utworzona jest interfejsem oderwania). `CComContainedObject` wywołania `CComObjectRootEx`w `OuterQueryInterface`, `OuterAddRef`, i `OuterRelease`, wszystkie odziedziczone przez `Base`.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `Base`  
  
 `CComContainedObject`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  
  
##  <a name="addref"></a>CComContainedObject::AddRef  
 Zwiększa liczbę odwołanie do obiektu właściciela.  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość, która może być przydatne w przypadku diagnostyki lub testowania.  
  
##  <a name="ccomcontainedobject"></a>CComContainedObject::CComContainedObject  
 Konstruktor.  
  
```
CComContainedObject(void* pv);
```  
  
### <a name="parameters"></a>Parametry  
 `pv`  
 [in] Obiekt właściciela **IUnknown**.  
  
### <a name="remarks"></a>Uwagi  
 Ustawia `m_pOuterUnknown` wskaźnik elementu członkowskiego (dziedziczone przez `Base` klasy) do `pv`.  
  
##  <a name="dtor"></a>CComContainedObject:: ~ CComContainedObject  
 Destruktor.  
  
```
~CComContainedObject();
```  
  
### <a name="remarks"></a>Uwagi  
 Zwalnia wszystkie przydzielone zasoby.  
  
##  <a name="getcontrollingunknown"></a>CComContainedObject::GetControllingUnknown  
 Zwraca `m_pOuterUnknown` wskaźnik elementu członkowskiego (dziedziczone przez *Base* klasy) zawierającego obiektu właściciela **IUnknown**.  
  
```
IUnknown* GetControllingUnknown();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Obiekt właściciela **IUnknown**.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda może być wirtualny Jeśli `Base` została zadeklarowana [DECLARE_GET_CONTROLLING_UNKNOWN](aggregation-and-class-factory-macros.md#declare_get_controlling_unknown) makra.  
  
##  <a name="queryinterface"></a>CComContainedObject::QueryInterface  
 Pobiera wskaźnik do interfejsu żądana właściciela obiektu.  
  
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
  
##  <a name="release"></a>CComContainedObject::Release  
 Zmniejsza liczba odwołanie do obiektu właściciela.  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 W kompilacjach do debugowania **wersji** zwróci wartość, która może być przydatne w przypadku diagnostyki lub testowania. W kompilacjach do debugowania z systemem innym niż **wersji** zawsze zwraca wartość 0.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../../atl/atl-class-overview.md)
