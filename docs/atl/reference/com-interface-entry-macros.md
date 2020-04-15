---
title: Makra wpisu interfejsu COM
ms.date: 03/28/2017
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
helpviewer_keywords:
- COM interfaces, COM interface entry macros
ms.assetid: 19dcb768-2e1f-4b8d-a618-453a01a4bd00
ms.openlocfilehash: bb7498f639f463290a4a6593ef7c0fbac09b539b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326678"
---
# <a name="com_interface_entry-macros"></a>makra COM_INTERFACE_ENTRY

Te makra wchodzą do interfejsów obiektu na mapie COM, dzięki `QueryInterface`czemu można uzyskać do nich dostęp za pomocą programu . Kolejność wpisów na mapie COM jest interfejsy zamówienia zostaną sprawdzone pod `QueryInterface`kątem pasującego identyfikatora podczas .

|||
|-|-|
|[COM_INTERFACE_ENTRY](#com_interface_entry)|Wprowadza interfejsy do mapy interfejsu COM.|
|[COM_INTERFACE_ENTRY2](#com_interface_entry2)|To makro służy do rozróżniania dwóch gałęzi dziedziczenia.|
|[COM_INTERFACE_ENTRY_IID](#com_interface_entry_iid)|Użyj tego makra, aby wprowadzić interfejs do mapy COM i określić jego identyfikator.|
|[COM_INTERFACE_ENTRY2_IID](#com_interface_entry2_iid)|Tak samo jak [COM_INTERFACE_ENTRY2](#com_interface_entry2), z tą różnicą, że można określić inny identyfikator.|
|[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)|Gdy interfejs identyfikowany przez *iid* `COM_INTERFACE_ENTRY_AGGREGATE` jest poszukiwany, przekazuje do . `punk`|
|[COM_INTERFACE_ENTRY_AGGREGATE_BLIND](#com_interface_entry_aggregate_blind)|Tak samo jak [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), z tą różnicą, że wykonywanie zapytań dla dowolnego identyfikatora powoduje przekazywanie zapytania do *punk*.|
|[COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate)|Tak samo jak [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), chyba że *punk* ma wartość NULL, automatycznie tworzy agregat opisany przez *clsid*.|
|[COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND](#com_interface_entry_autoaggregate_blind)|Tak samo jak [COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate), z tą różnicą, że wykonywanie zapytań dla dowolnego identyfikatora powoduje przekazywanie zapytania do *punka,* a jeśli *punk* ma wartość NULL, automatyczne tworzenie agregacji opisanej przez *clsid*.|
|[COM_INTERFACE_ENTRY_BREAK](#com_interface_entry_break)|Powoduje, że program do [wywołania DebugBreak,](/windows/win32/api/debugapi/nf-debugapi-debugbreak) gdy określony interfejs jest poszukiwany.|
|[COM_INTERFACE_ENTRY_CACHED_TEAR_OFF](#com_interface_entry_cached_tear_off)|Zapisuje dane specyficzne dla interfejsu dla każdego wystąpienia.|
|[COM_INTERFACE_ENTRY_TEAR_OFF](#com_interface_entry_tear_off)|Udostępnia oderwane interfejsy.|
|[COM_INTERFACE_ENTRY_CHAIN](#com_interface_entry_chain)|Przetwarza mapę COM klasy podstawowej, gdy przetwarzanie osiągnie ten wpis na mapie COM.|
|[COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func)|Ogólny mechanizm podłączania do `QueryInterface` logiki ATL.|
|[COM_INTERFACE_ENTRY_FUNC_BLIND](#com_interface_entry_func_blind)|Tak samo jak [COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func), z tą różnicą, że wykonywanie zapytań o dowolny identyfikator powoduje wywołanie *func*.|
|[COM_INTERFACE_ENTRY_NOINTERFACE](#com_interface_entry_nointerface)|Zwraca E_NOINTERFACE i kończy przetwarzanie map COM, gdy określony interfejs jest poszukiwany.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

## <a name="com_interface_entry"></a><a name="com_interface_entry"></a>COM_INTERFACE_ENTRY

Wprowadza interfejsy do mapy interfejsu COM.

### <a name="syntax"></a>Składnia

```
COM_INTERFACE_ENTRY( x )
```

### <a name="parameters"></a>Parametry

*X*<br/>
[w] Nazwa interfejsu obiektu klasy pochodzi bezpośrednio.

### <a name="remarks"></a>Uwagi

Zazwyczaj jest to typ wpisu, którego używasz najczęściej.

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

## <a name="com_interface_entry2"></a><a name="com_interface_entry2"></a>COM_INTERFACE_ENTRY2

To makro służy do rozróżniania dwóch gałęzi dziedziczenia.

```
COM_INTERFACE_ENTRY2(x, x2)
```

### <a name="parameters"></a>Parametry

*X*<br/>
[w] Nazwa interfejsu, który chcesz udostępnić z obiektu.

*x2*<br/>
[w] Nazwa gałęzi dziedziczenia, z której *x* jest narażony.

### <a name="remarks"></a>Uwagi

Na przykład jeśli pochodzisz obiektu klasy z dwóch interfejsów podwójnych, można udostępnić `IDispatch` przy użyciu COM_INTERFACE_ENTRY2 ponieważ `IDispatch` można uzyskać z jednego z interfejsów.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#118](../../atl/codesnippet/cpp/com-map-macros_2.h)]

## <a name="com_interface_entry_iid"></a><a name="com_interface_entry_iid"></a>COM_INTERFACE_ENTRY_IID

Użyj tego makra, aby wprowadzić interfejs do mapy COM i określić jego identyfikator.

```
COM_INTERFACE_ENTRY_IID(iid, x)
```

### <a name="parameters"></a>Parametry

*Iid*<br/>
[w] Identyfikator GUID interfejsu narażony.

*X*<br/>
[w] Nazwa klasy, której vtable będą widoczne jako interfejs identyfikowany przez *iid*.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#117](../../atl/codesnippet/cpp/com-map-macros_3.h)]

## <a name="com_interface_entry2_iid"></a><a name="com_interface_entry2_iid"></a>COM_INTERFACE_ENTRY2_IID

Tak samo jak [COM_INTERFACE_ENTRY2](#com_interface_entry2), z tą różnicą, że można określić inny identyfikator.

```
COM_INTERFACE_ENTRY2_IID(iid, x, x2)
```

### <a name="parameters"></a>Parametry

*Iid*<br/>
[w] Identyfikator GUID, który określasz dla interfejsu.

*X*<br/>
[w] Nazwa interfejsu, który obiekt klasy pochodzi bezpośrednio.

*x2*<br/>
[w] Nazwa drugiego interfejsu, który obiekt klasy pochodzi bezpośrednio.

## <a name="com_interface_entry_aggregate"></a><a name="com_interface_entry_aggregate"></a>COM_INTERFACE_ENTRY_AGGREGATE

Gdy interfejs identyfikowany przez *iid* jest poszukiwany, COM_INTERFACE_ENTRY_AGGREGATE przekazuje do *punka.*

```
COM_INTERFACE_ENTRY_AGGREGATE(iid, punk)
```

### <a name="parameters"></a>Parametry

*Iid*<br/>
[w] Identyfikator GUID interfejsu, do który jest poszukiwany.

*Punk*<br/>
[w] Nazwa wskaźnika. `IUnknown`

### <a name="remarks"></a>Uwagi

Przyjmuje się, że parametr *punk* wskazuje wewnętrzną niewiadomą agregacji lub null, w którym to przypadku wpis jest ignorowany. Zazwyczaj agregacja `CoCreate` w `FinalConstruct`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#112](../../atl/codesnippet/cpp/com-map-macros_4.h)]

## <a name="com_interface_entry_aggregate_blind"></a><a name="com_interface_entry_aggregate_blind"></a>COM_INTERFACE_ENTRY_AGGREGATE_BLIND

Tak samo jak [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), z tą różnicą, że wykonywanie zapytań dla dowolnego identyfikatora powoduje przekazywanie zapytania do *punk*.

```
COM_INTERFACE_ENTRY_AGGREGATE_BLIND(punk)
```

### <a name="parameters"></a>Parametry

*Punk*<br/>
[w] Nazwa wskaźnika. `IUnknown`

### <a name="remarks"></a>Uwagi

Jeśli kwerenda interfejsu nie powiedzie się, przetwarzanie mapy COM jest kontynuowane.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#113](../../atl/codesnippet/cpp/com-map-macros_5.h)]

## <a name="com_interface_entry_autoaggregate"></a><a name="com_interface_entry_autoaggregate"></a>COM_INTERFACE_ENTRY_AUTOAGGREGATE

Tak samo jak [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), chyba że *punk* ma wartość NULL, automatycznie tworzy agregat opisany przez *clsid*.

```
COM_INTERFACE_ENTRY_AUTOAGGREGATE(iid, punk, clsid)
```

### <a name="parameters"></a>Parametry

*Iid*<br/>
[w] Identyfikator GUID interfejsu, do który jest poszukiwany.

*Punk*<br/>
[w] Nazwa wskaźnika. `IUnknown` Musi być członkiem klasy zawierającej mapę COM.

*Clsid*<br/>
[w] Identyfikator agregacji, który zostanie utworzony, jeśli *punk* jest NULL.

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#114](../../atl/codesnippet/cpp/com-map-macros_6.h)]

## <a name="com_interface_entry_autoaggregate_blind"></a><a name="com_interface_entry_autoaggregate_blind"></a>COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND

Tak samo jak [COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate), z tą różnicą, że wykonywanie zapytań dla dowolnego identyfikatora powoduje przekazywanie zapytania do *punka,* a jeśli *punk* ma wartość NULL, automatyczne tworzenie agregacji opisanej przez *clsid*.

```
COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND(punk, clsid)
```

### <a name="parameters"></a>Parametry

*Punk*<br/>
[w] Nazwa wskaźnika. `IUnknown` Musi być członkiem klasy zawierającej mapę COM.

*Clsid*<br/>
[w] Identyfikator agregacji, który zostanie utworzony, jeśli *punk* jest NULL.

### <a name="remarks"></a>Uwagi

Jeśli kwerenda interfejsu nie powiedzie się, przetwarzanie mapy COM jest kontynuowane.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#115](../../atl/codesnippet/cpp/com-map-macros_7.h)]

## <a name="com_interface_entry_break"></a><a name="com_interface_entry_break"></a>COM_INTERFACE_ENTRY_BREAK

Powoduje, że program do [wywołania DebugBreak,](/windows/win32/api/debugapi/nf-debugapi-debugbreak) gdy określony interfejs jest poszukiwany.

```
COM_INTERFACE_ENTRY_BREAK(x)
```

### <a name="parameters"></a>Parametry

*X*<br/>
[w] Tekst używany do konstruowania identyfikatora interfejsu.

### <a name="remarks"></a>Uwagi

Identyfikator interfejsu zostanie skonstruowany przez dołączenie `IID_` *x* do . Na przykład, *x* jeśli `IPersistStorage`x jest , `IID_IPersistStorage`identyfikator będzie .

## <a name="com_interface_entry_cached_tear_off"></a><a name="com_interface_entry_cached_tear_off"></a>COM_INTERFACE_ENTRY_CACHED_TEAR_OFF

Zapisuje dane specyficzne dla interfejsu dla każdego wystąpienia.

```
COM_INTERFACE_ENTRY_CACHED_TEAR_OFF(iid, x, punk)
```

### <a name="parameters"></a>Parametry

*Iid*<br/>
[w] Identyfikator GUID interfejsu odrywu.

*X*<br/>
[w] Nazwa klasy implementującej interfejs.

*Punk*<br/>
[w] Nazwa wskaźnika. `IUnknown` Musi być członkiem klasy zawierającej mapę COM. Powinien zostać zainicjowany do wartości NULL w konstruktorze obiektu klasy.

### <a name="remarks"></a>Uwagi

Jeśli interfejs nie jest używany, zmniejsza ogólny rozmiar wystąpienia obiektu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#54](../../atl/codesnippet/cpp/com-map-macros_8.h)]

## <a name="com_interface_entry_tear_off"></a><a name="com_interface_entry_tear_off"></a>COM_INTERFACE_ENTRY_TEAR_OFF

Udostępnia oderwane interfejsy.

```
COM_INTERFACE_ENTRY_TEAR_OFF(iid, x)
```

### <a name="parameters"></a>Parametry

*Iid*<br/>
[w] Identyfikator GUID interfejsu odrywu.

*X*<br/>
[w] Nazwa klasy implementującej interfejs.

### <a name="remarks"></a>Uwagi

Interfejs odrywa jest implementowany jako oddzielny obiekt, który jest tworzone za każdym razem, gdy interfejs, który reprezentuje jest poszukiwany. Zazwyczaj tworzenie interfejsu jako oderwania, jeśli interfejs jest rzadko używany, ponieważ zapisuje wskaźnik vtable w każdym wystąpieniu obiektu głównego. Odrywać jest usuwany, gdy jego liczba odwołań staje się zero. Klasa implementująca odryw powinien pochodzić z `CComTearOffObjectBase` i mieć własną mapę COM.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#1](../../atl/codesnippet/cpp/com-map-macros_1.h)]

## <a name="com_interface_entry_chain"></a><a name="com_interface_entry_chain"></a>COM_INTERFACE_ENTRY_CHAIN

Przetwarza mapę COM klasy podstawowej, gdy przetwarzanie osiągnie ten wpis na mapie COM.

```
COM_INTERFACE_ENTRY_CHAIN(classname)
```

### <a name="parameters"></a>Parametry

*Classname*<br/>
[w] Klasa podstawowa bieżącego obiektu.

### <a name="remarks"></a>Uwagi

Na przykład w poniższym kodzie:

[!code-cpp[NVC_ATL_Windowing#116](../../atl/codesnippet/cpp/com-map-macros_9.h)]

Należy zauważyć, że pierwszy wpis na mapie COM musi być interfejsem na obiekcie zawierającym mapę COM. W związku z tym nie można uruchomić wpisów mapy COM z COM_INTERFACE_ENTRY_CHAIN, co powoduje, że mapa COM innego obiektu ma być przeszukiwana w miejscu, w którym **COM_INTERFACE_ENTRY_CHAIN(**`COtherObject`**)** pojawia się na mapie COM obiektu. Jeśli chcesz najpierw przeszukać mapę COM innego obiektu, `IUnknown` dodaj wpis interfejsu do mapy COM, a następnie posiekaj mapę COM innego obiektu. Przykład:

[!code-cpp[NVC_ATL_Windowing#111](../../atl/codesnippet/cpp/com-map-macros_10.h)]

## <a name="com_interface_entry_func"></a><a name="com_interface_entry_func"></a>COM_INTERFACE_ENTRY_FUNC

Ogólny mechanizm podłączania do `QueryInterface` logiki ATL.

```
COM_INTERFACE_ENTRY_FUNC(iid, dw, func)
```

### <a name="parameters"></a>Parametry

*Iid*<br/>
[w] Identyfikator GUID interfejsu narażony.

*Dw*<br/>
[w] Parametr przeszedł do *func*.

*func*<br/>
[w] Wskaźnik funkcji, który zwróci *identyfikator*.

### <a name="remarks"></a>Uwagi

Jeśli *identyfikator* jest zgodny z identyfikatorem interfejsu, dla których jest wyszukiwany, wywoływana jest funkcja określona przez *func.* Deklaracja dla funkcji powinna być:

`HRESULT WINAPI func(void* pv, REFIID riid, LPVOID* ppv, DWORD_PTR dw);`

Gdy funkcja jest `pv` wywoływana, wskazuje obiekt klasy. Parametr *riid* odnosi się do interfejsu, `ppv` o który pytany jest, jest wskaźnikiem do lokalizacji, w której funkcja powinna przechowywać wskaźnik do interfejsu, a *dw* jest parametrem określonym we wpisie. Funkcja powinna \* `ppv` być ustawiona na NULL i zwrócić E_NOINTERFACE lub S_FALSE, jeśli nie zdecyduje się na zwrócenie interfejsu. Z E_NOINTERFACE przetwarzanie map COM kończy się. Z S_FALSE przetwarzanie mapy COM jest kontynuowane, mimo że nie zwrócono żadnego wskaźnika interfejsu. Jeśli funkcja zwraca wskaźnik interfejsu, należy zwrócić S_OK.

## <a name="com_interface_entry_func_blind"></a><a name="com_interface_entry_func_blind"></a>COM_INTERFACE_ENTRY_FUNC_BLIND

Tak samo jak [COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func), z tą różnicą, że wykonywanie zapytań o dowolny identyfikator powoduje wywołanie *func*.

```
COM_INTERFACE_ENTRY_FUNC_BLIND(dw, func)
```

### <a name="parameters"></a>Parametry

*Dw*<br/>
[w] Parametr przeszedł do *func*.

*func*<br/>
[w] Funkcja, która zostanie wywołana podczas przetwarzania tego wpisu na mapie COM.

### <a name="remarks"></a>Uwagi

Każda awaria spowoduje kontynuowanie przetwarzania na mapie COM. Jeśli funkcja zwraca wskaźnik interfejsu, należy zwrócić S_OK.

## <a name="com_interface_entry_nointerface"></a><a name="com_interface_entry_nointerface"></a>COM_INTERFACE_ENTRY_NOINTERFACE

Zwraca E_NOINTERFACE i kończy przetwarzanie map COM, gdy określony interfejs jest poszukiwany.

```
COM_INTERFACE_ENTRY_NOINTERFACE(x)
```

### <a name="parameters"></a>Parametry

*X*<br/>
[w] Tekst używany do konstruowania identyfikatora interfejsu.

### <a name="remarks"></a>Uwagi

To makro służy do zapobiegania interfejs jest używany w określonym przypadku. Na przykład można wstawić to makro do mapy COM tuż przed COM_INTERFACE_ENTRY_AGGREGATE_BLIND, aby zapobiec przekazywaniu zapytania interfejsu do wewnętrznej nieznanej agregacji.

Identyfikator interfejsu zostanie skonstruowany przez dołączenie `IID_` *x* do . Na przykład, *x* jeśli `IPersistStorage`x jest , `IID_IPersistStorage`identyfikator będzie .
