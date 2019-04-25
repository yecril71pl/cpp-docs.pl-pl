---
title: Mapy zdarzeń
ms.date: 06/20/2018
f1_keywords:
- vc.mfc.macros.maps
helpviewer_keywords:
- event maps [MFC]
ms.assetid: 1ed53aee-bc53-43cd-834a-6fb935c0d29b
ms.openlocfilehash: 512170d7eaa891b3616ca1ea56c29a8bb5cccda9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62322244"
---
# <a name="event-maps"></a>Mapy zdarzeń

Zawsze, gdy formant chce powiadomić jej kontener, który jakąś akcję (określoną przez dewelopera kontrolek) stało się (na przykład naciśnięcie klawisza, kliknięcie myszą lub zmianę stanu formantu) wywołuje funkcję inicjowanie zdarzeń. Ta funkcja powiadomi kontenera kontrolki, która niektóre akcje, ważne jest przeprowadzana przez wyzwalanie zdarzeń powiązanych.

Biblioteki klas Microsoft Foundation udostępnia model programowania, zoptymalizowane pod kątem wyzwalanie zdarzeń. W tym modelu "mapy zdarzeń" są używane do wyznaczenia, jakie funkcje wyzwolenie zdarzenia dla określonego formantu. Mapy zdarzeń zawierają jeden makra dla każdego zdarzenia. Na przykład mapa zdarzeń, jest uruchamiana zasobu kliknij zdarzenie może wyglądać następująco:

