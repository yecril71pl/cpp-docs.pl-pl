---
title: "Makra wejścia interfejsu COM | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 03/28/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atlcom/ATL::COM_INTERFACE_ENTRY
- atlcom/ATL::COM_INTERFACE_ENTRY_IID
- atlcom/ATL::COM_INTERFACE_ENTRY_AGGREGATE
- atlcom/ATL::COM_INTERFACE_ENTRY_AGGREGATE_BLIND
- atlcom/ATL::COM_INTERFACE_ENTRY_AUTOAGGREGATE
- atlcom/ATL::COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND
- atlcom/ATL::COM_INTERFACE_ENTRY_BREAK
- atlcom/ATL::COM_INTERFACE_ENTRY_CACHED_TEAR_OFF
- atlcom/ATL::COM_INTERFACE_ENTRY_TEAR_OFF
- atlcom/ATL::COM_INTERFACE_ENTRY_CHAIN
- atlcom/ATL::COM_INTERFACE_ENTRY_FUNC
- atlcom/ATL::COM_INTERFACE_ENTRY_FUNC_BLIND
- atlcom/ATL::COM_INTERFACE_ENTRY_NOINTERFACE
dev_langs: C++
helpviewer_keywords: COM interfaces, COM interface entry macros
ms.assetid: 19dcb768-2e1f-4b8d-a618-453a01a4bd00
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 281829593087a936f201000faaa42f698344d3b5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cominterfaceentry-macros"></a>Com_interface_entry — makra  
 Te makra wprowadź interfejsy obiektu do jego mapie modelu COM, dzięki czemu są one dostępne przez `QueryInterface`. Kolejność wpisów w mapie modelu COM jest interfejsy kolejności będzie sprawdzana pasujący **IID** podczas `QueryInterface`.  

 |||
 |-|-|
 |[COM_INTERFACE_ENTRY —](#com_interface_entry)|Wprowadza interfejsy do mapy interfejsu COM.|  
|[COM_INTERFACE_ENTRY2](#com_interface_entry2)|Używanie tego makra do odróżniania dwóch gałęziach dziedziczenia.|  
|[COM_INTERFACE_ENTRY_IID](#com_interface_entry_iid)|Umożliwia to makro wprowadzić interfejsu w mapie modelu COM i określić jej identyfikator IID.|  
|[COM_INTERFACE_ENTRY2_IID](#com_interface_entry2_iid)|Taki sam jak [COM_INTERFACE_ENTRY2](#com_interface_entry2), z wyjątkiem możesz określić inny identyfikator IID.|  
|[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)|Gdy interfejs identyfikowane przez `iid` zostanie zapytany o, `COM_INTERFACE_ENTRY_AGGREGATE` przekazuje do `punk`.|  
|[COM_INTERFACE_ENTRY_AGGREGATE_BLIND](#com_interface_entry_aggregate_blind)|Taki sam jak [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), ale powoduje wykonanie zapytania dotyczącego żadnych IID przesyłania zapytań do `punk`.|  
|[COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate)|Taki sam jak [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), chyba że `punk` jest **NULL**, automatycznie tworzy agregacji opisanego przez `clsid`.|  
|[COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND](#com_interface_entry_autoaggregate_blind)|Taki sam jak [COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate), ale powoduje wykonanie zapytania dotyczącego żadnych IID przesyłania zapytań do `punk`i w razie `punk` jest **NULL**, automatycznego tworzenia Agregacja opisanego przez `clsid`.|  
|[COM_INTERFACE_ENTRY_BREAK](#com_interface_entry_break)|Powoduje, że program do wywołania [debugbreak —](http://msdn.microsoft.com/library/windows/desktop/ms679297) po jest poddawany kwerendzie dla określonego interfejsu.|  
|[COM_INTERFACE_ENTRY_CACHED_TEAR_OFF](#com_interface_entry_cached_tear_off)|Zapisuje dane specyficzne dla interfejsu dla każdego wystąpienia.|  
|[COM_INTERFACE_ENTRY_TEAR_OFF](#com_interface_entry_tear_off)|Udostępnia interfejsy oderwania.|  
|[COM_INTERFACE_ENTRY_CHAIN](#com_interface_entry_chain)|Przetwarza mapę modelu COM klasy podstawowej, gdy przetwarzanie osiągnie ten wpis w mapie modelu COM.|  
|[COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func)|Ogólne mechanizm przechwytywanie do jego ATL `QueryInterface` logiki.|  
|[COM_INTERFACE_ENTRY_FUNC_BLIND](#com_interface_entry_func_blind)|Taki sam jak [COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func), ale wykonanie zapytania dotyczącego żadnych IID powoduje wywołanie `func`.|  
|[COM_INTERFACE_ENTRY_NOINTERFACE](#com_interface_entry_nointerface)|Zwraca **E_NOINTERFACE** i kończy COM mapy przetwarzania, gdy określony interfejs zostanie zapytany o.|  

## <a name="requirements"></a>Wymagania
**Nagłówek:** atlcom.h

## <a name="com_interface_entry"></a>COM_INTERFACE_ENTRY —
Wprowadza interfejsy do mapy interfejsu COM.

### <a name="syntax"></a>Składnia

```
COM_INTERFACE_ENTRY( x )
```
### <a name="parameters"></a>Parametry

x [in] Nazwa interfejsu obiektu klasa pochodzi od bezpośrednio.

### <a name="remarks"></a>Uwagi
Zazwyczaj jest to najczęściej używanego typu wpisu.

### <a name="example"></a>Przykład
```cpp
BEGIN_COM_MAP(CThisExample)
   COM_INTERFACE_ENTRY(IThisExample)
   COM_INTERFACE_ENTRY(IDispatch)
   COM_INTERFACE_ENTRY(ISupportErrorInfo)
END_COM_MAP()
```
### <a name="requirements"></a>Wymagania
**Nagłówek:** atlcom.h
  
##  <a name="com_interface_entry2"></a>COM_INTERFACE_ENTRY2  
 Używanie tego makra do odróżniania dwóch gałęziach dziedziczenia.  
  
```
COM_INTERFACE_ENTRY2(x, x2)
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 [in] Nazwa interfejsu, który ma zostać udostępniona z obiektu.  
  
 `x2`  
 [in] Nazwa gałęzi dziedziczenia, z którego *x* jest widoczna.  
  
### <a name="remarks"></a>Uwagi  
 Na przykład, jeśli pochodzi z obiektu klasy z dwóch podwójne interfejsy, należy udostępnić `IDispatch` przy użyciu `COM_INTERFACE_ENTRY2` ponieważ `IDispatch` można uzyskać z jednego z interfejsów.  
  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Windowing#118](../../atl/codesnippet/cpp/com-map-macros_2.h)]  
  
##  <a name="com_interface_entry_iid"></a>COM_INTERFACE_ENTRY_IID  
 Umożliwia to makro wprowadzić interfejsu w mapie modelu COM i określić jej identyfikator IID.  
  
```
COM_INTERFACE_ENTRY_IID(iid, x)
```  
  
### <a name="parameters"></a>Parametry  
 `iid`  
 [in] Identyfikator GUID interfejsu widoczne.  
  
 *x*  
 [in] Nazwa klasy, których vtable mają być widoczne jako interfejs identyfikowane przez `iid`.  
  
 
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Windowing#117](../../atl/codesnippet/cpp/com-map-macros_3.h)]  
  
##  <a name="com_interface_entry2_iid"></a>COM_INTERFACE_ENTRY2_IID  
 Taki sam jak [COM_INTERFACE_ENTRY2](#com_interface_entry2), z wyjątkiem możesz określić inny identyfikator IID.  
  
```
COM_INTERFACE_ENTRY2_IID(iid, x, x2)
```   
  
### <a name="parameters"></a>Parametry  
 `iid`  
 [in] Identyfikator GUID, który określisz dla interfejsu.  
  
 *x*  
 [in] Nazwa interfejsu, który pochodzi bezpośrednio z obiektu klasy.  
  
 `x2`  
 [in] Nazwa drugi interfejs, który pochodzi bezpośrednio z obiektu klasy.  
  
##  <a name="com_interface_entry_aggregate"></a>COM_INTERFACE_ENTRY_AGGREGATE  
 Gdy interfejs identyfikowane przez `iid` zostanie zapytany o, `COM_INTERFACE_ENTRY_AGGREGATE` przekazuje do `punk`.  
  
```
COM_INTERFACE_ENTRY_AGGREGATE(iid, punk)
```  
  
### <a name="parameters"></a>Parametry  
 `iid`  
 [in] Identyfikator GUID interfejsu dotyczy zapytanie.  
  
 `punk`  
 [in] Nazwa **IUnknown** wskaźnika.  
  
### <a name="remarks"></a>Uwagi  
 `punk` Przyjęto, że parametr wskaż wewnętrzny nieznany agregacji lub **NULL**, w którym to przypadku wpis zostanie zignorowany. Zazwyczaj będzie **CoCreate** agregacji w `FinalConstruct`.  
  
  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Windowing#112](../../atl/codesnippet/cpp/com-map-macros_4.h)]  
  
##  <a name="com_interface_entry_aggregate_blind"></a>COM_INTERFACE_ENTRY_AGGREGATE_BLIND  
 Taki sam jak [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), ale powoduje wykonanie zapytania dotyczącego żadnych IID przesyłania zapytań do `punk`.  
  
```
COM_INTERFACE_ENTRY_AGGREGATE_BLIND(punk)
```  
  
### <a name="parameters"></a>Parametry  
 `punk`  
 [in] Nazwa **IUnknown** wskaźnika.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli działanie interfejsu nie powiodło się, przetwarzania na mapie modelu COM jest kontynuowane.  
  
  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Windowing#113](../../atl/codesnippet/cpp/com-map-macros_5.h)]  
  

##  <a name="com_interface_entry_autoaggregate"></a>COM_INTERFACE_ENTRY_AUTOAGGREGATE  
 Taki sam jak [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), chyba że `punk` jest **NULL**, automatycznie tworzy agregacji opisanego przez `clsid`.  
  
```
COM_INTERFACE_ENTRY_AUTOAGGREGATE(iid, punk, clsid)
```   
  
### <a name="parameters"></a>Parametry  
 `iid`  
 [in] Identyfikator GUID interfejsu dotyczy zapytanie.  
  
 `punk`  
 [in] Nazwa **IUnknown** wskaźnika. Musi być elementem członkowskim klasy zawierające mapie modelu COM.  
  
 `clsid`  
 [in] Identyfikator zagregowaną, która zostanie utworzona, jeśli `punk` jest **NULL**.  
  
### <a name="remarks"></a>Uwagi  
  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Windowing#114](../../atl/codesnippet/cpp/com-map-macros_6.h)]  
  
##  <a name="com_interface_entry_autoaggregate_blind"></a>COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND  
 Taki sam jak [COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate), ale powoduje wykonanie zapytania dotyczącego żadnych IID przesyłania zapytań do `punk`i w razie `punk` jest **NULL**, automatycznego tworzenia Agregacja opisanego przez `clsid`.  
  
```
COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND(punk, clsid)
```  
  
### <a name="parameters"></a>Parametry  
 `punk`  
 [in] Nazwa **IUnknown** wskaźnika. Musi być elementem członkowskim klasy zawierające mapie modelu COM.  
  
 `clsid`  
 [in] Identyfikator zagregowaną, która zostanie utworzona, jeśli `punk` jest **NULL**.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli działanie interfejsu nie powiodło się, przetwarzania na mapie modelu COM jest kontynuowane.  
  
  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Windowing#115](../../atl/codesnippet/cpp/com-map-macros_7.h)]  
  
##  <a name="com_interface_entry_break"></a>COM_INTERFACE_ENTRY_BREAK  
 Powoduje, że program do wywołania [debugbreak —](http://msdn.microsoft.com/library/windows/desktop/ms679297) po jest poddawany kwerendzie dla określonego interfejsu.  
  
```
COM_INTERFACE_ENTRY_BREAK(x)
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 [in] Tekst używany do utworzenia identyfikatora interfejsu.  
  
### <a name="remarks"></a>Uwagi  
 Interfejs IID zostanie wykonane przez dołączenie *x* do `IID_`. Na przykład jeśli *x* jest `IPersistStorage`, będzie uzyskanie identyfikatora IID `IID_IPersistStorage`.  
  
  
  
##  <a name="com_interface_entry_cached_tear_off"></a>COM_INTERFACE_ENTRY_CACHED_TEAR_OFF  
 Zapisuje dane specyficzne dla interfejsu dla każdego wystąpienia.  
  
```
COM_INTERFACE_ENTRY_CACHED_TEAR_OFF(iid, x, punk)
```   
  
### <a name="parameters"></a>Parametry  
 `iid`  
 [in] Identyfikator GUID interfejsu oderwania.  
  
 *x*  
 [in] Nazwa klasy implementującej interfejs.  
  
 `punk`  
 [in] Nazwa **IUnknown** wskaźnika. Musi być elementem członkowskim klasy zawierające mapie modelu COM. Powinien być inicjowany do **NULL** w Konstruktorze obiektu klasy.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli ten interfejs nie jest używany, to zmniejsza całkowity rozmiar wystąpienia obiektu.  
  
  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_COM#54](../../atl/codesnippet/cpp/com-map-macros_8.h)]  
  
##  <a name="com_interface_entry_tear_off"></a>COM_INTERFACE_ENTRY_TEAR_OFF  
 Udostępnia interfejsy oderwania.  
  
```
COM_INTERFACE_ENTRY_TEAR_OFF(iid, x)
```  
  
### <a name="parameters"></a>Parametry  
 `iid`  
 [in] Identyfikator GUID interfejsu oderwania.  
  
 *x*  
 [in] Nazwa klasy implementującej interfejs.  
  
### <a name="remarks"></a>Uwagi  
 Interfejs oderwania jest zaimplementowany jako oddzielny obiekt, który zostanie uruchomiony za każdym razem, gdy interfejs reprezentuje zostanie zapytany o. Zazwyczaj należy utworzyć interfejsu jako oderwania Jeśli interfejs jest rzadko używana, ponieważ to wskaźnikiem vtable jest zapisywany w każdym wystąpieniu obiektu głównego. Oderwania jest usuwany po jego liczba odwołań wynosi zero. Klasa implementacji oderwania powinien pochodzić z `CComTearOffObjectBase` i ma własną COM mapy.  
  
  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_COM#1](../../atl/codesnippet/cpp/com-map-macros_1.h)]  
  
##  <a name="com_interface_entry_chain"></a>COM_INTERFACE_ENTRY_CHAIN  
 Przetwarza mapę modelu COM klasy podstawowej, gdy przetwarzanie osiągnie ten wpis w mapie modelu COM.  
  
```
COM_INTERFACE_ENTRY_CHAIN(classname)
```  
  
### <a name="parameters"></a>Parametry  
 *ClassName*  
 [in] Klasa podstawowa bieżącego obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Na przykład w poniższym kodzie:  
  
 [!code-cpp[NVC_ATL_Windowing#116](../../atl/codesnippet/cpp/com-map-macros_9.h)]  
  
 Należy pamiętać, że pierwszy wpis w mapie modelu COM musi być interfejsem na obiektu zawierającego mapy COM. W związku z tym nie można uruchomić wpisy mapy COM z `COM_INTERFACE_ENTRY_CHAIN`, co powoduje, że na mapie modelu COM z innego obiektu do wyszukania w punkcie gdzie **COM_INTERFACE_ENTRY_CHAIN (**`COtherObject`**)** zostanie wyświetlone na mapie modelu COM do obiektu. Jeśli chcesz najpierw wyszukać mapie modelu COM z innym obiektem, Dodaj wpis interfejs dla **IUnknown** do mapy COM następnie łańcucha innego obiektu COM mapy. Na przykład:  
  
 [!code-cpp[NVC_ATL_Windowing#111](../../atl/codesnippet/cpp/com-map-macros_10.h)]  
  
  
  
##  <a name="com_interface_entry_func"></a>COM_INTERFACE_ENTRY_FUNC  
 Ogólne mechanizm przechwytywanie do jego ATL `QueryInterface` logiki.  
  
```
COM_INTERFACE_ENTRY_FUNC(iid, dw, func)
```   
  
### <a name="parameters"></a>Parametry  
 `iid`  
 [in] Identyfikator GUID interfejsu widoczne.  
  
 `dw`  
 [in] Parametr przekazywana do `func`.  
  
 `func`  
 [in] Wskaźnik funkcji, który zwróci `iid`.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli *iid* odpowiada uzyskanie identyfikatora IID interfejsu dotyczy zapytanie, a następnie funkcji określonej przez `func` jest wywoływana. Deklaracja funkcji powinny być:  
  
 `HRESULT WINAPI func(void* pv, REFIID riid, LPVOID* ppv, DWORD_PTR dw);`  
  
 Po wywołaniu funkcji `pv` wskazuje obiekt klasy. `riid` Parametr odnosi się do interfejsu, którego dotyczy zapytanie, `ppv` jest wskaźnik do lokalizacji, w której funkcja powinna przechowywać wskaźnika interfejsu, i `dw` jest parametru określonego we wpisie. Funkcja należy ustawić \* `ppv` do **NULL** i zwracać **E_NOINTERFACE** lub **S_FALSE** Jeśli go nie zwraca interfejsu. Z **E_NOINTERFACE**, kończy przetwarzanie mapy COM. Z **S_FALSE**, przetwarzania mapy COM będzie nadal występował, nawet jeśli została zwrócona ma wskaźnika interfejsu. Jeśli funkcja zwraca wskaźnika interfejsu, powinien on zwrócić `S_OK`.  
  
  
  
##  <a name="com_interface_entry_func_blind"></a>COM_INTERFACE_ENTRY_FUNC_BLIND  
 Taki sam jak [COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func), ale wykonanie zapytania dotyczącego żadnych IID powoduje wywołanie `func`.  
  
```
COM_INTERFACE_ENTRY_FUNC_BLIND(dw, func)
```  
  
### <a name="parameters"></a>Parametry  
 `dw`  
 [in] Parametr przekazywana do `func`.  
  
 `func`  
 [in] Funkcja, która jest wywoływana, gdy ten wpis w mapie modelu COM jest przetwarzany.  
  
### <a name="remarks"></a>Uwagi  
 Jakiekolwiek niepowodzenie spowoduje, że przetwarzanie na kontynuowanie na mapie modelu COM. Jeśli funkcja zwraca wskaźnika interfejsu, powinien on zwrócić `S_OK`.  
  
  
##  <a name="com_interface_entry_nointerface"></a>COM_INTERFACE_ENTRY_NOINTERFACE  
 Zwraca **E_NOINTERFACE** i kończy COM mapy przetwarzania, gdy określony interfejs zostanie zapytany o.  
  
```
COM_INTERFACE_ENTRY_NOINTERFACE(x)
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 [in] Tekst używany do utworzenia identyfikatora interfejsu.  
  
### <a name="remarks"></a>Uwagi  
 To makro umożliwia uniemożliwić używany w przypadku danego interfejsu. Na przykład można wstawić to makro do Twojej COM mapowania przed `COM_INTERFACE_ENTRY_AGGREGATE_BLIND` aby zapobiec przekazywane do wartości zagregowanej nieznany wewnętrzny zapytania dla interfejsu.  
  
 Interfejs IID zostanie wykonane przez dołączenie *x* do `IID_`. Na przykład jeśli *x* jest `IPersistStorage`, będzie uzyskanie identyfikatora IID `IID_IPersistStorage`.  
  
  