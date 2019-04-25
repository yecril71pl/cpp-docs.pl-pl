---
title: Klasa COleServerItem
ms.date: 11/04/2016
f1_keywords:
- COleServerItem
- AFXOLE/COleServerItem
- AFXOLE/COleServerItem::COleServerItem
- AFXOLE/COleServerItem::AddOtherClipboardData
- AFXOLE/COleServerItem::CopyToClipboard
- AFXOLE/COleServerItem::DoDragDrop
- AFXOLE/COleServerItem::GetClipboardData
- AFXOLE/COleServerItem::GetDocument
- AFXOLE/COleServerItem::GetEmbedSourceData
- AFXOLE/COleServerItem::GetItemName
- AFXOLE/COleServerItem::GetLinkSourceData
- AFXOLE/COleServerItem::GetObjectDescriptorData
- AFXOLE/COleServerItem::IsConnected
- AFXOLE/COleServerItem::IsLinkedItem
- AFXOLE/COleServerItem::NotifyChanged
- AFXOLE/COleServerItem::OnDoVerb
- AFXOLE/COleServerItem::OnDraw
- AFXOLE/COleServerItem::OnDrawEx
- AFXOLE/COleServerItem::OnGetClipboardData
- AFXOLE/COleServerItem::OnGetExtent
- AFXOLE/COleServerItem::OnInitFromData
- AFXOLE/COleServerItem::OnQueryUpdateItems
- AFXOLE/COleServerItem::OnRenderData
- AFXOLE/COleServerItem::OnRenderFileData
- AFXOLE/COleServerItem::OnRenderGlobalData
- AFXOLE/COleServerItem::OnSetColorScheme
- AFXOLE/COleServerItem::OnSetData
- AFXOLE/COleServerItem::OnSetExtent
- AFXOLE/COleServerItem::OnUpdate
- AFXOLE/COleServerItem::OnUpdateItems
- AFXOLE/COleServerItem::SetItemName
- AFXOLE/COleServerItem::GetDataSource
- AFXOLE/COleServerItem::OnHide
- AFXOLE/COleServerItem::OnOpen
- AFXOLE/COleServerItem::OnShow
- AFXOLE/COleServerItem::m_sizeExtent
helpviewer_keywords:
- COleServerItem [MFC], COleServerItem
- COleServerItem [MFC], AddOtherClipboardData
- COleServerItem [MFC], CopyToClipboard
- COleServerItem [MFC], DoDragDrop
- COleServerItem [MFC], GetClipboardData
- COleServerItem [MFC], GetDocument
- COleServerItem [MFC], GetEmbedSourceData
- COleServerItem [MFC], GetItemName
- COleServerItem [MFC], GetLinkSourceData
- COleServerItem [MFC], GetObjectDescriptorData
- COleServerItem [MFC], IsConnected
- COleServerItem [MFC], IsLinkedItem
- COleServerItem [MFC], NotifyChanged
- COleServerItem [MFC], OnDoVerb
- COleServerItem [MFC], OnDraw
- COleServerItem [MFC], OnDrawEx
- COleServerItem [MFC], OnGetClipboardData
- COleServerItem [MFC], OnGetExtent
- COleServerItem [MFC], OnInitFromData
- COleServerItem [MFC], OnQueryUpdateItems
- COleServerItem [MFC], OnRenderData
- COleServerItem [MFC], OnRenderFileData
- COleServerItem [MFC], OnRenderGlobalData
- COleServerItem [MFC], OnSetColorScheme
- COleServerItem [MFC], OnSetData
- COleServerItem [MFC], OnSetExtent
- COleServerItem [MFC], OnUpdate
- COleServerItem [MFC], OnUpdateItems
- COleServerItem [MFC], SetItemName
- COleServerItem [MFC], GetDataSource
- COleServerItem [MFC], OnHide
- COleServerItem [MFC], OnOpen
- COleServerItem [MFC], OnShow
- COleServerItem [MFC], m_sizeExtent
ms.assetid: 80256df6-3888-4256-944b-787d4b2e6b0d
ms.openlocfilehash: c4c026975e9884ac2a0e6aaef31e799c2b5b09bf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62224236"
---
# <a name="coleserveritem-class"></a>Klasa COleServerItem

Oferuje interfejs serwera elementów OLE.

## <a name="syntax"></a>Składnia

```
class COleServerItem : public CDocItem
```

## <a name="members"></a>Elementy członkowskie

### <a name="protected-constructors"></a>Konstruktory chronione

