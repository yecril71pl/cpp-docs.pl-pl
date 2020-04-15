---
title: Mapy połączeń
ms.date: 11/04/2016
helpviewer_keywords:
- connection maps
ms.assetid: 1f25a9bc-6d09-4614-99cf-dc38e8ddfa73
ms.openlocfilehash: 947cd09023ef4028a32db8e2e4e8b33f7e04e0dd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374800"
---
# <a name="connection-maps"></a>Mapy połączeń

Kontrolki OLE są w stanie udostępnić interfejsy innym aplikacjom. Te interfejsy zezwalają tylko na dostęp z kontenera do tego formantu. Jeśli formant OLE chce uzyskać dostęp do zewnętrznych interfejsów innych obiektów OLE, należy ustanowić punkt połączenia. Ten punkt połączenia umożliwia kontrolę wychodzącego dostępu do zewnętrznych map wysyłki, takich jak mapy zdarzeń lub funkcje powiadomień.

Biblioteka klas programu Microsoft Foundation oferuje model programowania obsługujący punkty połączenia. W tym modelu "mapy połączeń" są używane do wyznaczania interfejsów lub punktów połączenia dla formantu OLE. Mapy połączeń zawierają jedno makro dla każdego punktu połączenia. Aby uzyskać więcej informacji na temat map połączeń, zobacz [CConnectionPoint](../../mfc/reference/cconnectionpoint-class.md) klasy.

Zazwyczaj formant będzie obsługiwać tylko dwa punkty połączenia: jeden dla zdarzeń i jeden dla powiadomień właściwości. Są one implementowane `COleControl` przez klasę podstawową i nie wymagają dodatkowej pracy przez moduł zapisujący formant. Wszelkie dodatkowe punkty połączenia, które chcesz zaimplementować w klasie, należy dodać ręcznie. Aby obsługiwać mapy połączeń i punkty, MFC udostępnia następujące makra:

### <a name="connection-map-declaration-and-demarcation"></a>Deklaracja mapy połączeń i rozgraniczenie

