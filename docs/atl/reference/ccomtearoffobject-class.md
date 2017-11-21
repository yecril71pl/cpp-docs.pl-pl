---
title: Klasa CComTearOffObject | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComTearOffObject
- ATLCOM/ATL::CComTearOffObject
- ATLCOM/ATL::CComTearOffObject::CComTearOffObject
- ATLCOM/ATL::CComTearOffObject::AddRef
- ATLCOM/ATL::CComTearOffObject::QueryInterface
- ATLCOM/ATL::CComTearOffObject::Release
- ATLCOM/ATL::CComTearOffObjectBase
- ATLCOM/ATL::m_pOwner
dev_langs: C++
helpviewer_keywords:
- tear-off interfaces, ATL
- tear-off interfaces
- CComTearOffObject class
ms.assetid: d974b598-c6b2-42b1-8360-9190d9d0fbf3
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c4f6782e2e873e844fa1d2eb7a9c1090d887dac9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ccomtearoffobject-class"></a>Klasa CComTearOffObject
Ta klasa implementuje interfejs oderwania.  
  
## <a name="syntax"></a>Składnia  
  
```
template<class Base>
class CComTearOffObject : public Base
```  
  
#### <a name="parameters"></a>Parametry  
 `Base`  
 Pochodne klasy oderwania, `CComTearOffObjectBase` i interfejsy ma obiekt oderwania do obsługi.  
  
 ATL implementuje interfejsy oderwania w dwóch fazach — `CComTearOffObjectBase` metod obsługi liczebności referencyjnej i `QueryInterface`, podczas gdy `CComTearOffObject` implementuje [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509).  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComTearOffObject::CComTearOffObject](#ccomtearoffobject)|Konstruktor.|  
|[CComTearOffObject:: ~ CComTearOffObject](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComTearOffObject::AddRef](#addref)|Zwiększa liczbę odwołania dla `CComTearOffObject` obiektu.|  
|[CComTearOffObject::QueryInterface](#queryinterface)|Zwraca wskaźnik do żądanego interfejsu w klasie oderwania lub klasy właściciela.|  
|[CComTearOffObject::Release](#release)|Zmniejsza liczba odwołanie o `CComTearOffObject` obiektu i niszczy go.|  
  
### <a name="ccomtearoffobjectbase-methods"></a>Metody CComTearOffObjectBase  
  
|||  
|-|-|  
|[CComTearOffObjectBase](#ccomtearoffobjectbase)|Konstruktor.|  
  
### <a name="ccomtearoffobjectbase-data-members"></a>Elementy członkowskie danych CComTearOffObjectBase  
  
|||  
|-|-|  
|[m_pOwner](#m_powner)|Wskaźnik do `CComObject` pochodzi od klasy właściciela.|  
  
## <a name="remarks"></a>Uwagi  
 `CComTearOffObject`implementuje interfejs oderwania jako oddzielny obiekt, który zostanie uruchomiony tylko wtedy, gdy ten interfejs jest kwerenda usługi. Oderwania jest usuwany po jego liczba odwołań wynosi zero. Zazwyczaj należy utworzyć interfejs oderwania dla interfejsu, który jest rzadko używana, ponieważ przy użyciu oderwania zapisuje wskaźnikiem vtable we wszystkich wystąpieniach obiektu głównego.  
  
 Klasa implementacji oderwania z powinien pochodzić `CComTearOffObjectBase` i z jednego z tych interfejsów ma obiekt oderwania do obsługi. `CComTearOffObjectBase`którego ma zastosowany jest szablon się na klasie właściciela i modelu wątku. Klasa właściciela jest klasę obiektu, dla którego oderwania jest implementowana. Jeśli modelu wątków nie zostanie określony, używany jest domyślny model wątków.  
  
 Należy utworzyć mapę COM dla klasy oderwania. Gdy występuje ATL oderwania, utworzy on **CComTearOffObject\<CYourTearOffClass >** lub **CComCachedTearOffObject\<CYourTearOffClass >**.  
  
 Na przykład w przykładowej BEEPER `CBeeper2` klasa jest klasą oderwania i `CBeeper` klasa jest klasą właściciela:  
  
 [!code-cpp[NVC_ATL_COM#43](../../atl/codesnippet/cpp/ccomtearoffobject-class_1.h)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `Base`  
  
 `CComTearOffObject`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  
  
##  <a name="addref"></a>CComTearOffObject::AddRef  
 Zwiększa liczbę odwołanie z `CComTearOffObject` obiekt o jeden.  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość, która może być przydatne w przypadku diagnostyki i testowania.  
  
##  <a name="ccomtearoffobject"></a>CComTearOffObject::CComTearOffObject  
 Konstruktor.  
  
```
CComTearOffObject(void* pv);
```  
  
### <a name="parameters"></a>Parametry  
 `pv`  
 [in] Wskaźnik, który zostanie przekonwertowany na wskaźnik do **element CComObject\<właściciela >** obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Zwiększa liczbę odwołań właściciela o jeden.  
  
##  <a name="dtor"></a>CComTearOffObject:: ~ CComTearOffObject  
 Destruktor.  
  
```
~CComTearOffObject();
```  
  
### <a name="remarks"></a>Uwagi  
 Zwalnia wszystkie przydzielone zasoby, wywołują FinalRelease i zmniejsza moduł zablokować count.  
  
##  <a name="ccomtearoffobjectbase"></a>CComTearOffObject::CComTearOffObjectBase  
 Konstruktor.  
  
```
CComTearOffObjectBase();
```  
  
### <a name="remarks"></a>Uwagi  
 Inicjuje [m_pOwner](#m_powner) członka **NULL**.  
  
##  <a name="m_powner"></a>CComTearOffObject::m_pOwner  
 Wskaźnik do [element CComObject](../../atl/reference/ccomobject-class.md) pochodną obiektu *właściciela*.  
  
```
CComObject<Owner>* m_pOwner;
```  
  
### <a name="parameters"></a>Parametry  
 *Właściciel*  
 [in] Klasa, dla którego oderwania jest implementowana.  
  
### <a name="remarks"></a>Uwagi  
 Wskaźnik jest ustawiana na **NULL** podczas konstruowania.  
  
##  <a name="queryinterface"></a>CComTearOffObject::QueryInterface  
 Pobiera wskaźnik do żądanego interfejsu.  
  
```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```  
  
### <a name="parameters"></a>Parametry  
 `iid`  
 [in] Uzyskanie identyfikatora IID interfejsu żądanej.  
  
 `ppvObject`  
 [out] Wskaźnik do wskaźnika interfejsu identyfikowane przez `iid`, lub **NULL** Jeśli nie można odnaleźć interfejsu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Zapytania najpierw dla interfejsów w klasie oderwania. Jeśli interfejs nie jest, zapytania dotyczące interfejsu właściciela obiektu. Jeśli jest żądany interfejs **IUnknown**, zwraca **IUnknown** właściciela.  
  
##  <a name="release"></a>CComTearOffObject::Release  
 Zmniejsza odwołanie liczba przez jedną i, jeśli liczba odwołań wynosi zero, usuwa `CComTearOffObject`.  
  
```
STDMETHOD_ULONG Release();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 W kompilacjach do debugowania z systemem innym niż zawsze zwraca wartość zero. W kompilacjach debugowania zwraca wartość, która może być przydatne w przypadku diagnostyki lub testowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CComCachedTearOffObject](../../atl/reference/ccomcachedtearoffobject-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