|Nazwa|Opis|
|----------|-----------------|
|[COleServerItem::COleServerItem](#coleserveritem)|Konstruuje `COleServerItem` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleServerItem::AddOtherClipboardData](#addotherclipboarddata)|Umieszcza prezentacji i konwersji formatów w `COleDataSource` obiektu.|
|[COleServerItem::CopyToClipboard](#copytoclipboard)|Kopiuje element do Schowka.|
|[COleServerItem::DoDragDrop](#dodragdrop)|Wykonuje operację przeciągania i upuszczania.|
|[COleServerItem::GetClipboardData](#getclipboarddata)|Pobiera źródło danych do użycia w transfer danych (przeciągania i upuszczania lub Schowka).|
|[COleServerItem::GetDocument](#getdocument)|Zwraca dokument serwera, który zawiera element.|
|[COleServerItem::GetEmbedSourceData](#getembedsourcedata)|Pobiera dane CF_EMBEDSOURCE dla elementu OLE.|
|[COleServerItem::GetItemName](#getitemname)|Zwraca nazwę elementu. Używany tylko połączone elementy.|
|[COleServerItem::GetLinkSourceData](#getlinksourcedata)|Pobiera dane CF_LINKSOURCE dla elementu OLE.|
|[COleServerItem::GetObjectDescriptorData](#getobjectdescriptordata)|Pobiera dane CF_OBJECTDESCRIPTOR dla elementu OLE.|
|[COleServerItem::IsConnected](#isconnected)|Wskazuje, czy element jest obecnie dołączony do aktywny kontener.|
|[COleServerItem::IsLinkedItem](#islinkeditem)|Wskazuje, czy element reprezentuje połączony element OLE.|
|[COleServerItem::NotifyChanged](#notifychanged)|Aktualizuje wszystkie kontenery za pomocą aktualizacji automatycznych łącza.|
|[COleServerItem::OnDoVerb](#ondoverb)|Wywołuje się, by wykonać zlecenia.|
|[COleServerItem::OnDraw](#ondraw)|Wywołuje się, gdy kontener żąda danych do rysowania elementu; Implementacja jest wymagana.|
|[COleServerItem::OnDrawEx](#ondrawex)|Wywoływana dla rysowań elementów specjalne.|
|[COleServerItem::OnGetClipboardData](#ongetclipboarddata)|Metoda wywoływana przez platformę, by uzyskać dane, które będą skopiowane do Schowka.|
|[COleServerItem::OnGetExtent](#ongetextent)|Metoda wywoływana przez platformę, by pobrać rozmiar elementu OLE.|
|[COleServerItem::OnInitFromData](#oninitfromdata)|Metoda wywoływana przez platformę, by zainicjować element OLE przy użyciu zawartości określony obiekt transferu danych.|
|[COleServerItem::OnQueryUpdateItems](#onqueryupdateitems)|Wywoływane w celu określenia, czy którykolwiek z elementów powiązanych wymagają aktualizacji.|
|[COleServerItem::OnRenderData](#onrenderdata)|Pobiera dane jako część opóźnione renderowanie.|
|[COleServerItem::OnRenderFileData](#onrenderfiledata)|Pobiera dane do `CFile` obiektu jako część opóźnione renderowanie.|
|[COleServerItem::OnRenderGlobalData](#onrenderglobaldata)|Pobiera dane do wartości HGLOBAL jako część opóźnione renderowanie.|
|[COleServerItem::OnSetColorScheme](#onsetcolorscheme)|Wywołuje się, by ustawić schemat kolorów elementu.|
|[COleServerItem::OnSetData](#onsetdata)|Wywołuje się, by ustawić elementu danych.|
|[COleServerItem::OnSetExtent](#onsetextent)|Metoda wywoływana przez platformę, by ustawić rozmiar elementu OLE.|
|[COleServerItem::OnUpdate](#onupdate)|Wywołuje się, kiedy należy do niektórych części dokumentu elementu została zmieniona.|
|[COleServerItem::OnUpdateItems](#onupdateitems)|Wywoływana, aby zaktualizować pamięć podręczną prezentacji wszystkich elementów w dokumencie serwera.|
|[COleServerItem::SetItemName](#setitemname)|Ustawia nazwę elementu. Używany tylko połączone elementy.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[COleServerItem::GetDataSource](#getdatasource)|Pobiera obiekt używany do przechowywania konwersji formatów.|
|[COleServerItem::OnHide](#onhide)|Metoda wywoływana przez platformę, by ukryć element OLE.|
|[COleServerItem::OnOpen](#onopen)|Metoda wywoływana przez platformę, by wyświetlić element OLE w osobnym oknie najwyższego poziomu.|
|[COleServerItem::OnShow](#onshow)|Wywołuje się, gdy kontener żąda danych do wyświetlenia elementu.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[COleServerItem::m_sizeExtent](#m_sizeextent)|Informuje serwer o tym, ile elementu OLE jest widoczny.|

## <a name="remarks"></a>Uwagi

Połączony element może reprezentować niektórych lub wszystkich dokumentów serwera. Osadzonego elementu zawsze reprezentuje dokument całego serwera.

`COleServerItem` Klasa definiuje kilka funkcji Członkowskich możliwym do zastąpienia, które są wywoływane przez bibliotek OLE systemu dołączana dynamicznie (dll), zwykle w odpowiedzi na żądania z aplikacji kontenera. Te funkcje elementów członkowskich Zezwól aplikacji kontenera do manipulowania elementem pośrednio na różne sposoby, takie jak wyświetlanie, wykonywanie jej zlecenia lub pobieranie jej danych w różnych formatach.

Aby użyć `COleServerItem`dziedziczyć po nim klasę i zaimplementować [OnDraw](#ondraw) i [Serialize](../../mfc/reference/cobject-class.md#serialize) funkcji elementów członkowskich. `OnDraw` Funkcji zawiera reprezentację metaplik element, dzięki któremu będzie wyświetlana po aplikacji kontenera zostanie otwarty w dokumencie złożonym. `Serialize` Funkcji `CObject` zapewnia natywną reprezentację elementu, dzięki czemu element osadzony, należy dokonać między aplikacje kontenera i serwera. [OnGetExtent](#ongetextent) zapewnia naturalnych rozmiar elementu do kontenera, umożliwiając kontener, aby rozmiar elementu.

Aby uzyskać więcej informacji na temat serwerów i materiały pokrewne, zobacz artykuł [serwerów: Implementowanie serwera](../../mfc/servers-implementing-a-server.md) oraz "Tworzenie kontenera/serwera aplikacji" w artykule [kontenerów: Zaawansowane funkcje](../../mfc/containers-advanced-features.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

`COleServerItem`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxole.h

##  <a name="addotherclipboarddata"></a>  COleServerItem::AddOtherClipboardData

Wywołaj tę funkcję, aby umieścić formaty prezentacji i konwersji dla elementu OLE w określonym `COleDataSource` obiektu.

```
void AddOtherClipboardData(COleDataSource* pDataSource);
```

### <a name="parameters"></a>Parametry

*pDataSource*<br/>
Wskaźnik do `COleDataSource` obiekt, w którym dane powinny być umieszczone.

### <a name="remarks"></a>Uwagi

Ci się wdrożyć [OnDraw](#ondraw) funkcja elementu członkowskiego, aby zapewnić format prezentacji (obraz metaplik) dla elementu. Aby zapewnić obsługę innych konwersji formatów, zarejestruj je przy użyciu [COleDataSource](../../mfc/reference/coledatasource-class.md) obiektu zwróconego przez [metody GetDataSource](#getdatasource) i zastąpić [OnRenderData](#onrenderdata) funkcja elementu członkowskiego do Podaj dane w formatach, które mają być obsługiwane.

##  <a name="coleserveritem"></a>  COleServerItem::COleServerItem

Konstruuje `COleServerItem` obiektu i dodaje go do dokumentu na serwerze zbiór elementów dokumentu.

```
COleServerItem(
    COleServerDoc* pServerDoc,
    BOOL bAutoDelete);
```

### <a name="parameters"></a>Parametry

*pServerDoc*<br/>
Wskaźnik do dokumentu, który będzie zawierać nowy element.

*bAutoDelete*<br/>
Flaga oznaczająca, czy obiekt może zostać usunięty po udostępnieniu do niej łącza. Ustaw tę opcję na wartość FALSE, jeśli `COleServerItem` obiekt jest integralną częścią danych dokumentu, które należy usunąć. Ustaw tę pozycję na wartość TRUE, jeśli obiekt jest strukturą dodatkowych, używany do identyfikowania zakres danych dokumentu, który może zostać usunięta przez platformę.

##  <a name="copytoclipboard"></a>  COleServerItem::CopyToClipboard

Wywołaj tę funkcję, aby skopiować element OLE do Schowka.

```
void CopyToClipboard(BOOL bIncludeLink = FALSE);
```

### <a name="parameters"></a>Parametry

*bIncludeLink*<br/>
Ustaw tę opcję na wartość TRUE, jeśli danych link powinien zostać skopiowany do Schowka. Ustaw tę pozycję na wartość FALSE, jeśli serwer aplikacji nie obsługuje łączy.

### <a name="remarks"></a>Uwagi

Funkcja używa [OnGetClipboardData](#ongetclipboarddata) funkcji elementu członkowskiego, aby utworzyć [COleDataSource](../../mfc/reference/coledatasource-class.md) obiekt zawierający dane elementu OLE w formatach obsługiwanych. Funkcja umieszcza `COleDataSource` obiektu w Schowku przy użyciu [COleDataSource::SetClipboard](../../mfc/reference/coledatasource-class.md#setclipboard) funkcji. `COleDataSource` Obiekt zawiera elementu danych natywnych i jego reprezentację w formacie CF_METAFILEPICT, a także dane w dowolnej formaty konwersji możliwość obsługi. Ci się wdrożyć [Serialize](../../mfc/reference/cobject-class.md#serialize) i [OnDraw](#ondraw) dla tej funkcji elementu członkowskiego do pracy.

##  <a name="dodragdrop"></a>  COleServerItem::DoDragDrop

Wywołaj `DoDragDrop` funkcja elementu członkowskiego, które można wykonać operacji przeciągania i upuszczania.

```
DROPEFFECT DoDragDrop(
    LPCRECT lpRectItem,
    CPoint ptOffset,
    BOOL bIncludeLink = FALSE,
    DWORD dwEffects = DROPEFFECT_COPY | DROPEFFECT_MOVE,
    LPCRECT lpRectStartDrag = NULL);
```

### <a name="parameters"></a>Parametry

*lpRectItem*<br/>
Prostokąt elementu na ekranie, w pikselach, względem pola klienta.

*ptOffset*<br/>
Przesunięcie od *lpItemRect* których położenie myszy zakończyła się w czasie przeciągania.

*bIncludeLink*<br/>
Ustaw tę opcję na wartość TRUE, jeśli danych link powinien zostać skopiowany do Schowka. Ustaw ją na wartość FALSE, jeśli aplikacja nie obsługuje łączy.

*dwEffects*<br/>
Określa, czy efekty, których elementem źródłowym przeciągania pozwoli w operacji przeciągania (kombinację kopiowanie, przenoszenie i Link)

*lpRectStartDrag*<br/>
Wskaźnik do prostokąt, który definiuje, w którym faktycznie zacznie przeciągania. Aby uzyskać więcej informacji zobacz następujące sekcji uwag.

### <a name="return-value"></a>Wartość zwracana

Wartość z wyliczenia DROPEFFECT. Jeśli jest to DROPEFFECT_MOVE, należy usunąć oryginalnych danych.

### <a name="remarks"></a>Uwagi

Operacja przeciągania i upuszczania nie rozpoczyna się natychmiast. Czeka, aż kursor myszy opuszcza prostokąt określony przez *lpRectStartDrag* lub dopóki nie przeszły przez określoną liczbę milisekund. Jeśli *lpRectStartDrag* ma wartość NULL, prostokąt domyślnej jest używana co przeciągania rozpoczyna się, gdy kursor myszy przesuwa się o jeden piksel.

Czas opóźnienia jest określona przez ustawienie klucza rejestru. Możesz zmienić czas opóźnienia, wywołując [CWinApp::WriteProfileString](../../mfc/reference/cwinapp-class.md#writeprofilestring) lub [CWinApp::WriteProfileInt](../../mfc/reference/cwinapp-class.md#writeprofileint). Jeśli nie określisz czas opóźnienia, jest używana domyślna wartość 200 ms. Przeciągnij opóźnienia są przechowywane w następujący sposób:

- Czas opóźnienia przeciągania Windows NT jest przechowywany w HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\NT\CurrentVersion\IniFileMapping\win.ini\Windows\DragDelay.

- Czas opóźnienia przeciągania 3.x Windows są przechowywane w ZWYCIĘSTWA. Plik INI, w sekcji [Windows}.

- Przeciągnij Windows 95/98 opóźnienia są przechowywane w pamięci podręcznej wersji systemu Windows. PLIKU INI.

Dla przeciągnij więcej informacji o tym, jak opóźnienie informacje są przechowywane w rejestrze albo lub. Plik INI, zobacz [WriteProfileString](/windows/desktop/api/winbase/nf-winbase-writeprofilestringa) w zestawie Windows SDK.

##  <a name="getclipboarddata"></a>  COleServerItem::GetClipboardData

Wywołaj tę funkcję, aby wypełnić określonego [COleDataSource](../../mfc/reference/coledatasource-class.md) obiektu z danymi, które będą skopiowane do Schowka, jeśli wywołano [CopyToClipboard](#copytoclipboard) (te same dane również będą przenoszone, jeśli użytkownik wywołuje się [DoDragDrop](#dodragdrop)).

```
void GetClipboardData(
    COleDataSource* pDataSource,
    BOOL bIncludeLink = FALSE,
    LPPOINT lpOffset = NULL,
    LPSIZE lpSize = NULL);
```

### <a name="parameters"></a>Parametry

*pDataSource*<br/>
Wskaźnik do `COleDataSource` obiekt, który będzie otrzymywać dane elementu OLE we wszystkich obsługiwanych formatach.

*bIncludeLink*<br/>
Wartość TRUE, jeśli danych link powinien zostać skopiowany do Schowka. Wartość FALSE, jeśli aplikacja serwera nie obsługuje łączy.

*lpOffset*<br/>
Przesunięcie w pikselach, kursor myszy ze źródła obiektu.

*lpSize*<br/>
Rozmiar obiektu w pikselach.

### <a name="remarks"></a>Uwagi

Ta funkcja wywołuje [GetEmbedSourceData](#getembedsourcedata) funkcję elementu członkowskiego w celu uzyskania danych natywnych dla elementu OLE i wywołania [AddOtherClipboardData](#addotherclipboarddata) funkcję elementu członkowskiego w celu uzyskania formatu prezentacji i wszystkie obsługiwane formaty konwersji. Jeśli *bIncludeLink* jest wartość PRAWDA, funkcja również wywołuje [GetLinkSourceData](#getlinksourcedata) można pobrać danych linku dla elementu.

Przesłonić tę funkcję, jeśli chcesz umieścić formatów w `COleDataSource` obiekt przed lub po tych formatów, dostarczone przez `CopyToClipboard`.

##  <a name="getdatasource"></a>  COleServerItem::GetDataSource

Wywołaj tę funkcję, aby uzyskać [COleDataSource](../../mfc/reference/coledatasource-class.md) obiekt używany do przechowywania konwersji formatów, obsługiwanych przez aplikację serwera.

```
COleDataSource* GetDataSource();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `COleDataSource` obiekt używany do przechowywania formaty konwersji.

### <a name="remarks"></a>Uwagi

Jeśli chcesz, aby aplikacja serwera do zaoferowania danych w różnych formatach podczas danych transferu operacji, zarejestruj te formaty z `COleDataSource` obiektu zwróconego przez tę funkcję. Na przykład, jeśli chcesz podać CF_TEXT reprezentacja elementu OLE Schowek lub operacji przeciągania i upuszczania, czy rejestrowania formacie z `COleDataSource` ta funkcja zwraca obiekt, a następnie zastąp `OnRenderXxxData` funkcji składowej Podaj dane.

##  <a name="getdocument"></a>  COleServerItem::GetDocument

Wywołaj tę funkcję, aby uzyskać wskaźnik do dokumentu, który zawiera element.

```
COleServerDoc* GetDocument() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do dokumentu, który zawiera element; Wartość NULL, jeśli element nie jest częścią dokumentu.

### <a name="remarks"></a>Uwagi

Dzięki temu dostęp do dokumentu serwera, który jest przekazywany jako argument do `COleServerItem` konstruktora.

##  <a name="getembedsourcedata"></a>  COleServerItem::GetEmbedSourceData

Wywołaj tę funkcję można pobrać danych CF_EMBEDSOURCE dla elementu OLE.

```
void GetEmbedSourceData(LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>Parametry

*lpStgMedium*<br/>
Wskaźnik do [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) strukturę, która będzie odbierać dane CF_EMBEDSOURCE dla elementu OLE.

### <a name="remarks"></a>Uwagi

Ten format obejmuje elementu danych natywnych. Ci się wdrożyć `Serialize` funkcję członkowską tę funkcję, aby działać prawidłowo.

Następnie można dodać wynik ze źródłem danych przy użyciu [COleDataSource::CacheData](../../mfc/reference/coledatasource-class.md#cachedata). Ta funkcja jest wywoływana automatycznie przez [COleServerItem::OnGetClipboardData](#ongetclipboarddata).

Aby uzyskać więcej informacji, zobacz [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) w zestawie Windows SDK.

##  <a name="getitemname"></a>  COleServerItem::GetItemName

Wywołaj tę funkcję, aby uzyskać nazwę elementu.

```
const CString& GetItemName() const;
```

### <a name="return-value"></a>Wartość zwracana

Nazwa elementu.

### <a name="remarks"></a>Uwagi

Zazwyczaj Wywołaj tę funkcję tylko dla połączonych elementów.

##  <a name="getlinksourcedata"></a>  COleServerItem::GetLinkSourceData

Wywołaj tę funkcję można pobrać danych CF_LINKSOURCE dla elementu OLE.

```
BOOL GetLinkSourceData(LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>Parametry

*lpStgMedium*<br/>
Wskaźnik do [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) strukturę, która będzie odbierać dane CF_LINKSOURCE dla elementu OLE.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ten format zawiera identyfikator CLSID opisujący typ elementu OLE i informacje potrzebne do zlokalizowania dokumentu zawierającego element OLE.

Następnie można dodać wynik ze źródłem danych przy użyciu [COleDataSource::CacheData](../../mfc/reference/coledatasource-class.md#cachedata). Ta funkcja jest wywoływana automatycznie przez [OnGetClipboardData](#ongetclipboarddata).

Aby uzyskać więcej informacji, zobacz [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) w zestawie Windows SDK.

##  <a name="getobjectdescriptordata"></a>  COleServerItem::GetObjectDescriptorData

Wywołaj tę funkcję można pobrać danych CF_OBJECTDESCRIPTOR dla elementu OLE.

```
void GetObjectDescriptorData(
    LPPOINT lpOffset,
    LPSIZE lpSize,
    LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>Parametry

*lpOffset*<br/>
Przesunięcie kursora myszy, kliknij w lewym górnym rogu elementu OLE. Może mieć wartości NULL.

*lpSize*<br/>
Rozmiar elementu OLE. Może mieć wartości NULL.

*lpStgMedium*<br/>
Wskaźnik do [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) strukturę, która będzie odbierać dane CF_OBJECTDESCRIPTOR dla elementu OLE.

### <a name="remarks"></a>Uwagi

Informacje są kopiowane do `STGMEDIUM` wskazywanej przez *lpStgMedium*. Ten format zawiera informacje potrzebne do okna dialogowego Wklej specjalne.

Aby uzyskać więcej informacji, zobacz [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) w zestawie Windows SDK.

##  <a name="isconnected"></a>  COleServerItem::IsConnected

Wywołaj tę funkcję, aby zobaczyć, czy jest połączony element OLE.

```
BOOL IsConnected() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli element jest połączona; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Element OLE, jest traktowany jako połączone, jeśli co najmniej jeden kontener odwołują się do elementu. Element jest połączony, jeśli jego licznik odwołań jest większa niż 0, lub jeśli jest element osadzony.

##  <a name="islinkeditem"></a>  COleServerItem::IsLinkedItem

Wywołaj tę funkcję, aby sprawdzić, czy element OLE jest połączony element.

```
BOOL IsLinkedItem() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli element jest połączony element; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Element jest połączony, jeśli element jest prawidłowa i nie jest zwracana w dokumentu listę elementów osadzonych. Połączony element może być lub może nie być połączony z kontenerem.

Jest to często używa się tej samej klasie elementy osadzone i połączone. `IsLinkedItem` Umożliwia zapewnienie połączone elementy będą działały inaczej niż elementów osadzonych, chociaż wiele razy kod jest często.

##  <a name="m_sizeextent"></a>  COleServerItem::m_sizeExtent

Ten element członkowski informuje serwer, jaka część obiektu jest widoczne w dokumencie kontenera.

```
CSize m_sizeExtent;
```

### <a name="remarks"></a>Uwagi

Domyślna implementacja klasy [OnSetExtent](#onsetextent) ustawia tego elementu członkowskiego.

##  <a name="notifychanged"></a>  COleServerItem::NotifyChanged

Wywołaj tę funkcję, po połączony element został zmieniony.

```
void NotifyChanged(DVASPECT nDrawAspect = DVASPECT_CONTENT);
```

### <a name="parameters"></a>Parametry

*nDrawAspect*<br/>
Zmieniona wartość z wyliczenia DVASPECT, która wskazuje, z którym aspektem elementu OLE. Ten parametr może mieć jedną z następujących wartości:

- Element DVASPECT_CONTENT jest reprezentowana w taki sposób, aby go mogą być wyświetlane jako osadzonego obiektu wewnątrz jej kontenera.

- DVASPECT_THUMBNAIL element jest renderowany w reprezentacji "miniaturę", więc, że mogą być wyświetlane w narzędziu do przeglądania.

- Element DVASPECT_ICON jest reprezentowany przez ikonę.

- Element DVASPECT_DOCPRINT jest reprezentowany tak, jakby były drukowane, za pomocą polecenia drukowania, za pomocą menu Plik.

### <a name="remarks"></a>Uwagi

Jeśli element kontenera jest połączony do dokumentu z łączem automatyczne, element zostanie zaktualizowany zgodnie ze zmianami. W aplikacjach kontenera napisane przy użyciu biblioteki klas Microsoft Foundation [COleClientItem::OnChange](../../mfc/reference/coleclientitem-class.md#onchange) jest wywoływana w odpowiedzi.

##  <a name="ondoverb"></a>  COleServerItem::OnDoVerb

Metoda wywoływana przez platformę, by wykonać określone zlecenie.

```
virtual void OnDoVerb(LONG iVerb);
```

### <a name="parameters"></a>Parametry

*iVerb*<br/>
Określa polecenie do wykonania. Może być dowolną z następujących czynności:

|Wartość|Znaczenie|Symbol|
|-----------|-------------|------------|
|0|Primary — Zlecenie|OLEIVERB_PRIMARY|
|1|Pomocniczy zlecenia|(Brak)|
|- 1|Wyświetlanie elementu do edycji|OLEIVERB_SHOW|
|- 2|Edytuj element w osobnym oknie|OLEIVERB_OPEN|
|- 3|Ukrywanie elementu|OLEIVERB_HIDE|

Wartość-1 zwykle jest aliasem dla innej zlecenie. Jeśli otwarty do edycji nie jest obsługiwany, -2 ma taki sam skutek jak -1. Aby uzyskać dodatkowe wartości, zobacz [IOleObject::DoVerb](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-doverb) w zestawie Windows SDK.

### <a name="remarks"></a>Uwagi

Jeśli aplikacja kontenera została napisana przy użyciu biblioteki klas Microsoft Foundation, ta funkcja jest wywoływana, gdy [COleClientItem::Activate](../../mfc/reference/coleclientitem-class.md#activate) funkcji składowej typu odpowiadającego `COleClientItem` nosi nazwę obiektu. Domyślna implementacja wywołuje [metodzie OnShow](#onshow) funkcja elementu członkowskiego, jeśli określono primary — zlecenie lub OLEIVERB_SHOW [zdarzenia](#onopen) Jeśli określono dodatkowej zlecenie lub OLEIVERB_OPEN i [OnHide ](#onhide) Jeśli OLEIVERB_HIDE jest określony. Domyślna implementacja wywołuje `OnShow` Jeśli *iVerb* nie jest jednym z poleceń wymienionych powyżej.

Należy przesłonić tę funkcję, jeśli Twoja primary — zlecenie nie pokazuje elementu. Na przykład jeśli element jest nagrywanie dźwięku i jego primary — zlecenie jest Play, nie trzeba do wyświetlenia aplikacji serwera, aby odtworzyć element.

Aby uzyskać więcej informacji, zobacz [IOleObject::DoVerb](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-doverb) w zestawie Windows SDK.

##  <a name="ondraw"></a>  COleServerItem::OnDraw

Metoda wywoływana przez platformę, by renderować element OLE w metaplik.

```
virtual BOOL OnDraw(
    CDC* pDC,
    CSize& rSize) = 0;
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
Wskaźnik do [CDC](../../mfc/reference/cdc-class.md) obiektu, na którym do rysowania elementu. Kontekst wyświetlania jest z nią automatycznie połączony kontekst wyświetlania atrybutu można więc wywoływać funkcje atrybutu, mimo że spowoduje to więc spowodowałoby metaplik specyficznych dla urządzenia.

*rSize*<br/>
Rozmiar w jednostkach HIMETRIC, w którym do rysowania metaplik.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli element został pomyślnie rysowana; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Metaplik reprezentacja elementu OLE służy do wyświetlania elementu w aplikacji kontenera. Jeśli aplikacja kontenera została napisana przy użyciu biblioteki klas Microsoft Foundation, metaplik jest używany przez [Rysowanie](../../mfc/reference/coleclientitem-class.md#draw) funkcji składowej typu odpowiadającego [COleClientItem](../../mfc/reference/coleclientitem-class.md) obiektu. Brak implementacji domyślnej. Należy przesłonić tę funkcję, aby rysować element w kontekście urządzenia określone.

##  <a name="ondrawex"></a>  COleServerItem::OnDrawEx

Wywoływane przez platformę, dla wszystkich rysowania.

```
virtual BOOL OnDrawEx(
    CDC* pDC,
    DVASPECT nDrawAspect,
    CSize& rSize);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
Wskaźnik do [CDC](../../mfc/reference/cdc-class.md) obiektu, na którym do rysowania elementu. Kontroler domeny jest z nią automatycznie połączony atrybutu kontrolera domeny można więc wywoływać funkcje atrybutu, mimo że spowoduje to więc spowodowałoby metaplik specyficznych dla urządzenia.

*nDrawAspect*<br/>
Wartość z wyliczenia DVASPECT. Ten parametr może mieć jedną z następujących wartości:

- Element DVASPECT_CONTENT jest reprezentowana w taki sposób, aby go mogą być wyświetlane jako osadzonego obiektu wewnątrz jej kontenera.

- DVASPECT_THUMBNAIL element jest renderowany w reprezentacji "miniaturę", więc, że mogą być wyświetlane w narzędziu do przeglądania.

- Element DVASPECT_ICON jest reprezentowany przez ikonę.

- Element DVASPECT_DOCPRINT jest reprezentowany tak, jakby były drukowane, za pomocą polecenia drukowania, za pomocą menu Plik.

*rSize*<br/>
Rozmiar elementu w jednostkach HIMETRIC.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli element został pomyślnie rysowana; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Domyślna implementacja wywołuje `OnDraw` DVASPECT jest równy DVASPECT_CONTENT; w przeciwnym razie jej nie powiedzie się.

Należy przesłonić tę funkcję, aby zapewnić prezentacji danych dla elementów innych niż DVASPECT_CONTENT, takie jak DVASPECT_ICON lub DVASPECT_THUMBNAIL.

##  <a name="ongetclipboarddata"></a>  COleServerItem::OnGetClipboardData

Wywoływane przez platformę, by pobrać `COleDataSource` obiekt, który zawiera wszystkie dane, które zostają umieszczone w Schowku przez wywołanie [CopyToClipboard](#copytoclipboard) funkcja elementu członkowskiego.

```
virtual COleDataSource* OnGetClipboardData(
    BOOL bIncludeLink,
    LPPOINT lpOffset,
    LPSIZE lpSize);
```

### <a name="parameters"></a>Parametry

*bIncludeLink*<br/>
Ustaw tę opcję na wartość TRUE, jeśli danych link powinien zostać skopiowany do Schowka. Ustaw tę pozycję na wartość FALSE, jeśli serwer aplikacji nie obsługuje łączy.

*lpOffset*<br/>
Przesunięcie kursora myszy ze źródła obiektu w pikselach.

*lpSize*<br/>
Rozmiar obiektu w pikselach.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do [COleDataSource](../../mfc/reference/coledatasource-class.md) obiekt zawierający dane Schowka.

### <a name="remarks"></a>Uwagi

Domyślna implementacja ta funkcja wywołuje [GetClipboardData](#getclipboarddata).

##  <a name="ongetextent"></a>  COleServerItem::OnGetExtent

Metoda wywoływana przez platformę, by pobrać rozmiar w jednostkach HIMETRIC elementu OLE.

```
virtual BOOL OnGetExtent(
    DVASPECT nDrawAspect,
    CSize& rSize);
```

### <a name="parameters"></a>Parametry

*nDrawAspect*<br/>
Określa aspekt elementu OLE, którego granice, które mają być pobierane. Ten parametr może mieć jedną z następujących wartości:

- Element DVASPECT_CONTENT jest reprezentowana w taki sposób, aby go mogą być wyświetlane jako osadzonego obiektu wewnątrz jej kontenera.

- DVASPECT_THUMBNAIL element jest renderowany w reprezentacji "miniaturę", więc, że mogą być wyświetlane w narzędziu do przeglądania.

- Element DVASPECT_ICON jest reprezentowany przez ikonę.

- Element DVASPECT_DOCPRINT jest reprezentowany tak, jakby były drukowane, za pomocą polecenia drukowania, za pomocą menu Plik.

*rSize*<br/>
Odwołanie do `CSize` obiekt, który zostanie wyświetlony rozmiar elementu OLE.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli aplikacja kontenera została napisana przy użyciu biblioteki klas Microsoft Foundation, ta funkcja jest wywoływana, gdy [GetExtent](../../mfc/reference/coleclientitem-class.md#getextent) funkcji składowej typu odpowiadającego `COleClientItem` nosi nazwę obiektu. Domyślna implementacja nic nie robi. Należy zaimplementować go samodzielnie. Należy przesłonić tę funkcję, jeśli chcesz wykonać przetwarzana w specjalny sposób podczas obsługi żądania rozmiar elementu OLE.

##  <a name="onhide"></a>  COleServerItem::OnHide

Metoda wywoływana przez platformę, by ukryć element OLE.

```
virtual void OnHide();
```

### <a name="remarks"></a>Uwagi

Wywołuje domyślną `COleServerDoc::OnShowDocument( FALSE )`. Funkcja powiadamia również kontenera elementów OLE zostało ukryte. Należy przesłonić tę funkcję, jeśli chcesz przeprowadzić specjalnego przetwarzania, ukrywając elementu OLE.

##  <a name="oninitfromdata"></a>  COleServerItem::OnInitFromData

Wywoływane przez platformę, by zainicjować element OLE przy użyciu zawartości *pDataObject*.

```
virtual BOOL OnInitFromData(
    COleDataObject* pDataObject,
    BOOL bCreation);
```

### <a name="parameters"></a>Parametry

*pDataObject*<br/>
Wskaźnik do obiektu danych OLE, zawierające dane w różnych formatach zainicjować element OLE.

*bCreation*<br/>
Wartość TRUE, jeśli funkcja jest wywoływana, aby zainicjować element OLE nowo tworzonego przez aplikację kontenera. Wartość FALSE, jeśli funkcja jest wywoływana, aby zastąpić zawartość istniejącego elementu OLE.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli *bCreation* ma wartość TRUE, ta funkcja jest wywoływana, gdy kontener implementuje wstawiania nowego obiektu na podstawie bieżącego zaznaczenia. Wybrane dane jest używane podczas tworzenia nowego elementu OLE. Na przykład podczas zaznaczania zakresu komórek w arkuszu kalkulacyjnym programu, a następnie używając Wstaw nowy obiekt do utworzenia wykresu na podstawie wartości w wybranym zakresie. Domyślna implementacja nic nie robi. Zastąp tę funkcję, aby wybierać akceptowalny format oferowane przez *pDataObject* i zainicjować element OLE na podstawie danych, pod warunkiem. Jest to zaawansowany możliwym do zastąpienia.

Aby uzyskać więcej informacji, zobacz [IOleObject::InitFromData](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-initfromdata) w zestawie Windows SDK.

##  <a name="onopen"></a>  COleServerItem::OnOpen

Metoda wywoływana przez platformę, by wyświetlić element OLE w oddzielnym wystąpieniu aplikacji serwera, a nie w miejscu.

```
virtual void OnOpen();
```

### <a name="remarks"></a>Uwagi

Domyślna implementacja aktywuje pierwszej ramki okna wyświetlania dokumentu, który zawiera element OLE; Jeśli aplikacja jest mini serwer domyślną implementację przedstawiono głównego okna. Funkcja powiadamia również kontenera otwarcia elementu OLE.

Należy przesłonić tę funkcję, jeśli chcesz wykonać przetwarzana w specjalny sposób podczas otwierania elementu OLE. Jest to szczególnie powszechne połączonych elementów, w której chcesz ustawić zaznaczenie łącza, po jego otwarciu.

Aby uzyskać więcej informacji, zobacz [IOleClientSite::OnShowWindow](/windows/desktop/api/oleidl/nf-oleidl-ioleclientsite-onshowwindow) w zestawie Windows SDK.

##  <a name="onqueryupdateitems"></a>  COleServerItem::OnQueryUpdateItems

Metoda wywoływana przez platformę, aby określić, czy którykolwiek z elementów powiązanych w bieżącym dokumencie serwera są nieaktualne.

```
virtual BOOL OnQueryUpdateItems();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli dokument ma elementy wymagające aktualizacji 0, jeśli wszystkie elementy są aktualne.

### <a name="remarks"></a>Uwagi

Element jest nieaktualna, jeśli jego dokumentu źródłowego został zmieniony, ale połączony element nie został zaktualizowany w celu odzwierciedlenia zmian w dokumencie.

##  <a name="onrenderdata"></a>  COleServerItem::OnRenderData

Metoda wywoływana przez platformę, by pobrać dane w określonym formacie.

```
virtual BOOL OnRenderData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>Parametry

*lpFormatEtc*<br/>
Wskazuje [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) Struktura określająca format, w którym wymagane informacje.

*lpStgMedium*<br/>
Wskazuje [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) struktury, w którym ma zostać zwrócone dane.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Podany format jest jednym wcześniej umieszczone w `COleDataSource` przy użyciu [DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata) lub [DelayRenderFileData](../../mfc/reference/coledatasource-class.md#delayrenderfiledata) funkcję członkowską opóźnione renderowanie. Domyślna implementacja ta funkcja wywołuje [OnRenderFileData](#onrenderfiledata) lub [OnRenderGlobalData](#onrenderglobaldata), odpowiednio, jeśli podany nośnik jest pliku lub pamięci. Jeśli żadna z tych formatów nie zostanie podany, domyślna implementacja zwraca wartość 0, a nic nie robi.

Jeśli *lpStgMedium*-> *tymed* jest TYMED_NULL, STGMEDIUM powinien przydzielony i wypełnione określony przez *lpFormatEtc -> tymed*. W przeciwnym razie TYMED_NULL, STGMEDIUM powinno być wypełnione w miejscu z danymi.

Jest to zaawansowany możliwym do zastąpienia. Należy przesłonić tę funkcję, aby podać dane w żądany format i średnie. W zależności od danych można zastąpić jedną z innych wersji tej funkcji, zamiast tego. W przypadku małych i stały rozmiar danych zastąpić `OnRenderGlobalData`. Jeśli Twoje dane znajduje się w pliku, lub o zmiennym rozmiarze, zastąpić `OnRenderFileData`.

Aby uzyskać więcej informacji, zobacz [Metoda IDataObject::GetData](/windows/desktop/api/objidl/nf-objidl-idataobject-getdata), [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium), [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc), i [TYMED](/windows/desktop/api/objidl/ne-objidl-tagtymed) w zestawie Windows SDK.

##  <a name="onrenderfiledata"></a>  COleServerItem::OnRenderFileData

Metoda wywoływana przez platformę, by pobrać dane w określonym formacie pliku po nośnika magazynowania.

```
virtual BOOL OnRenderFileData(
    LPFORMATETC lpFormatEtc,
    CFile* pFile);
```

### <a name="parameters"></a>Parametry

*lpFormatEtc*<br/>
Wskazuje [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) Struktura określająca format, w którym wymagane informacje.

*pFile*<br/>
Wskazuje `CFile` obiekt danych ma być renderowany.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Podany format jest jednym wcześniej umieszczone w `COleDataSource` przy użyciu [DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata) funkcję członkowską opóźnione renderowanie. Domyślna implementacja tej funkcji, po prostu zwraca wartość FALSE.

Jest to zaawansowany możliwym do zastąpienia. Należy przesłonić tę funkcję, aby podać dane w żądany format i średnie. W zależności od danych można zastąpić jedną z innych wersji tej funkcji, zamiast tego. Jeśli chcesz obsługiwać wiele nośników magazynowania, należy zastąpić [OnRenderData](#onrenderdata). Jeśli Twoje dane znajduje się w pliku, lub o zmiennym rozmiarze, zastąpić [OnRenderFileData](#onrenderfiledata).

Aby uzyskać więcej informacji, zobacz [Metoda IDataObject::GetData](/windows/desktop/api/objidl/nf-objidl-idataobject-getdata) i [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) w zestawie Windows SDK.

##  <a name="onrenderglobaldata"></a>  COleServerItem::OnRenderGlobalData

Metoda wywoływana przez platformę, by pobrać dane w określonym formacie po określonym nośniku pamięci globalnej.

```
virtual BOOL OnRenderGlobalData(
    LPFORMATETC lpFormatEtc,
    HGLOBAL* phGlobal);
```

### <a name="parameters"></a>Parametry

*lpFormatEtc*<br/>
Wskazuje [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) Struktura określająca format, w którym wymagane informacje.

*phGlobal*<br/>
Wskazuje dojścia do pamięci globalnej, w którym ma zostać zwrócone dane. Jeśli nie pamięć została przydzielona, ten parametr może być równa NULL.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Podany format jest jednym wcześniej umieszczone w `COleDataSource` przy użyciu [DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata) funkcję członkowską opóźnione renderowanie. Domyślna implementacja tej funkcji, po prostu zwraca wartość FALSE.

Jeśli *phGlobal* ma wartość NULL, a następnie nowe wartości HGLOBAL powinien być przydzielony i zwracane w *phGlobal*. W przeciwnym razie wartości HGLOBAL określony przez *phGlobal* powinno być wypełnione przy użyciu danych. Ilość danych, umieszczone w wartości HGLOBAL nie może przekraczać bieżący rozmiar bloku pamięci. Ponadto nie można ponownie przydzielane bloku, na większy rozmiar.

Jest to zaawansowany możliwym do zastąpienia. Należy przesłonić tę funkcję, aby podać dane w żądany format i średnie. W zależności od danych można zastąpić jedną z innych wersji tej funkcji, zamiast tego. Jeśli chcesz obsługiwać wiele nośników magazynowania, należy zastąpić [OnRenderData](#onrenderdata). Jeśli Twoje dane znajduje się w pliku, lub o zmiennym rozmiarze, zastąpić [OnRenderFileData](#onrenderfiledata).

Aby uzyskać więcej informacji, zobacz [Metoda IDataObject::GetData](/windows/desktop/api/objidl/nf-objidl-idataobject-getdata) i [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) w zestawie Windows SDK.

##  <a name="onsetcolorscheme"></a>  COleServerItem::OnSetColorScheme

Metoda wywoływana przez platformę, by określić paletę kolorów, które będą używane podczas edycji elementu OLE.

```
virtual BOOL OnSetColorScheme(const LOGPALETTE* lpLogPalette);
```

### <a name="parameters"></a>Parametry

*lpLogPalette*<br/>
Wskaźnik do Windows [LOGPALETTE](/windows/desktop/api/wingdi/ns-wingdi-taglogpalette) struktury.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli jest używany z palety kolorów; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli aplikacja kontenera została napisana przy użyciu biblioteki klas Microsoft Foundation, ta funkcja jest wywoływana, gdy [IOleObject::SetColorScheme](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-setcolorscheme) funkcja odpowiadającego `COleClientItem` nosi nazwę obiektu. Domyślna implementacja zwraca wartość FALSE. Należy przesłonić tę funkcję, jeśli chcesz używać zalecanych palety. Aplikacja serwera nie jest wymagana do użycia z sugerowanych palety.

Aby uzyskać więcej informacji, zobacz [IOleObject::SetColorScheme](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-setcolorscheme) w zestawie Windows SDK.

##  <a name="onsetdata"></a>  COleServerItem::OnSetData

Metoda wywoływana przez platformę, aby zastąpić element OLE danych z określonymi danymi.

```
virtual BOOL OnSetData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium,
    BOOL bRelease);
```

### <a name="parameters"></a>Parametry

*lpFormatEtc*<br/>
Wskaźnik do [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) struktury, określając format danych.

*lpStgMedium*<br/>
Wskaźnik do [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) struktury, w którym znajdują się dane.

*bRelease*<br/>
Wskazuje, kto jest właścicielem nośnika magazynowania po wykonaniu wywołania funkcji. Obiekt wywołujący decyduje o tym, kto jest odpowiedzialny za przy zwalnianiu zasobów przydzielonych w imieniu nośnika magazynowania. Obiekt wywołujący robi to poprzez ustawienie *bRelease*. Jeśli *bRelease* jest różna od zera, element serwera przejmuje, zwalniając nośnik, po zakończeniu korzystania z niego. Gdy *bRelease* jest 0, obiekt wywołujący zachowuje własność i element serwera przy użyciu nośnika magazynowania tylko na czas trwania wywołania.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Element serwera dopiero właściciela danych został pomyślnie uzyskał go. Oznacza to go nie przejęcie na własność Jeśli zwraca 0. Jeśli źródło danych przejmuje na własność, zwalnia nośnika magazynowania, wywołując [ReleaseStgMedium](/windows/desktop/api/ole2/nf-ole2-releasestgmedium) funkcji.

Domyślna implementacja nic nie robi. Należy przesłonić tę funkcję, aby zastąpić element OLE danych z określonymi danymi. Jest to zaawansowany możliwym do zastąpienia.

Aby uzyskać więcej informacji, zobacz [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium), [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc), i [ReleaseStgMedium](/windows/desktop/api/ole2/nf-ole2-releasestgmedium) w zestawie Windows SDK.

##  <a name="onsetextent"></a>  COleServerItem::OnSetExtent

Metoda wywoływana przez platformę, by przekazać elementowi OLE, ile miejsca jest dostępnych w dokumencie kontenera.

```
virtual BOOL OnSetExtent(
    DVASPECT nDrawAspect,
    const CSize& size);
```

### <a name="parameters"></a>Parametry

*nDrawAspect*<br/>
Określa aspekt podano którego granice elementu OLE. Ten parametr może mieć jedną z następujących wartości:

- Element DVASPECT_CONTENT jest reprezentowana w taki sposób, aby go mogą być wyświetlane jako osadzonego obiektu wewnątrz jej kontenera.

- DVASPECT_THUMBNAIL element jest renderowany w reprezentacji "miniaturę", więc, że mogą być wyświetlane w narzędziu do przeglądania.

- Element DVASPECT_ICON jest reprezentowany przez ikonę.

- Element DVASPECT_DOCPRINT jest reprezentowany tak, jakby były drukowane, za pomocą polecenia drukowania, za pomocą menu Plik.

*Rozmiar*<br/>
A [CSize](../../atl-mfc-shared/reference/csize-class.md) struktury, określając nowy rozmiar elementu OLE.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli aplikacja kontenera została napisana przy użyciu biblioteki klas Microsoft Foundation, ta funkcja jest wywoływana, gdy [SetExtent](../../mfc/reference/coleclientitem-class.md#setextent) funkcji składowej typu odpowiadającego `COleClientItem` nosi nazwę obiektu. Domyślne zestawy implementacji [m_sizeExtent](#m_sizeextent) elementu członkowskiego z określonym rozmiarem Jeśli *nDrawAspect* jest DVASPECT_CONTENT; w przeciwnym razie zwraca wartość 0. Należy przesłonić tę funkcję, aby wykonać specjalnego przetwarzania, gdy zmieniasz rozmiar elementu.

##  <a name="onshow"></a>  COleServerItem::OnShow

Metoda wywoływana przez platformę, aby nakazać aplikacji serwera, aby wyświetlić element OLE w miejscu.

```
virtual void OnShow();
```

### <a name="remarks"></a>Uwagi

Ta funkcja jest wywoływana zazwyczaj, gdy użytkownik aplikacji kontenera tworzy element lub wykonuje zlecenie, takie jak edytowanie, które wymaga element które mają być wyświetlane. Domyślna implementacja próby aktywacji w miejscu. Jeśli to się nie powiedzie, wywołania funkcji `OnOpen` funkcję elementu członkowskiego, aby wyświetlić element OLE w osobnym oknie.

Należy przesłonić tę funkcję, jeśli chcesz wykonać specjalnego przetwarzania, jeśli jest wyświetlany element OLE.

##  <a name="onupdate"></a>  COleServerItem::OnUpdate

Wywoływane przez platformę, gdy element został zmodyfikowany.

```
virtual void OnUpdate(
    COleServerItem* pSender,
    LPARAM lHint,
    CObject* pHint,
    DVASPECT nDrawAspect);
```

### <a name="parameters"></a>Parametry

*pSender*<br/>
Wskaźnik do elementu, który zmodyfikował dokument. Może mieć wartości NULL.

*lHint*<br/>
Zawiera informacje o modyfikacji.

*pHint*<br/>
Wskaźnik do przechowywania informacji o modyfikacji obiektu.

*nDrawAspect*<br/>
Wartość z wyliczenia DVASPECT. Ten parametr może mieć jeden z następujących wartości:

- Element DVASPECT_CONTENT jest reprezentowana w taki sposób, aby go mogą być wyświetlane jako osadzonego obiektu wewnątrz jej kontenera.

- DVASPECT_THUMBNAIL element jest renderowany w reprezentacji "miniaturę", więc, że mogą być wyświetlane w narzędziu do przeglądania.

- Element DVASPECT_ICON jest reprezentowany przez ikonę.

- Element DVASPECT_DOCPRINT jest reprezentowany tak, jakby były drukowane, za pomocą polecenia drukowania, za pomocą menu Plik.

### <a name="remarks"></a>Uwagi

Domyślna implementacja wywołuje [NotifyChanged](#notifychanged), niezależnie od tego, czy wskazówki lub nadawcy.

##  <a name="onupdateitems"></a>  COleServerItem::OnUpdateItems

Metoda wywoływana przez platformę, by uaktualnić wszystkie elementy w dokumencie serwera.

```
virtual void OnUpdateItems();
```

### <a name="remarks"></a>Uwagi

Domyślna implementacja wywołuje [UpdateLink](../../mfc/reference/coleclientitem-class.md#updatelink) dla wszystkich `COleClientItem` obiektów w dokumencie.

##  <a name="setitemname"></a>  COleServerItem::SetItemName

Wywołaj tę funkcję, podczas tworzenia połączonego elementu można ustawić jego nazwy.

```
void SetItemName(LPCTSTR lpszItemName);
```

### <a name="parameters"></a>Parametry

*lpszItemName*<br/>
Wskaźnik na nazwę nowego elementu.

### <a name="remarks"></a>Uwagi

Nazwa musi być unikatowa w obrębie dokumentu. Aplikacja serwera wywołanego do edycji połączony element aplikacja używa tej nazwy Aby znaleźć element. Nie musisz wywołać tę funkcję dla elementów osadzonych.

## <a name="see-also"></a>Zobacz także

[Próbki MFC HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[Klasa CDocItem](../../mfc/reference/cdocitem-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleClientItem](../../mfc/reference/coleclientitem-class.md)<br/>
[Klasa COleServerDoc](../../mfc/reference/coleserverdoc-class.md)<br/>
[Klasa COleTemplateServer](../../mfc/reference/coletemplateserver-class.md)
