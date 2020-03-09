---
title: Makra wpisów interfejsu COM
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
ms.openlocfilehash: 1e1674bad1164e640939d430a860beac7a6e4208
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855669"
---
# <a name="com_interface_entry-macros"></a>Makra COM_INTERFACE_ENTRY

Te makra wprowadzają interfejsy obiektu do mapy modelu COM, aby można było uzyskać do nich dostęp `QueryInterface`. Kolejność wpisów w mapie COM jest sprawdzana pod kątem pasującego identyfikatora IID podczas `QueryInterface`.

|||
|-|-|
|[COM_INTERFACE_ENTRY](#com_interface_entry)|Wprowadza interfejsy do mapy interfejsu COM.|
|[COM_INTERFACE_ENTRY2](#com_interface_entry2)|Za pomocą tego makra można odróżnić dwa gałęzie dziedziczenia.|
|[COM_INTERFACE_ENTRY_IID](#com_interface_entry_iid)|To makro służy do wprowadzania interfejsu do mapy COM i określania identyfikatora IID.|
|[COM_INTERFACE_ENTRY2_IID](#com_interface_entry2_iid)|Analogicznie jak [COM_INTERFACE_ENTRY2](#com_interface_entry2), z wyjątkiem sytuacji, w której można określić inny identyfikator IID.|
|[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)|Gdy jest wysyłany interfejs identyfikowany przez *Identyfikator IID* , `COM_INTERFACE_ENTRY_AGGREGATE` przekazuje do `punk`.|
|[COM_INTERFACE_ENTRY_AGGREGATE_BLIND](#com_interface_entry_aggregate_blind)|Analogicznie jak [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), z tą różnicą, że zapytania dotyczące dowolnego identyfikatora IID w wyniku przesyłania zapytania do elementu *punktowego*.|
|[COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate)|Analogicznie jak [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), z wyjątkiem tego, że *punkt* ma wartość null, automatycznie tworzy agregację opisaną przez *CLSID*.|
|[COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND](#com_interface_entry_autoaggregate_blind)|Analogicznie jak [COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate), z tą różnicą, że zapytanie dla dowolnego identyfikatora IID powoduje przekazanie zapytania do elementu *punktowego*, a jeśli *punkt* jest pusty, automatyczne tworzenie agregacji opisanej przez *CLSID*.|
|[COM_INTERFACE_ENTRY_BREAK](#com_interface_entry_break)|Powoduje, że program wywoła [DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) , gdy zostanie określony interfejs.|
|[COM_INTERFACE_ENTRY_CACHED_TEAR_OFF](#com_interface_entry_cached_tear_off)|Zapisuje dane specyficzne dla interfejsu dla każdego wystąpienia.|
|[COM_INTERFACE_ENTRY_TEAR_OFF](#com_interface_entry_tear_off)|Uwidacznia interfejsy Odrywane.|
|[COM_INTERFACE_ENTRY_CHAIN](#com_interface_entry_chain)|Przetwarza mapę COM klasy bazowej, gdy przetwarzanie osiągnie ten wpis w mapie COM.|
|[COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func)|Ogólny mechanizm podłączania do logiki `QueryInterface` ATL.|
|[COM_INTERFACE_ENTRY_FUNC_BLIND](#com_interface_entry_func_blind)|Analogicznie jak [COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func), z tą różnicą, że zapytanie dla dowolnego identyfikatora IID spowoduje wywołanie funkcji *Func*.|
|[COM_INTERFACE_ENTRY_NOINTERFACE](#com_interface_entry_nointerface)|Zwraca E_NOINTERFACE i przerywa przetwarzanie mapowania modelu COM, gdy określony interfejs jest badany.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom. h

## <a name="com_interface_entry"></a>COM_INTERFACE_ENTRY

Wprowadza interfejsy do mapy interfejsu COM.

### <a name="syntax"></a>Składnia

```
COM_INTERFACE_ENTRY( x )
```

### <a name="parameters"></a>Parametry

*y*<br/>
podczas Nazwa interfejsu, bezpośrednio pochodzi od obiektu klasy.

### <a name="remarks"></a>Uwagi

Typowo, jest to najczęściej używany typ wpisu.

### <a name="example"></a>Przykład

```cpp
BEGIN_COM_MAP(CThisExample)
   COM_INTERFACE_ENTRY(IThisExample)
   COM_INTERFACE_ENTRY(IDispatch)
   COM_INTERFACE_ENTRY(ISupportErrorInfo)
END_COM_MAP()
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom. h

##  <a name="com_interface_entry2"></a>COM_INTERFACE_ENTRY2

Za pomocą tego makra można odróżnić dwa gałęzie dziedziczenia.

```
COM_INTERFACE_ENTRY2(x, x2)
```

### <a name="parameters"></a>Parametry

*y*<br/>
podczas Nazwa interfejsu, który ma być ujawniony dla obiektu.

*x2*<br/>
podczas Nazwa gałęzi dziedziczenia, z której jest uwidaczniany *x* .

### <a name="remarks"></a>Uwagi

Na przykład, jeśli pochodny jest obiekt klasy z dwóch podwójnych interfejsów, uwidaczniasz `IDispatch` przy użyciu COM_INTERFACE_ENTRY2, ponieważ `IDispatch` można uzyskać z jednego z tych interfejsów.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#118](../../atl/codesnippet/cpp/com-map-macros_2.h)]

##  <a name="com_interface_entry_iid"></a>COM_INTERFACE_ENTRY_IID

To makro służy do wprowadzania interfejsu do mapy COM i określania identyfikatora IID.

```
COM_INTERFACE_ENTRY_IID(iid, x)
```

### <a name="parameters"></a>Parametry

*IID*<br/>
podczas Identyfikator GUID interfejsu uwidocznione.

*y*<br/>
podczas Nazwa klasy, której tablicę zawierającą zostanie uwidoczniony jako interfejs identyfikowany przez *Identyfikator IID*.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#117](../../atl/codesnippet/cpp/com-map-macros_3.h)]

##  <a name="com_interface_entry2_iid"></a>COM_INTERFACE_ENTRY2_IID

Analogicznie jak [COM_INTERFACE_ENTRY2](#com_interface_entry2), z wyjątkiem sytuacji, w której można określić inny identyfikator IID.

```
COM_INTERFACE_ENTRY2_IID(iid, x, x2)
```

### <a name="parameters"></a>Parametry

*IID*<br/>
podczas Identyfikator GUID, który jest określany dla interfejsu.

*y*<br/>
podczas Nazwa interfejsu, bezpośrednio pochodzący od obiektu klasy.

*x2*<br/>
podczas Nazwa drugiego interfejsu, bezpośrednio pochodzący od obiektu klasy.

##  <a name="com_interface_entry_aggregate"></a>COM_INTERFACE_ENTRY_AGGREGATE

Gdy do interfejsu identyfikowanego za pomocą *identyfikatora IID* jest wysyłana kwerenda, COM_INTERFACE_ENTRY_AGGREGATE dalej do elementu *punktowego*.

```
COM_INTERFACE_ENTRY_AGGREGATE(iid, punk)
```

### <a name="parameters"></a>Parametry

*IID*<br/>
podczas Identyfikator GUID interfejsu, dla którego wykonano zapytanie.

*punkt*<br/>
podczas Nazwa `IUnknown`ego wskaźnika.

### <a name="remarks"></a>Uwagi

Przyjęto, że parametr *punktowy* wskazuje na wewnętrzny nieznany element zagregowany lub wartość null, w takim przypadku wpis jest ignorowany. Zwykle `CoCreate` wartość zagregowana w `FinalConstruct`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#112](../../atl/codesnippet/cpp/com-map-macros_4.h)]

##  <a name="com_interface_entry_aggregate_blind"></a>COM_INTERFACE_ENTRY_AGGREGATE_BLIND

Analogicznie jak [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), z tą różnicą, że zapytania dotyczące dowolnego identyfikatora IID w wyniku przesyłania zapytania do elementu *punktowego*.

```
COM_INTERFACE_ENTRY_AGGREGATE_BLIND(punk)
```

### <a name="parameters"></a>Parametry

*punkt*<br/>
podczas Nazwa `IUnknown`ego wskaźnika.

### <a name="remarks"></a>Uwagi

Jeśli zapytanie interfejsu zakończy się niepowodzeniem, przetwarzanie mapy COM jest kontynuowane.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#113](../../atl/codesnippet/cpp/com-map-macros_5.h)]

##  <a name="com_interface_entry_autoaggregate"></a>COM_INTERFACE_ENTRY_AUTOAGGREGATE

Analogicznie jak [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), z wyjątkiem tego, że *punkt* ma wartość null, automatycznie tworzy agregację opisaną przez *CLSID*.

```
COM_INTERFACE_ENTRY_AUTOAGGREGATE(iid, punk, clsid)
```

### <a name="parameters"></a>Parametry

*IID*<br/>
podczas Identyfikator GUID interfejsu, dla którego wykonano zapytanie.

*punkt*<br/>
podczas Nazwa `IUnknown`ego wskaźnika. Musi być członkiem klasy zawierającej mapę COM.

*Identyfikator*<br/>
podczas Identyfikator agregacji, która zostanie utworzona, jeśli *punkt* wartościowy ma wartość null.

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#114](../../atl/codesnippet/cpp/com-map-macros_6.h)]

##  <a name="com_interface_entry_autoaggregate_blind"></a>COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND

Analogicznie jak [COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate), z tą różnicą, że zapytanie dla dowolnego identyfikatora IID powoduje przekazanie zapytania do elementu *punktowego*, a jeśli *punkt* jest pusty, automatyczne tworzenie agregacji opisanej przez *CLSID*.

```
COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND(punk, clsid)
```

### <a name="parameters"></a>Parametry

*punkt*<br/>
podczas Nazwa `IUnknown`ego wskaźnika. Musi być członkiem klasy zawierającej mapę COM.

*Identyfikator*<br/>
podczas Identyfikator agregacji, która zostanie utworzona, jeśli *punkt* wartościowy ma wartość null.

### <a name="remarks"></a>Uwagi

Jeśli zapytanie interfejsu zakończy się niepowodzeniem, przetwarzanie mapy COM jest kontynuowane.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#115](../../atl/codesnippet/cpp/com-map-macros_7.h)]

##  <a name="com_interface_entry_break"></a>COM_INTERFACE_ENTRY_BREAK

Powoduje, że program wywoła [DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) , gdy zostanie określony interfejs.

```
COM_INTERFACE_ENTRY_BREAK(x)
```

### <a name="parameters"></a>Parametry

*y*<br/>
podczas Tekst służący do konstruowania identyfikatora interfejsu.

### <a name="remarks"></a>Uwagi

Identyfikator IID interfejsu zostanie skonstruowany przez dołączenie *x* do `IID_`. Na przykład jeśli *x* jest `IPersistStorage`, identyfikator IID zostanie `IID_IPersistStorage`.

##  <a name="com_interface_entry_cached_tear_off"></a>COM_INTERFACE_ENTRY_CACHED_TEAR_OFF

Zapisuje dane specyficzne dla interfejsu dla każdego wystąpienia.

```
COM_INTERFACE_ENTRY_CACHED_TEAR_OFF(iid, x, punk)
```

### <a name="parameters"></a>Parametry

*IID*<br/>
podczas Identyfikator GUID interfejsu odnoszącego się do odrywania.

*y*<br/>
podczas Nazwa klasy implementującej interfejs.

*punkt*<br/>
podczas Nazwa `IUnknown`ego wskaźnika. Musi być członkiem klasy zawierającej mapę COM. Powinien być zainicjowany do wartości NULL w konstruktorze obiektu klasy.

### <a name="remarks"></a>Uwagi

Jeśli interfejs nie jest używany, spowoduje to zmniejszenie ogólnego rozmiaru wystąpienia obiektu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#54](../../atl/codesnippet/cpp/com-map-macros_8.h)]

##  <a name="com_interface_entry_tear_off"></a>COM_INTERFACE_ENTRY_TEAR_OFF

Uwidacznia interfejsy Odrywane.

```
COM_INTERFACE_ENTRY_TEAR_OFF(iid, x)
```

### <a name="parameters"></a>Parametry

*IID*<br/>
podczas Identyfikator GUID interfejsu odnoszącego się do odrywania.

*y*<br/>
podczas Nazwa klasy implementującej interfejs.

### <a name="remarks"></a>Uwagi

Interfejs odrywany jest implementowany jako oddzielny obiekt, który jest określany za każdym razem, gdy interfejs, który reprezentuje, jest wysyłany do zapytania. Zazwyczaj można skompilować interfejs jako odrywany, jeśli interfejs jest rzadko używany, ponieważ zapisuje wskaźnik tablic wirtualnych w każdym wystąpieniu obiektu głównego. Odrywanie jest usuwane, gdy jej liczba odwołań zmieni się na zero. Klasa implementująca rozerwanie powinna być pochodną `CComTearOffObjectBase` i mieć własną mapę COM.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#1](../../atl/codesnippet/cpp/com-map-macros_1.h)]

##  <a name="com_interface_entry_chain"></a>COM_INTERFACE_ENTRY_CHAIN

Przetwarza mapę COM klasy bazowej, gdy przetwarzanie osiągnie ten wpis w mapie COM.

```
COM_INTERFACE_ENTRY_CHAIN(classname)
```

### <a name="parameters"></a>Parametry

*nazwą*<br/>
podczas Klasa bazowa bieżącego obiektu.

### <a name="remarks"></a>Uwagi

Na przykład, w poniższym kodzie:

[!code-cpp[NVC_ATL_Windowing#116](../../atl/codesnippet/cpp/com-map-macros_9.h)]

Należy zauważyć, że pierwszy wpis w mapie COM musi być interfejsem obiektu zawierającego mapę COM. W tym celu nie można uruchomić wpisów mapy COM przy użyciu COM_INTERFACE_ENTRY_CHAIN, co spowoduje, że mapa COM innego obiektu będzie przeszukiwana w punkcie, w którym **COM_INTERFACE_ENTRY_CHAIN (** `COtherObject` **)** pojawia się na mapie com obiektu. Aby najpierw przeszukać mapę COM innego obiektu, należy dodać wpis interfejsu dla `IUnknown` do mapy modelu COM, a następnie połączyć mapę COM innego obiektu. Na przykład:

[!code-cpp[NVC_ATL_Windowing#111](../../atl/codesnippet/cpp/com-map-macros_10.h)]

##  <a name="com_interface_entry_func"></a>COM_INTERFACE_ENTRY_FUNC

Ogólny mechanizm podłączania do logiki `QueryInterface` ATL.

```
COM_INTERFACE_ENTRY_FUNC(iid, dw, func)
```

### <a name="parameters"></a>Parametry

*IID*<br/>
podczas Identyfikator GUID interfejsu uwidocznione.

*magazynu*<br/>
podczas Parametr przeszedł do funkcji *Func*.

*func*<br/>
podczas Wskaźnik funkcji, który zwróci *Identyfikator IID*.

### <a name="remarks"></a>Uwagi

Jeśli *Identyfikator IID* jest zgodny z identyfikatorem IID interfejsu, dla którego wykonano zapytanie, funkcja określona przez *Func* jest wywoływana. Deklaracja dla funkcji powinna być:

`HRESULT WINAPI func(void* pv, REFIID riid, LPVOID* ppv, DWORD_PTR dw);`

Gdy funkcja jest wywoływana, `pv` wskazuje obiekt klasy. Parametr *riid* odwołuje się do interfejsu, dla którego jest wykonywana kwerenda, `ppv` jest wskaźnikiem do lokalizacji, w której funkcja powinna przechowywać wskaźnik do interfejsu, a *DW* jest parametrem określonym we wpisie. Funkcja powinna ustawić \* `ppv` na wartość NULL i zwrócić E_NOINTERFACE lub S_FALSE, jeśli wybierze nie zwracać interfejsu. W przypadku E_NOINTERFACE przerywa przetwarzanie mapowania COM. S_FALSE, przetwarzanie mapy COM jest kontynuowane, nawet jeśli nie został zwrócony żaden wskaźnik interfejsu. Jeśli funkcja zwraca wskaźnik interfejsu, powinien zwrócić S_OK.

##  <a name="com_interface_entry_func_blind"></a>COM_INTERFACE_ENTRY_FUNC_BLIND

Analogicznie jak [COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func), z tą różnicą, że zapytanie dla dowolnego identyfikatora IID spowoduje wywołanie funkcji *Func*.

```
COM_INTERFACE_ENTRY_FUNC_BLIND(dw, func)
```

### <a name="parameters"></a>Parametry

*magazynu*<br/>
podczas Parametr przeszedł do funkcji *Func*.

*func*<br/>
podczas Funkcja, która jest wywoływana, gdy ten wpis w mapie COM jest przetwarzany.

### <a name="remarks"></a>Uwagi

Wszelkie awarie spowodują, że przetwarzanie będzie kontynuowane na mapie COM. Jeśli funkcja zwraca wskaźnik interfejsu, powinien zwrócić S_OK.

##  <a name="com_interface_entry_nointerface"></a>COM_INTERFACE_ENTRY_NOINTERFACE

Zwraca E_NOINTERFACE i przerywa przetwarzanie mapowania modelu COM, gdy określony interfejs jest badany.

```
COM_INTERFACE_ENTRY_NOINTERFACE(x)
```

### <a name="parameters"></a>Parametry

*y*<br/>
podczas Tekst służący do konstruowania identyfikatora interfejsu.

### <a name="remarks"></a>Uwagi

To makro służy do zapobiegania użyciu interfejsu w konkretnym przypadku. Na przykład możesz wstawić to makro do mapy COM bezpośrednio przed COM_INTERFACE_ENTRY_AGGREGATE_BLIND, aby zapobiec przekazywaniu zapytania dotyczącego interfejsu do nieznanego elementu wartości wewnętrznej agregacji.

Identyfikator IID interfejsu zostanie skonstruowany przez dołączenie *x* do `IID_`. Na przykład jeśli *x* jest `IPersistStorage`, identyfikator IID zostanie `IID_IPersistStorage`.