|||
|-|-|
|[BEGIN_CONNECTION_PART](#begin_connection_part)|Deklaruje klasę osadzoną, która implementuje dodatkowy punkt połączenia (musi być używany w deklaracji klasy).|
|[END_CONNECTION_PART](#end_connection_part)|Kończy deklarację punktu połączenia (musi być używany w deklaracji klasy).|
|[CONNECTION_IID](#connection_iid)|Określa identyfikator interfejsu punktu połączenia formantu.|
|[DECLARE_CONNECTION_MAP](#declare_connection_map)|Deklaruje, że mapa połączenia będzie używana w klasie (musi być używana w deklaracji klasy).|
|[BEGIN_CONNECTION_MAP](#begin_connection_map)|Rozpoczyna definicję mapy połączenia (musi być używany w implementacji klasy).|
|[END_CONNECTION_MAP](#end_connection_map)|Kończy definicję mapy połączeń (musi być używana w implementacji klasy).|
|[CONNECTION_PART](#connection_part)|Określa punkt połączenia na mapie połączenia formantu.|

Następujące funkcje pomagają zlewowi w ustanawianiu i odłączaniu połączenia przy użyciu przyłączy:

### <a name="initializationtermination-of-connection-points"></a>Inicjowanie/zakończenie punktów połączenia

|||
|-|-|
|[AfxConnectionAdvise](#afxconnectionadvise)|Ustanawia połączenie między źródłem a ujściem.|
|[AfxConnectionUnadvise](#afxconnectionunadvise)|Przerywa połączenie między źródłem a zlewem.|

## <a name="begin_connection_part"></a><a name="begin_connection_part"></a>BEGIN_CONNECTION_PART

Użyj makra BEGIN_CONNECTION_PART, aby rozpocząć definicję dodatkowych punktów połączenia poza punktami połączenia zdarzenia i powiadomień właściwości.

```
BEGIN_CONNECTION_PART(theClass, localClass)
```

### <a name="parameters"></a>Parametry

*klasa*<br/>
Określa nazwę klasy kontrolnej, której punkt połączenia jest taki.

*localClass (Klasa lokalna)*<br/>
Określa nazwę klasy lokalnej, która implementuje punkt połączenia.

### <a name="remarks"></a>Uwagi

W pliku deklaracji (.h), który definiuje funkcje członkowskie dla klasy, uruchom punkt połączenia z makra BEGIN_CONNECTION_PART, a następnie dodaj makro CONNECTION_IID i inne funkcje członkowskie, które chcesz zaimplementować, i wypełnij mapę punktu połączenia za pomocą makra END_CONNECTION_PART.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdisp.h

## <a name="end_connection_part"></a><a name="end_connection_part"></a>END_CONNECTION_PART

Kończy deklarację punktu połączenia.

```
END_CONNECTION_PART(localClass)
```

### <a name="parameters"></a>Parametry

*localClass (Klasa lokalna)*<br/>
Określa nazwę klasy lokalnej, która implementuje punkt połączenia.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdisp.h

## <a name="connection_iid"></a><a name="connection_iid"></a>CONNECTION_IID

Użyj między makrami BEGIN_CONNECTION_PART i END_CONNECTION_PART, aby zdefiniować identyfikator interfejsu dla punktu połączenia obsługiwanego przez kontrolkę OLE.

```
CONNECTION_IID(iid)
```

### <a name="parameters"></a>Parametry

*Iid*<br/>
Identyfikator interfejsu interfejsu wywoływanego przez punkt połączenia.

### <a name="remarks"></a>Uwagi

Argument *iid* jest identyfikatorem interfejsu używanym do identyfikowania interfejsu, który punkt połączenia wywoła na połączonych zlewozmywakach. Przykład:

[!code-cpp[NVC_MFCConnectionPoints#10](../../mfc/codesnippet/cpp/connection-maps_1.h)]

określa punkt połączenia, który `ISinkInterface` wywołuje interfejs.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdisp.h

## <a name="declare_connection_map"></a><a name="declare_connection_map"></a>DECLARE_CONNECTION_MAP

Każda `COleControl`klasa pochodna w programie może zapewnić mapę połączenia, aby określić dodatkowe punkty połączenia, które obsługuje formant.

```
DECLARE_CONNECTION_MAP()
```

### <a name="remarks"></a>Uwagi

Jeśli formant obsługuje dodatkowe punkty, należy użyć makra DECLARE_CONNECTION_MAP na końcu deklaracji klasy. Następnie w pliku .cpp, który definiuje funkcje członkowskie dla klasy, użyj makra BEGIN_CONNECTION_MAP, CONNECTION_PART makra dla każdego z punktów połączenia formantu i makra END_CONNECTION_MAP, aby zadeklarować koniec mapy połączenia.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdisp.h

## <a name="begin_connection_map"></a><a name="begin_connection_map"></a>BEGIN_CONNECTION_MAP

Każda `COleControl`klasa pochodna w programie może zapewnić mapę połączenia, aby określić punkty połączenia, które będą obsługiwane przez formant.

```
BEGIN_CONNECTION_MAP(theClass, theBase)
```

### <a name="parameters"></a>Parametry

*klasa*<br/>
Określa nazwę klasy kontrolnej, której mapa połączenia jest to.

*baza danych*<br/>
Określa nazwę klasy podstawowej *klasy klasy*.

### <a name="remarks"></a>Uwagi

W realizacji (. CPP), który definiuje funkcje członkowskie dla klasy, rozpoczyna mapę połączenia z BEGIN_CONNECTION_MAP makra, a następnie dodaje wpisy makr dla każdego z punktów połączenia za pomocą [makra CONNECTION_PART.](#connection_part) Na koniec uzupełnij mapę połączenia z [END_CONNECTION_MAP](#end_connection_map) makra.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdisp.h

## <a name="end_connection_map"></a><a name="end_connection_map"></a>END_CONNECTION_MAP

Kończy definicję mapy połączeń.

```
END_CONNECTION_MAP()
```

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdisp.h

## <a name="connection_part"></a><a name="connection_part"></a>CONNECTION_PART

Mapuje punkt połączenia dla formantu OLE na określony identyfikator interfejsu.

```
CONNECTION_PART(theClass, iid, localClass)
```

### <a name="parameters"></a>Parametry

*klasa*<br/>
Określa nazwę klasy kontrolnej, której punkt połączenia jest taki.

*Iid*<br/>
Identyfikator interfejsu interfejsu wywoływanego przez punkt połączenia.

*localClass (Klasa lokalna)*<br/>
Określa nazwę klasy lokalnej, która implementuje punkt połączenia.

### <a name="remarks"></a>Uwagi

Przykład:

[!code-cpp[NVC_MFCConnectionPoints#2](../../mfc/codesnippet/cpp/connection-maps_2.cpp)]

implementuje mapę połączenia z punktem połączenia, który wywołuje `IID_ISinkInterface` interfejs .

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdisp.h

## <a name="afxconnectionadvise"></a><a name="afxconnectionadvise"></a>AfxConnectionAdvise

Wywołanie tej funkcji, aby ustanowić połączenie między źródłem, określonym przez *pUnkSrc*, a ujściem, określonym przez *pUnkSink*.

```
BOOL AFXAPI AfxConnectionAdvise(
    LPUNKNOWN pUnkSrc,
    REFIID iid,
    LPUNKNOWN pUnkSink,
    BOOL bRefCount,
    DWORD FAR* pdwCookie);
```

### <a name="parameters"></a>Parametry

*pUnkSrc (własówce)*<br/>
Wskaźnik do obiektu, który wywołuje interfejs.

*pUnkSink (własnek)*<br/>
Wskaźnik do obiektu, który implementuje interfejs.

*Iid*<br/>
Identyfikator interfejsu połączenia.

*bLiczna liczba*<br/>
TRUE wskazuje, że utworzenie połączenia powinno spowodować przyrost liczby odwołań *pUnkSink.* FALSE wskazuje, że liczba odwołań nie powinna być zwiększana.

*pdwCookie*<br/>
Wskaźnik do DWORD, gdzie zwracany jest identyfikator połączenia. Ta wartość powinna być przekazywana jako `AfxConnectionUnadvise` parametr *dwCookie* podczas odłączania połączenia.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli połączenie zostało ustanowione; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCConnectionPoints#8](../../mfc/codesnippet/cpp/connection-maps_3.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxctl.h

## <a name="afxconnectionunadvise"></a><a name="afxconnectionunadvise"></a>AfxConnectionUnadvise

Wywołanie tej funkcji, aby odłączyć połączenie między źródłem, określone przez *pUnkSrc*, a ujściem, określone przez *pUnkSink*.

```
BOOL AFXAPI AfxConnectionUnadvise(
    LPUNKNOWN pUnkSrc,
    REFIID iid,
    LPUNKNOWN pUnkSink,
    BOOL bRefCount,
    DWORD dwCookie);
```

### <a name="parameters"></a>Parametry

*pUnkSrc (własówce)*<br/>
Wskaźnik do obiektu, który wywołuje interfejs.

*pUnkSink (własnek)*<br/>
Wskaźnik do obiektu, który implementuje interfejs.

*Iid*<br/>
Identyfikator interfejsu punktu połączenia.

*bLiczna liczba*<br/>
WARTOŚĆ TRUE wskazuje, że odłączenie połączenia powinno spowodować zmniejszenie liczby odwołań *pUnkSink.* FALSE wskazuje, że liczba odwołań nie powinna być zmniejszana.

*dwCookie (właśc.*<br/>
Identyfikator połączenia zwrócony `AfxConnectionAdvise`przez plik .

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli połączenie zostało odłączone; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCConnectionPoints#9](../../mfc/codesnippet/cpp/connection-maps_4.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxctl.h

## <a name="see-also"></a>Zobacz też

[Makra i globals](../../mfc/reference/mfc-macros-and-globals.md)
