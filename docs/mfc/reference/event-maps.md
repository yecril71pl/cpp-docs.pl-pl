---
title: Mapy zdarzeń | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros.maps
dev_langs:
- C++
helpviewer_keywords:
- event maps [MFC]
ms.assetid: 1ed53aee-bc53-43cd-834a-6fb935c0d29b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4e7ab64af82e2f37104f82778d4c6f5eb12bd032
ms.sourcegitcommit: 05075fce8a0ed7fddb99f50f3931db966a91450d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/20/2018
ms.locfileid: "36271308"
---
# <a name="event-maps"></a>Mapy zdarzeń
Zawsze, gdy formant pragnie powiadomić jego kontenera, w którym wykonano akcję (określoną przez dewelopera kontrolek) (na przykład naciśnięcie klawisza, kliknięcie myszą lub zmianę stanu formantu) wywołuje funkcję inicjowanie zdarzeń. Ta funkcja powiadamia kontenera kontrolki, w którym niektóre akcje, ważne nastąpił przed wyzwoleniem zdarzenia pokrewne.  
  
 Microsoft Foundation Class Library zapewnia model programowania zoptymalizowane pod kątem uruchamiania zdarzeń. W tym modelu "mapy zdarzeń" służą do wyznaczenia, które funkcje wyzwalać zdarzenia dla określonego formantu. Mapy zdarzeń zawiera jedno makro dla każdego zdarzenia. Na przykład mapę zdarzeń który generowane zasobu kliknij zdarzenie może wyglądać następująco:  
  
 [!code-cpp[NVC_MFCAxCtl#16](../../mfc/reference/codesnippet/cpp/event-maps_1.cpp)]  
  
 **Event_stock_click —** makro wskazuje, czy formant uruchomią zasobu kliknij zdarzenie za każdym razem, gdy wykryje myszy, kliknij przycisk. Aby uzyskać bardziej szczegółowy wykaz innych standardowych zdarzeń, zobacz artykuł [formantów ActiveX: zdarzenia](../../mfc/mfc-activex-controls-events.md). Makra są również dostępne w celu wskazania zdarzeń niestandardowych.  
  
 Makra mapy zdarzeń są ważne, zwykle nie wstawiono je bezpośrednio. Jest to spowodowane okna właściwości automatycznie tworzy wpisy mapy zdarzeń w plikach źródłowych przypadku użycia jej do skojarzenia ze zdarzeniami funkcje inicjowanie zdarzeń. Zawsze, gdy chcesz edytować, lub Dodaj wpis Mapa zdarzeń można użyć okna właściwości.  
  
 Aby obsługiwać mapy zdarzeń, MFC zapewnia następujące makra:  
  
### <a name="event-map-declaration-and-demarcation"></a>Zdarzenie mapy deklaracja i odgraniczenie  
  
|||  
|-|-|  
|[DECLARE_EVENT_MAP —](#declare_event_map)|Deklaruje używane w klasie mapowania zdarzeń na inicjowanie zdarzeń funkcji (należy użyć w deklaracji klasy) mapę zdarzeń.|  
|[BEGIN_EVENT_MAP —](#begin_event_map)|Rozpoczyna się definicji mapy zdarzeń (musi być zastosowany w implementacji klasy).|  
|[END_EVENT_MAP —](#end_event_map)|Kończy definicję mapy zdarzeń (musi być zastosowany w implementacji klasy).|  
  
### <a name="event-mapping-macros"></a>Makra mapowania zdarzeń  
  
|||  
|-|-|  
|[EVENT_CUSTOM —](#event_custom)|Wskazuje, funkcja inicjowanie zdarzeń, które będą wyzwalać określone zdarzenie.|  
|[EVENT_CUSTOM_ID —](#event_custom_id)|Wskazuje, funkcja inicjowanie zdarzeń, które będą uruchamiane określonego zdarzenia, przy użyciu identyfikatora wyznaczonych wysyłania.|  
  
### <a name="message-mapping-macros"></a>Makra mapowania wiadomości  
  
|||  
|-|-|  
|[ON_OLEVERB —](#on_oleverb)|Wskazuje niestandardowego polecenia obsługiwane przez formant OLE.|  
|[ON_STDOLEVERB —](#on_stdoleverb)|Zastępuje mapowanie zlecenie standardowe formantu OLE.|  
  
##  <a name="declare_event_map"></a>  DECLARE_EVENT_MAP —  
 Każdy `COleControl`-klasy pochodnej w programie zapewniają Mapa zdarzeń, aby określić zdarzenia formantu zostanie zastosowana.  
  
```   
DECLARE_EVENT_MAP()   
```  
  
### <a name="remarks"></a>Uwagi  
 Użyj `DECLARE_EVENT_MAP` makro końca z deklaracji klasy. Następnie, w pliku .cpp, który definiuje funkcji elementów członkowskich klasy, należy użyć `BEGIN_EVENT_MAP` makra, makro wpisy dla każdego zdarzenia formantu i `END_EVENT_MAP` makra, aby zadeklarować na końcu listy zdarzeń.  
  
 Aby uzyskać więcej informacji na mapy zdarzeń, zobacz artykuł [formantów ActiveX: zdarzenia](../../mfc/mfc-activex-controls-events.md).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxctl.h  
  
##  <a name="begin_event_map"></a>  BEGIN_EVENT_MAP —  
 Rozpoczyna się definicji mapy zdarzeń.  
  
```   
BEGIN_EVENT_MAP(theClass,  baseClass)  
```  
  
### <a name="parameters"></a>Parametry  
 `theClass`  
 Określa nazwę klasy formantu, którego zdarzenie mapowania.  
  
 `baseClass`  
 Określa nazwę klasy podstawowej `theClass`.  
  
### <a name="remarks"></a>Uwagi  
 W pliku implementacji (.cpp), który definiuje funkcje Członkowskie dla klasy, należy uruchomić Mapa zdarzeń z `BEGIN_EVENT_MAP` makra, Dodaj makro wpisy dla każdego ze zdarzeń i ukończyć Mapa zdarzeń z `END_EVENT_MAP` makra.  
  
 Aby uzyskać więcej informacji na temat zdarzeń mapuje i `BEGIN_EVENT_MAP` makra, zapoznaj się z artykułem [formantów ActiveX: zdarzenia](../../mfc/mfc-activex-controls-events.md).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxctl.h  
  
##  <a name="end_event_map"></a>  END_EVENT_MAP —  
 Użyj `END_EVENT_MAP` makro na koniec definicji mapy zdarzeń.  
  
```   
END_EVENT_MAP()   
```  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxctl.h  
  
##  <a name="event_custom"></a>  EVENT_CUSTOM —  
 Określa wpis Mapa zdarzeń dla zdarzenia niestandardowego.  
  
```   
EVENT_CUSTOM(pszName, pfnFire,  vtsParams) 
```  
  
### <a name="parameters"></a>Parametry  
 `pszName`  
 Nazwa zdarzenia.  
  
 `pfnFire`  
 Nazwa zdarzenie wywołujące funkcji.  
  
 `vtsParams`  
 Rozdzielonej spacjami listy co najmniej jedną stałą określenie listy parametrów funkcji.  
  
### <a name="remarks"></a>Uwagi  
 `vtsParams` Parametr jest rozdzielonej spacjami listy wartości z **VTS_** stałe. Co najmniej jeden z tych wartości, rozdzielając je spacjami (nie przecinkami) określa listę parametrów funkcji. Na przykład:  
  
 [!code-cpp[NVC_MFCActiveXControl#13](../../mfc/codesnippet/cpp/event-maps_2.cpp)]  
  
 Określa listę zawierającą 32-bitową liczbę całkowitą reprezentującą RGB wartości, następuje wskaźnik koloru **IFontDisp** interfejsu obiektu czcionki.  
  
 **VTS_** stałe i ich znaczenie są następujące:  
  
|Symbol|Typ parametru|  
|------------|--------------------|  
|**VTS_I2**|**short**|  
|**VTS_I4**|**long**|  
|**VTS_R4**|**float**|  
|**VTS_R8**|**double**|  
|**VTS_COLOR**|**OLE_COLOR**|  
|**VTS_CY**|**WALUTY**|  
|**VTS_DATE**|**DATA**|  
|**VTS_BSTR**|**Const char\\\***|  
|**VTS_DISPATCH**|`LPDISPATCH`|  
|**VTS_FONT**|**IFontDispatch\\\***|  
|**VTS_HANDLE**|`HANDLE`|  
|**VTS_SCODE**|`SCODE`|  
|**VTS_BOOL**|**BOOL**|  
|**VTS_VARIANT**|**Wariant const\\\***|  
|**VTS_PVARIANT**|**VARIANT\\\***|  
|**VTS_UNKNOWN**|`LPUNKNOWN`|  
|**VTS_OPTEXCLUSIVE**|**OLE_OPTEXCLUSIVE**|  
|**VTS_PICTURE —**|**IPictureDisp\\\***|  
|**VTS_TRISTATE —**|**OLE_TRISTATE**|  
|**VTS_XPOS_PIXELS**|**OLE_XPOS_PIXELS**|  
|**VTS_YPOS_PIXELS**|**OLE_YPOS_PIXELS**|  
|**VTS_XSIZE_PIXELS**|**OLE_XSIZE_PIXELS**|  
|**VTS_YSIZE_PIXELS**|**OLE_YSIZE_PIXELS**|  
|**VTS_XPOS_HIMETRIC**|**OLE_XPOS_HIMETRIC**|  
|**VTS_YPOS_HIMETRIC**|**OLE_YPOS_HIMETRIC**|  
|**VTS_XSIZE_HIMETRIC**|**OLE_XSIZE_HIMETRIC**|  
|**VTS_YSIZE_HIMETRIC**|**OLE_YSIZE_HIMETRIC**|  
  
> [!NOTE]
>  Dodatkowe stałe variant zostały zdefiniowane dla wszystkich typów variant, z wyjątkiem produktów **vts_font —** i **vts_picture —**, które zapewniają wskaźnik do stała danych variant. Stałe te są nazywane przy użyciu **VTS_P** `constantname` Konwencji. Na przykład **VTS_PCOLOR** jest wskaźnikiem do **vts_color —** stałej.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxctl.h  
  
##  <a name="event_custom_id"></a>  EVENT_CUSTOM_ID —  
 Definiuje zdarzenie wywołujące funkcja niestandardowe zdarzenie należących do określonej przez identyfikator wysyłania `dispid`.  
  
```   
EVENT_CUSTOM_ID(
  pszName,   
  dispid,   
  pfnFire,
  vtsParams)  
 
```  
  
### <a name="parameters"></a>Parametry  
 `pszName`  
 Nazwa zdarzenia.  
  
 `dispid`  
 Identyfikator wysyłania używany przez formant, gdy wyzwoleniem zdarzenia.  
  
 `pfnFire`  
 Nazwa zdarzenie wywołujące funkcji.  
  
 `vtsParams`  
 Zmiennej listy parametrów przekazane do kontenera formantu, gdy zdarzenie jest wywoływane.  
  
### <a name="remarks"></a>Uwagi  
 `vtsParams` Argument jest rozdzielonej spacjami listy wartości z **VTS_** stałe. Co najmniej jeden z tych wartości rozdzielone spacjami, a nie przecinkami, określa listę parametrów funkcji. Na przykład:  
  
 [!code-cpp[NVC_MFCActiveXControl#13](../../mfc/codesnippet/cpp/event-maps_2.cpp)]  
  
 Określa listę zawierającą 32-bitową liczbę całkowitą reprezentującą RGB wartości, następuje wskaźnik koloru **IFontDisp** interfejsu obiektu czcionki.  
  
 Aby uzyskać listę **VTS_** stałe, zobacz [event_custom —](#event_custom).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxctl.h  
  
##  <a name="on_oleverb"></a>  ON_OLEVERB —  
 To makro definiuje wpisu mapy wiadomości, mapująca niestandardowego polecenia do funkcji członkowskiej określonego formantu.  
  
```   
ON_OLEVERB(idsVerbName,  memberFxn)   
```  
  
### <a name="parameters"></a>Parametry  
 *idsVerbName*  
 Identyfikator zasobu ciągu oznacza, że nazwa.  
  
 `memberFxn`  
 Funkcja wywoływana przez platformę, gdy zlecenie jest wywoływany.  
  
### <a name="remarks"></a>Uwagi  
 Edytor zasobów może służyć do tworzenia nazwy niestandardowego polecenia, które są dodawane do tabeli w ciągu.  
  
 Prototyp funkcji `memberFxn` jest:  
  
 `BOOL memberFxn(`    
 `LPMSG` `lpMsg` `,`   
 `HWND` `hWndParent` `,`   
 `LPCRECT` `lpRect`   `);`  
  
 Wartości `lpMsg`, `hWndParent`, i `lpRect` parametry są pobierane z odpowiadających im parametrów **IOleObject::DoVerb** funkcję elementu członkowskiego.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxole.h  
  
##  <a name="on_stdoleverb"></a>  ON_STDOLEVERB —  
 To makro umożliwia zastąpienie zachowania domyślnego standardowe zlecenia.  
  
```   
ON_STDOLEVERB(iVerb,   memberFxn)   
```  
  
### <a name="parameters"></a>Parametry  
 `iVerb`  
 Indeks standardowe zlecenie zlecenie aktualnie zastępowany.  
  
 `memberFxn`  
 Funkcja wywoływana przez platformę, gdy zlecenie jest wywoływany.  
  
### <a name="remarks"></a>Uwagi  
 Indeks standardowe zlecenie ma postać **OLEIVERB_**, a następnie akcji. `OLEIVERB_SHOW`, `OLEIVERB_HIDE`, i `OLEIVERB_UIACTIVATE` przedstawiono kilka przykładów zleceń standardowych.  
  
 Zobacz [on_oleverb —](#on_oleverb) opis prototypu funkcji, które mają być używane jako `memberFxn` parametru.  

  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxole.h  
    
## <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)