[!code-cpp[NVC_MFCAxCtl#16](../../mfc/reference/codesnippet/cpp/event-maps_1.cpp)]

`EVENT_STOCK_CLICK` — Makro wskazuje, że formant zostanie uruchomiony zasobu kliknij zdarzenie za każdym razem, gdy wykryje myszy, kliknij przycisk. Aby uzyskać bardziej szczegółowe listę innych standardowych zdarzeń, zobacz artykuł [kontrolek ActiveX: Zdarzenia](../../mfc/mfc-activex-controls-events.md). Makra są również dostępne w celu wskazania zdarzenia niestandardowe.

Makra mapy zdarzeń są ważne, zazwyczaj nie wstawiono je bezpośrednio. Jest to spowodowane w oknie dialogowym właściwości automatycznie tworzy wpisy mapy zdarzeń w plikach źródłowych, gdy używasz do skojarzenia inicjowanie zdarzeń funkcji ze zdarzeniami. Zawsze, gdy chcesz edytować, lub Dodaj wpis mapy zdarzeń można użyć w oknie właściwości.

Aby zapewnić obsługę mapy zdarzeń, biblioteka MFC zawiera następujące makra:

## <a name="event-map-macros"></a>Makra mapy zdarzeń

### <a name="event-map-declaration-and-demarcation"></a>Zdarzenie mapy deklaracja i odgraniczenie

|||
|-|-|
|[DECLARE_EVENT_MAP](#declare_event_map)|Deklaruje, używane w klasie do mapowania zdarzeń funkcji inicjowanie zdarzeń (muszą być używane w deklaracji klasy) mapę zdarzeń.|
|[BEGIN_EVENT_MAP](#begin_event_map)|Rozpoczyna się definicji mapę zdarzeń (muszą być używane w implementacji klasy).|
|[END_EVENT_MAP](#end_event_map)|Kończy definicję mapę zdarzeń (muszą być używane w implementacji klasy).|

### <a name="event-mapping-macros"></a>Makra mapowania zdarzeń

|||
|-|-|
|[EVENT_CUSTOM](#event_custom)|Wskazuje, która funkcja inicjowanie zdarzeń nastąpi określonego zdarzenia.|
|[EVENT_CUSTOM_ID](#event_custom_id)|Wskazuje, funkcja inicjowanie zdarzeń, które będą uruchamiane określonych zdarzeń, z identyfikatorem wyznaczonym wysyłania.|

### <a name="message-mapping-macros"></a>Makra mapowania wiadomości

|||
|-|-|
|[ON_OLEVERB](#on_oleverb)|Wskazuje niestandardowy zlecenie, obsługiwane przez kontrolkę OLE.|
|[ON_STDOLEVERB](#on_stdoleverb)|Zastępuje mapowanie standardowy czasownika kontrolkę OLE.|

##  <a name="declare_event_map"></a>  DECLARE_EVENT_MAP

Każdy `COleControl`-klasy pochodnej w programie może zapewnić Mapa zdarzeń, aby określić zdarzenia kontrolki zostanie uruchomiony.

```cpp
DECLARE_EVENT_MAP()
```

### <a name="remarks"></a>Uwagi

Użyj DECLARE_EVENT_MAP — makro na końcu deklaracją klasy. Następnie w pliku .cpp, który definiuje funkcji elementów członkowskich klasy, użyj BEGIN_EVENT_MAP — makro, wpisy makra dla każdego zdarzenia obiektu Controls i END_EVENT_MAP — makro do deklarowania na końcu listy zdarzeń.

Aby uzyskać więcej informacji na temat mapy zdarzeń, zobacz artykuł [kontrolek ActiveX: Zdarzenia](../../mfc/mfc-activex-controls-events.md).

### <a name="requirements"></a>Wymagania

**Nagłówek** afxctl.h

## <a name="begin_event_map"></a>  BEGIN_EVENT_MAP

Rozpoczyna się definicji mapę zdarzeń.

```cpp
BEGIN_EVENT_MAP(theClass,  baseClass)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Określa, że nazwa klasy kontrolki, którego zdarzenie Mapuj.

*baseClass*<br/>
Określa nazwę klasy bazowej *theClass*.

### <a name="remarks"></a>Uwagi

W pliku implementacji (.cpp), który definiuje funkcji elementów członkowskich dla swojej klasy rozpoczynać Mapa zdarzeń BEGIN_EVENT_MAP — makro, a następnie dodać wpisy makra dla każdego zdarzenia i ukończenia mapy zdarzeń za pomocą END_EVENT_MAP — makro.

Aby uzyskać więcej informacji o mapy zdarzeń i BEGIN_EVENT_MAP — makro, zobacz artykuł [kontrolek ActiveX: Zdarzenia](../../mfc/mfc-activex-controls-events.md).

### <a name="requirements"></a>Wymagania

**Nagłówek** afxctl.h

##  <a name="end_event_map"></a>  END_EVENT_MAP

Aby zakończyć definicji mapy zdarzeń, należy użyć END_EVENT_MAP — makro.

```cpp
END_EVENT_MAP()
```

### <a name="requirements"></a>Wymagania

**Nagłówek** afxctl.h

## <a name="event_custom"></a>  EVENT_CUSTOM —

Definiuje wpis mapy zdarzeń dla zdarzenia niestandardowego.

```cpp
EVENT_CUSTOM(pszName, pfnFire,  vtsParams)
```

### <a name="parameters"></a>Parametry

*pszName*<br/>
Nazwa zdarzenia.

*pfnFire*<br/>
Nazwa zdarzenia wyzwalanie funkcji.

*vtsParams*<br/>
Rozdzielonej spacjami listy co najmniej jedną stałą, określając listę parametrów funkcji.

### <a name="remarks"></a>Uwagi

*VtsParams* parametr jest rozdzielonej spacjami listy wartości z `VTS_` stałe. Co najmniej jeden z tych wartości, rozdzielone spacjami (nie przecinki) określa listę parametrów funkcji. Na przykład:

[!code-cpp[NVC_MFCActiveXControl#13](../../mfc/codesnippet/cpp/event-maps_2.cpp)]

Określa listę zawierającą 32-bitową liczbę całkowitą reprezentującą RGB kolor wartości, a następnie wskaźnik do `IFontDisp` interfejs obiektu czcionki.

`VTS_` Stałe i ich znaczenie są następujące:

|Symbol|Typ parametru|
|------------|--------------------|
|VTS_I2|**short**|
|VTS_I4|**long**|
|VTS_R4|**float**|
|VTS_R8|**double**|
|VTS_COLOR|OLE_COLOR|
|VTS_CY|WALUTY|
|VTS_DATE|DATE|
|VTS_BSTR|**Const** __char\*__|
|VTS_DISPATCH|LPDISPATCH|
|VTS_FONT|`IFontDispatch*`|
|VTS_HANDLE|UCHWYT|
|VTS_SCODE|SCODE|
|VTS_BOOL|WARTOŚĆ LOGICZNA|
|VTS_VARIANT|`const VARIANT*`|
|VTS_PVARIANT|`VARIANT*`|
|VTS_UNKNOWN|LPUNKNOWN|
|VTS_OPTEXCLUSIVE|OLE_OPTEXCLUSIVE|
|VTS_PICTURE|`IPictureDisp*`|
|VTS_TRISTATE|OLE_TRISTATE|
|VTS_XPOS_PIXELS|OLE_XPOS_PIXELS|
|VTS_YPOS_PIXELS|OLE_YPOS_PIXELS|
|VTS_XSIZE_PIXELS|OLE_XSIZE_PIXELS|
|VTS_YSIZE_PIXELS|OLE_YSIZE_PIXELS|
|TS_XPOS_HIMETRIC|OLE_XPOS_HIMETRIC|
|VTS_YPOS_HIMETRIC|OLE_YPOS_HIMETRIC|
|VTS_XSIZE_HIMETRIC|OLE_XSIZE_HIMETRIC|
|VTS_YSIZE_HIMETRIC|OLE_YSIZE_HIMETRIC|

> [!NOTE]
> Dodatkowe variant — stałe zostały zdefiniowane dla wszystkich wariantów typów, z wyjątkiem VTS_FONT i VTS_PICTURE, stanowiące wskaźnik ze stałą danych variant. Te stałe są nazywane przy użyciu `VTS_Pconstantname` Konwencji. Na przykład VTS_PCOLOR jest wskaźnikiem do VTS_COLOR — stała.

### <a name="requirements"></a>Wymagania

**Nagłówek** afxctl.h

## <a name="event_custom_id"></a>  EVENT_CUSTOM_ID

Określa zdarzenie funkcji dla niestandardowego zdarzenia należące do określonego przez identyfikator wysyłania *dispid*.

```cpp
EVENT_CUSTOM_ID(
  pszName,
  dispid,
  pfnFire,
  vtsParams)
```

### <a name="parameters"></a>Parametry

*pszName*<br/>
Nazwa zdarzenia.

*dispid*<br/>
Identyfikator wysyłania używany przez kontrolkę, gdy wyzwoleniem zdarzenia.

*pfnFire*<br/>
Nazwa zdarzenia wyzwalanie funkcji.

*vtsParams*<br/>
Zmiennej listy parametrów jest przekazywane do kontenera kontrolki, gdy zdarzenie jest uruchamiane.

### <a name="remarks"></a>Uwagi

*VtsParams* argument jest rozdzielonej spacjami listy wartości z `VTS_` stałe. Co najmniej jeden z tych wartości, rozdzielone spacjami, przecinki nie określa listy parametrów funkcji. Na przykład:

[!code-cpp[NVC_MFCActiveXControl#13](../../mfc/codesnippet/cpp/event-maps_2.cpp)]

Określa listę zawierającą 32-bitową liczbę całkowitą reprezentującą RGB kolor wartości, a następnie wskaźnik do `IFontDisp` interfejs obiektu czcionki.

Aby uzyskać listę `VTS_` stałych, zobacz [EVENT_CUSTOM](#event_custom).

### <a name="requirements"></a>Wymagania

**Nagłówek** afxctl.h

## <a name="on_oleverb"></a>  ON_OLEVERB

To makro definiuje wpis mapy wiadomości mapowaną zlecenie niestandardowych do funkcji składowej określonej kontrolki.

```cpp
ON_OLEVERB(idsVerbName,  memberFxn)
```

### <a name="parameters"></a>Parametry

*idsVerbName*<br/>
Identyfikator ciągu zasobu o nazwie zlecenie.

*memberFxn*<br/>
Funkcja wywoływane przez platformę, gdy jest wywoływany zlecenie.

### <a name="remarks"></a>Uwagi

Edytor zasobów może służyć do tworzenia nazwy niestandardowych zlecenia, które są dodawane do tabeli ciągów.

Prototyp funkcji *memberFxn* jest:

```cpp
BOOL memberFxn(
   LPMSG    lpMsg,
   HWND     hWndParent,
   LPCRECT  lpRect);
```

Wartości *lpMsg*, *hWndParent*, i *lprect —* parametry są pobierane z odpowiednich parametrów `IOleObject::DoVerb` funkcja elementu członkowskiego.

### <a name="requirements"></a>Wymagania

**Nagłówek** afxole.h

## <a name="on_stdoleverb"></a>  ON_STDOLEVERB

Użyj tego makra, aby zastąpić domyślne zachowanie standardowy czasownika.

```cpp
ON_STDOLEVERB(iVerb, memberFxn)
```

### <a name="parameters"></a>Parametry

*iVerb*<br/>
Indeks standardowy czasownika zlecenie zastępowaniu.

*memberFxn*<br/>
Funkcja wywoływane przez platformę, gdy jest wywoływany zlecenie.

### <a name="remarks"></a>Uwagi

Indeks standardowy czasownika ma postać `OLEIVERB_`, a następnie akcję. OLEIVERB_SHOW OLEIVERB_HIDE i OLEIVERB_UIACTIVATE przedstawiono kilka przykładów zleceń standardowych.

Zobacz [ON_OLEVERB](#on_oleverb) opis prototypu funkcji, która ma być używany jako *memberFxn* parametru.

### <a name="requirements"></a>Wymagania

**Nagłówek** afxole.h

## <a name="see-also"></a>Zobacz także

[Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)
