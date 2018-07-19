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
ms.openlocfilehash: a7aad2093ecc9511c3b15f68963b496130bf3c3f
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37882114"
---
# <a name="ccomcachedtearoffobject-class"></a>Klasa CComCachedTearOffObject
Ta klasa implementuje [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) odrywania interfejsu.  
  
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
 Twoje odrywania klasą pochodną `CComTearOffObjectBase` i interfejsy odrywania obiektu do obsługi.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComCachedTearOffObject::CComCachedTearOffObject](#ccomcachedtearoffobject)|Konstruktor.|  
|[CComCachedTearOffObject:: ~ CComCachedTearOffObject](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComCachedTearOffObject::AddRef](#addref)|Zwiększa liczbę odwołań dla `CComCachedTearOffObject` obiektu.|  
|[CComCachedTearOffObject::FinalConstruct](#finalconstruct)|Wywołania `m_contained::FinalConstruct` (metoda odrywania klasy).|  
|[CComCachedTearOffObject::FinalRelease](#finalrelease)|Wywołania `m_contained::FinalRelease` (metoda odrywania klasy).|  
|[CComCachedTearOffObject::QueryInterface](#queryinterface)|Zwraca wskaźnik do `IUnknown` z `CComCachedTearOffObject` obiektu, lub do żądanego interfejsu w klasie odrywania (klasy `contained`).|  
|[CComCachedTearOffObject::Release](#release)|Dekrementuje liczbę odwołań dla `CComCachedTearOffObject` obiektu i niszczy go, jeśli licznik odwołań ma wartość 0.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComCachedTearOffObject::m_contained](#m_contained)|A `CComContainedObject` obiekt pochodzi od klasy odrywania (klasy `contained`).|  
  
## <a name="remarks"></a>Uwagi  
 `CComCachedTearOffObject` implementuje [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) odrywania interfejsu. Ta klasa różni się od `CComTearOffObject` , `CComCachedTearOffObject` ma swój własny `IUnknown`, niezależne od obiektu właściciela `IUnknown` (właścicielem jest obiekt, dla którego odrywania jest tworzona). `CComCachedTearOffObject` przechowuje swój własny odwoływać się do liczby na jego `IUnknown` i usuwana po jego licznik odwołań wynosi zero. Jednak po wykonaniu zapytania dotyczącego wszystkich jego odrywania interfejsy, licznik odwołań obiektu właściciela `IUnknown` jest zwiększany.  
  
 Jeśli `CComCachedTearOffObject` obiektu Implementowanie odrywania jest już uruchomiony, a interfejs odrywania jest wysyłane zapytanie ponownie, tego samego `CComCachedTearOffObject` obiektu jest ponownie. Natomiast jeśli odrywania interfejs implementowany przez `CComTearOffObject` jest ponownie wykonywane zapytanie dla za pośrednictwem obiektu właściciela innego `CComTearOffObject` zostanie utworzone wystąpienie.  
  
 Klasa właściciel musi implementować `FinalRelease` , a następnie wywołać `Release` w pamięci podręcznej `IUnknown` dla `CComCachedTearOffObject`, który zmniejszy się jego licznik odwołań. Spowoduje to `CComCachedTearOffObject`firmy `FinalRelease` można wywołać i usuwania odrywania.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `CComObjectRootBase`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IUnknown`  
  
 `CComCachedTearOffObject`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  
  
##  <a name="addref"></a>  CComCachedTearOffObject::AddRef  
 Zwiększa liczbę odwołań z `CComCachedTearOffObject` obiektu o 1.  
  
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
 *Wa*  
 [in] Wskaźnik do `IUnknown` z `CComCachedTearOffObject`.  
  
### <a name="remarks"></a>Uwagi  
 Inicjuje `CComContainedObject` elementu członkowskiego, [m_contained](#m_contained).  
  
##  <a name="dtor"></a>  CComCachedTearOffObject:: ~ CComCachedTearOffObject  
 Destruktor.  
  
```
~CComCachedTearOffObject();
```  
  
### <a name="remarks"></a>Uwagi  
 Zwalnia wszystkie przydzielone zasoby i wywołania [FinalRelease](#finalrelease).  
  
##  <a name="finalconstruct"></a>  CComCachedTearOffObject::FinalConstruct  
 Wywołania `m_contained::FinalConstruct` utworzyć `m_contained`, `CComContainedObject` <  `contained`> obiekt umożliwiający dostęp do interfejsu, zaimplementowany przez klasę odrywania.  
  
```
HRESULT FinalConstruct();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowe wartości HRESULT.  
  
##  <a name="finalrelease"></a>  CComCachedTearOffObject::FinalRelease  
 Wywołania `m_contained::FinalRelease` zwolnienie `m_contained`, `CComContainedObject` <  `contained`> obiektu.  
  
```
void FinalRelease();
```  
  
##  <a name="m_contained"></a>  CComCachedTearOffObject::m_contained  
 A [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) obiekt pochodzi od klasy odrywania.  
  
```
CcomContainedObject <contained> m_contained;
```     
  
### <a name="parameters"></a>Parametry  
 *zawiera*  
 [in] Twoje odrywania klasą pochodną `CComTearOffObjectBase` i interfejsy odrywania obiektu do obsługi.  
  
### <a name="remarks"></a>Uwagi  
 Metody `m_contained` dziedziczy umożliwiają dostęp interfejs odrywania w klasie odrywania za pomocą pamięci podręcznej odrywania obiektu `QueryInterface`, `FinalConstruct`, i `FinalRelease`.  
  
##  <a name="queryinterface"></a>  CComCachedTearOffObject::QueryInterface  
 Pobiera wskaźnik do żądanego interfejsu.  
  
```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```  
  
### <a name="parameters"></a>Parametry  
 *IID*  
 [in] Identyfikator GUID interfejsu żądanej.  
  
 *ppvObject*  
 [out] Wskaźnik do wskaźnika interfejsu identyfikowane przez *iid*, lub wartość NULL, jeśli nie można odnaleźć interfejsu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowe wartości HRESULT.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli jest żądany interfejs `IUnknown`, zwraca wskaźnik do `CComCachedTearOffObject`firmy własnych `IUnknown` i zwiększa liczbę odwołań. W przeciwnym razie wysyła zapytanie o interfejs na przy użyciu klasy odrywania [InternalQueryInterface](ccomobjectrootex-class.md#internalqueryinterface) metody dziedziczone z `CComObjectRootEx`.  

  
##  <a name="release"></a>  CComCachedTearOffObject::Release  
 Dekrementuje liczbę odwołań o 1 i, jeśli licznik odwołań to 0, usuwa `CComCachedTearOffObject` obiektu.  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 W kompilacjach nieprzeznaczonych do debugowania zawsze zwraca wartość 0. W przypadku kompilacji do debugowania zwraca wartość, która może być użyteczna, diagnostykę lub testowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CComTearOffObject](../../atl/reference/ccomtearoffobject-class.md)   
 [Klasa CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)   
 [Klasa — Przegląd](../../atl/atl-class-overview.md)
