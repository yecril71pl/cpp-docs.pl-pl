---
title: Makra wejść interfejsu COM | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/28/2017
ms.technology:
- cpp-atl
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
dev_langs:
- C++
helpviewer_keywords:
- COM interfaces, COM interface entry macros
ms.assetid: 19dcb768-2e1f-4b8d-a618-453a01a4bd00
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fa3f3356cf3fdddeeb4245986549fa1bd2e12ae7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46085228"
---
# <a name="cominterfaceentry-macros"></a>Com_interface_entry — makra  

Te makra wejść interfejsy obiektu w jego mapy interfejsu COM tak, aby może zostać oceniony przez `QueryInterface`. Kolejność wpisy mapy interfejsu COM jest interfejsów kolejność będzie sprawdzana dopasowania identyfikatora IID podczas `QueryInterface`.  

|||
|-|-|
|[COM_INTERFACE_ENTRY —](#com_interface_entry)|Wprowadza interfejsów w mapie interfejsu COM.|
|[COM_INTERFACE_ENTRY2](#com_interface_entry2)|Użyj tego makra do odróżniania dwóch gałęzi dziedziczenia.|
|[COM_INTERFACE_ENTRY_IID](#com_interface_entry_iid)|Użyj tego makra wejść interfejsu w mapie com. i określić jego identyfikatora IID.|
|[COM_INTERFACE_ENTRY2_IID](#com_interface_entry2_iid)|Taki sam jak [COM_INTERFACE_ENTRY2](#com_interface_entry2), z wyjątkiem można określić różne IID.|
|[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)|Gdy interfejs identyfikowane przez *iid* zostaje przesłane zapytanie, `COM_INTERFACE_ENTRY_AGGREGATE` przekazuje do `punk`.|
|[COM_INTERFACE_ENTRY_AGGREGATE_BLIND](#com_interface_entry_aggregate_blind)|Taki sam jak [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), z tą różnicą, że wykonywanie zapytań dotyczących dowolnej IID skutkuje przekazywania zapytanie, aby *punk*.|
|[COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate)|Taki sam jak [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), chyba że *punk* ma wartość NULL, automatycznie tworzy agregacji opisanego przez *clsid*.|
|[COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND](#com_interface_entry_autoaggregate_blind)|Taki sam jak [COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate), z tą różnicą, że wykonywanie zapytań dotyczących dowolnej IID skutkuje przekazywania zapytanie, aby *punk*i jeśli *punk* ma wartość NULL, automatycznie tworząc Agregacja opisanego przez *clsid*.|
|[COM_INTERFACE_ENTRY_BREAK](#com_interface_entry_break)|Powoduje, że program do wywołania [DebugBreak](https://msdn.microsoft.com/library/windows/desktop/ms679297) podczas określonego interfejsu zostaje przesłane zapytanie.|
|[COM_INTERFACE_ENTRY_CACHED_TEAR_OFF](#com_interface_entry_cached_tear_off)|Zapisuje dane specyficzne dla interfejsu dla każdego wystąpienia.|
|[COM_INTERFACE_ENTRY_TEAR_OFF](#com_interface_entry_tear_off)|Udostępnia interfejsy odrywania.|
|[COM_INTERFACE_ENTRY_CHAIN](#com_interface_entry_chain)|Przetwarza mapę COM klasy bazowej, gdy przetwarzanie osiągnie ten wpis w mapie com.|
|[COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func)|Ogólny mechanizm przechwytywanie do ATL `QueryInterface` logiki.|
|[COM_INTERFACE_ENTRY_FUNC_BLIND](#com_interface_entry_func_blind)|Taki sam jak [COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func), z tą różnicą, że wykonywanie zapytań dotyczących dowolnej IID powoduje wywołanie *func*.|
|[COM_INTERFACE_ENTRY_NOINTERFACE](#com_interface_entry_nointerface)|Zwraca E_NOINTERFACE i kończy się COM mapy przetwarzania, gdy zostaje przesłane zapytanie określonego interfejsu.|  

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

## <a name="com_interface_entry"></a> COM_INTERFACE_ENTRY —

Wprowadza interfejsów w mapie interfejsu COM.

### <a name="syntax"></a>Składnia

```
COM_INTERFACE_ENTRY( x )
```
### <a name="parameters"></a>Parametry

*x*<br/>
[in] Nazwa interfejsu, obiekt klasy pochodzi od klasy bezpośrednio.

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

##  <a name="com_interface_entry2"></a>  COM_INTERFACE_ENTRY2

Użyj tego makra do odróżniania dwóch gałęzi dziedziczenia.

```
COM_INTERFACE_ENTRY2(x, x2)
```

### <a name="parameters"></a>Parametry

*x*<br/>
[in] Nazwa interfejsu, który ma zostać uwidoczniona z obiektu.

*x2*<br/>
[in] Nazwa gałęzi dziedziczenia, z którego *x* jest widoczna.

### <a name="remarks"></a>Uwagi

Na przykład, jeśli pochodzi obiekt klasy z dwóch dwa interfejsy, należy udostępnić `IDispatch` przy użyciu COM_INTERFACE_ENTRY2 od `IDispatch` mogą pochodzić z jednego z interfejsów.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#118](../../atl/codesnippet/cpp/com-map-macros_2.h)]

##  <a name="com_interface_entry_iid"></a>  COM_INTERFACE_ENTRY_IID

Użyj tego makra wejść interfejsu w mapie com. i określić jego identyfikatora IID.

```
COM_INTERFACE_ENTRY_IID(iid, x)
```

### <a name="parameters"></a>Parametry

*IID*<br/>
[in] Identyfikator GUID interfejsu widoczne.

*x*<br/>
[in] Nazwa klasy, w których vtable zostaną ujawnione jako interfejs identyfikowane przez *iid*.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#117](../../atl/codesnippet/cpp/com-map-macros_3.h)]

##  <a name="com_interface_entry2_iid"></a>  COM_INTERFACE_ENTRY2_IID

Taki sam jak [COM_INTERFACE_ENTRY2](#com_interface_entry2), z wyjątkiem można określić różne IID.

```
COM_INTERFACE_ENTRY2_IID(iid, x, x2)
```

### <a name="parameters"></a>Parametry

*IID*<br/>
[in] Identyfikator GUID, którą określasz interfejsu.

*x*<br/>
[in] Nazwa interfejsu, który pochodzi bezpośrednio z obiektu klasy.

*x2*<br/>
[in] Nazwa drugiego interfejsu, który pochodzi bezpośrednio z obiektu klasy.

##  <a name="com_interface_entry_aggregate"></a>  COM_INTERFACE_ENTRY_AGGREGATE

Gdy interfejs identyfikowane przez *iid* zostaje przesłane zapytanie do COM_INTERFACE_ENTRY_AGGREGATE przekazuje do *punk*.

```
COM_INTERFACE_ENTRY_AGGREGATE(iid, punk)
```

### <a name="parameters"></a>Parametry

*IID*<br/>
[in] Identyfikator GUID interfejsu kwerenda.

*punk*<br/>
[in] Nazwa `IUnknown` wskaźnika.

### <a name="remarks"></a>Uwagi

*Punk* parametru zakłada, że aby wskazywała wewnętrzny nieznanych agregacji lub wartość NULL, w którym to przypadku wpis zostanie zignorowany. Zazwyczaj będzie `CoCreate` agregacji w `FinalConstruct`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#112](../../atl/codesnippet/cpp/com-map-macros_4.h)]

##  <a name="com_interface_entry_aggregate_blind"></a>  COM_INTERFACE_ENTRY_AGGREGATE_BLIND

Taki sam jak [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), z tą różnicą, że wykonywanie zapytań dotyczących dowolnej IID skutkuje przekazywania zapytanie, aby *punk*.

```
COM_INTERFACE_ENTRY_AGGREGATE_BLIND(punk)
```

### <a name="parameters"></a>Parametry

*punk*<br/>
[in] Nazwa `IUnknown` wskaźnika.

### <a name="remarks"></a>Uwagi

Jeśli zapytanie interfejsu nie powiedzie się, przetwarzanie mapy interfejsu COM jest kontynuowane.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#113](../../atl/codesnippet/cpp/com-map-macros_5.h)]

##  <a name="com_interface_entry_autoaggregate"></a>  COM_INTERFACE_ENTRY_AUTOAGGREGATE

Taki sam jak [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), chyba że *punk* ma wartość NULL, automatycznie tworzy agregacji opisanego przez *clsid*.

```
COM_INTERFACE_ENTRY_AUTOAGGREGATE(iid, punk, clsid)
```

### <a name="parameters"></a>Parametry

*IID*<br/>
[in] Identyfikator GUID interfejsu kwerenda.

*punk*<br/>
[in] Nazwa `IUnknown` wskaźnika. Musi należeć do klasy zawierającej mapy interfejsu COM.

*Identyfikator klasy*<br/>
[in] Identyfikator agregacji, która zostanie utworzona, jeśli *punk* ma wartość NULL.

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#114](../../atl/codesnippet/cpp/com-map-macros_6.h)]

##  <a name="com_interface_entry_autoaggregate_blind"></a>  COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND

Taki sam jak [COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate), z tą różnicą, że wykonywanie zapytań dotyczących dowolnej IID skutkuje przekazywania zapytanie, aby *punk*i jeśli *punk* ma wartość NULL, automatycznie tworząc Agregacja opisanego przez *clsid*.

```
COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND(punk, clsid)
```

### <a name="parameters"></a>Parametry

*punk*<br/>
[in] Nazwa `IUnknown` wskaźnika. Musi należeć do klasy zawierającej mapy interfejsu COM.

*Identyfikator klasy*<br/>
[in] Identyfikator agregacji, która zostanie utworzona, jeśli *punk* ma wartość NULL.

### <a name="remarks"></a>Uwagi

Jeśli zapytanie interfejsu nie powiedzie się, przetwarzanie mapy interfejsu COM jest kontynuowane.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#115](../../atl/codesnippet/cpp/com-map-macros_7.h)]

##  <a name="com_interface_entry_break"></a>  COM_INTERFACE_ENTRY_BREAK

Powoduje, że program do wywołania [DebugBreak](https://msdn.microsoft.com/library/windows/desktop/ms679297) podczas określonego interfejsu zostaje przesłane zapytanie.

```
COM_INTERFACE_ENTRY_BREAK(x)
```

### <a name="parameters"></a>Parametry

*x*<br/>
[in] Tekst używany do utworzenia identyfikatora interfejsu.

### <a name="remarks"></a>Uwagi

Interfejsu IID, zostanie wykonane przez dołączenie *x* do `IID_`. Na przykład jeśli *x* jest `IPersistStorage`, będzie identyfikatora IID `IID_IPersistStorage`.

##  <a name="com_interface_entry_cached_tear_off"></a>  COM_INTERFACE_ENTRY_CACHED_TEAR_OFF

Zapisuje dane specyficzne dla interfejsu dla każdego wystąpienia.

```
COM_INTERFACE_ENTRY_CACHED_TEAR_OFF(iid, x, punk)
```

### <a name="parameters"></a>Parametry

*IID*<br/>
[in] Identyfikator GUID interfejs odrywania.

*x*<br/>
[in] Nazwa klasy implementującej interfejs.

*punk*<br/>
[in] Nazwa `IUnknown` wskaźnika. Musi należeć do klasy zawierającej mapy interfejsu COM. Powinna zostać zainicjowana na wartość NULL w Konstruktorze obiektu klasy.

### <a name="remarks"></a>Uwagi

Jeśli interfejs nie jest używany, to zmniejsza całkowity rozmiar wystąpienia obiektu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#54](../../atl/codesnippet/cpp/com-map-macros_8.h)]

##  <a name="com_interface_entry_tear_off"></a>  COM_INTERFACE_ENTRY_TEAR_OFF

Udostępnia interfejsy odrywania.

```
COM_INTERFACE_ENTRY_TEAR_OFF(iid, x)
```

### <a name="parameters"></a>Parametry

*IID*<br/>
[in] Identyfikator GUID interfejs odrywania.

*x*<br/>
[in] Nazwa klasy implementującej interfejs.

### <a name="remarks"></a>Uwagi

Interfejs odrywania jest implementowany jako oddzielny obiekt, który zostanie uruchomiony za każdym razem, gdy interfejs reprezentuje zostaje przesłane zapytanie. Zwykle tworzysz interfejsu jako odrywania Jeśli interfejs jest rzadko używana, ponieważ ta zapisuje wskaźnik vtable w każdym wystąpieniu obiektu głównego. Odrywania jest usuwany po jego licznik odwołań staje się zerem. Klasa Implementowanie odrywania powinny pochodzić z `CComTearOffObjectBase` i ma swój własny mapy interfejsu COM.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#1](../../atl/codesnippet/cpp/com-map-macros_1.h)]

##  <a name="com_interface_entry_chain"></a>  COM_INTERFACE_ENTRY_CHAIN

Przetwarza mapę COM klasy bazowej, gdy przetwarzanie osiągnie ten wpis w mapie com.

```
COM_INTERFACE_ENTRY_CHAIN(classname)
```

### <a name="parameters"></a>Parametry

*ClassName*<br/>
[in] Klasa bazowa bieżącego obiektu.

### <a name="remarks"></a>Uwagi

Na przykład w poniższym kodzie:

[!code-cpp[NVC_ATL_Windowing#116](../../atl/codesnippet/cpp/com-map-macros_9.h)]

Należy pamiętać, że pierwszy wpis mapy interfejsu COM musi być interfejsem w obiekcie, zawierająca mapy interfejsu COM. W związku z tym, nie można uruchomić wpisy mapy modelu COM z COM_INTERFACE_ENTRY_CHAIN, co powoduje, że mapa COM innego obiektu do wyszukania w punkcie, w którym **COM_INTERFACE_ENTRY_CHAIN (**`COtherObject`**)** pojawia się w mapie com. obiektu. Jeśli chcesz najpierw wyszukać mapy COM innego obiektu, Dodaj wpis interfejsu dla `IUnknown` do mapy COM następnie połączyć w łańcuch mapy interfejsu COM innego obiektu. Na przykład:

[!code-cpp[NVC_ATL_Windowing#111](../../atl/codesnippet/cpp/com-map-macros_10.h)]

##  <a name="com_interface_entry_func"></a>  COM_INTERFACE_ENTRY_FUNC

Ogólny mechanizm przechwytywanie do ATL `QueryInterface` logiki.

```
COM_INTERFACE_ENTRY_FUNC(iid, dw, func)
```

### <a name="parameters"></a>Parametry

*IID*<br/>
[in] Identyfikator GUID interfejsu widoczne.

*Magazyn danych*<br/>
[in] Parametr przekazywany za pośrednictwem do *func*.

*FUNC*<br/>
[in] Wskaźnik funkcji, która zwróci *iid*.

### <a name="remarks"></a>Uwagi

Jeśli *iid* pasuje do identyfikatora IID interfejsu przesłane zapytanie, a następnie funkcji określonej przez *func* jest wywoływana. Deklaracja funkcji powinny być następujące:

`HRESULT WINAPI func(void* pv, REFIID riid, LPVOID* ppv, DWORD_PTR dw);`

Po wywołaniu funkcji `pv` wskazuje na obiekt klasy. *Riid* parametr odnosi się do interfejsu, którego dotyczy kwerenda, `ppv` jest wskaźnikiem do lokalizacji, w której funkcja powinna przechowywać wskaźnik do interfejsu, a *dw* jest parametrem możesz określony we wpisie. Funkcja powinna być ustawiona \* `ppv` o wartości NULL i zwracana E_NOINTERFACE lub S_FALSE, jeśli go nie zwracają interfejs. Za pomocą E_NOINTERFACE kończy przetwarzanie mapy COM. Za pomocą S_FALSE przetwarzanie mapy COM będzie nadal występował, mimo że zwrócony wskaźnik nie interfejsu. Jeśli funkcja zwraca wskaźnik interfejsu, powinna zwrócić S_OK.

##  <a name="com_interface_entry_func_blind"></a>  COM_INTERFACE_ENTRY_FUNC_BLIND

Taki sam jak [COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func), z tą różnicą, że wykonywanie zapytań dotyczących dowolnej IID powoduje wywołanie *func*.

```
COM_INTERFACE_ENTRY_FUNC_BLIND(dw, func)
```

### <a name="parameters"></a>Parametry

*Magazyn danych*<br/>
[in] Parametr przekazywany za pośrednictwem do *func*.

*FUNC*<br/>
[in] Funkcja, która jest wywoływana podczas przetwarzania tego wpisu w mapie com.

### <a name="remarks"></a>Uwagi

Jakiekolwiek niepowodzenie spowoduje, że przetwarzanie na kontynuowanie na mapie com. Jeśli funkcja zwraca wskaźnik interfejsu, powinna zwrócić S_OK.

##  <a name="com_interface_entry_nointerface"></a>  COM_INTERFACE_ENTRY_NOINTERFACE

Zwraca E_NOINTERFACE i kończy się COM mapy przetwarzania, gdy zostaje przesłane zapytanie określonego interfejsu.

```
COM_INTERFACE_ENTRY_NOINTERFACE(x)
```

### <a name="parameters"></a>Parametry

*x*<br/>
[in] Tekst używany do utworzenia identyfikatora interfejsu.

### <a name="remarks"></a>Uwagi

Aby zapobiec używany w przypadku określonego interfejsu, można użyć tego makra. Na przykład można wstawić tego makra do mapy COM bezpośrednio poprzedzający COM_INTERFACE_ENTRY_AGGREGATE_BLIND, aby uniemożliwić przekazywane do agregacji wewnętrzny nieznany zapytania dla interfejsu.

Interfejsu IID, zostanie wykonane przez dołączenie *x* do `IID_`. Na przykład jeśli *x* jest `IPersistStorage`, będzie identyfikatora IID `IID_IPersistStorage`.

  