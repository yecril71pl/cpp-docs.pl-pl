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
ms.openlocfilehash: dcae304e8571ecb5743002638ea23f13c3e21517
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79421087"
---
# <a name="coleserveritem-class"></a>Klasa COleServerItem

Udostępnia interfejs serwera do elementów OLE.

## <a name="syntax"></a>Składnia

```
class COleServerItem : public CDocItem
```

## <a name="members"></a>Members

### <a name="protected-constructors"></a>Konstruktory chronione

|Name (Nazwa)|Opis|
|----------|-----------------|
|[COleServerItem:: COleServerItem](#coleserveritem)|Konstruuje obiekt `COleServerItem`.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[COleServerItem:: AddOtherClipboardData](#addotherclipboarddata)|Umieszcza formaty prezentacji i konwersji w obiekcie `COleDataSource`.|
|[COleServerItem:: CopyToClipboard](#copytoclipboard)|Kopiuje element do Schowka.|
|[COleServerItem::D oDragDrop](#dodragdrop)|Wykonuje operację przeciągania i upuszczania.|
|[COleServerItem:: GetClipboardData](#getclipboarddata)|Pobiera źródło danych do użycia w transferze danych (przeciągnij i upuść lub Clipboard).|
|[COleServerItem:: GetDocument](#getdocument)|Zwraca dokument serwera, który zawiera element.|
|[COleServerItem:: GetEmbedSourceData](#getembedsourcedata)|Pobiera CF_EMBEDSOURCE dane dla elementu OLE.|
|[COleServerItem:: getitemname](#getitemname)|Zwraca nazwę elementu. Używany tylko do elementów połączonych.|
|[COleServerItem:: GetLinkSourceData](#getlinksourcedata)|Pobiera CF_LINKSOURCE dane dla elementu OLE.|
|[COleServerItem:: GetObjectDescriptorData](#getobjectdescriptordata)|Pobiera CF_OBJECTDESCRIPTOR dane dla elementu OLE.|
|[COleServerItem:: IsConnected](#isconnected)|Wskazuje, czy element jest obecnie dołączony do aktywnego kontenera.|
|[COleServerItem:: IsLinkedItem](#islinkeditem)|Wskazuje, czy element reprezentuje połączony element OLE.|
|[COleServerItem:: NotifyChanged](#notifychanged)|Aktualizuje wszystkie kontenery za pomocą automatycznej aktualizacji łącza.|
|[COleServerItem:: OnDoVerb](#ondoverb)|Wywołuje się, by wykonać czasownik.|
|[COleServerItem:: OnDraw](#ondraw)|Wywołuje się, gdy kontener przeprosi o narysowanie elementu; wymagana implementacja.|
|[COleServerItem:: przesłonięcie ondrawex](#ondrawex)|Wywołuje się, by uzyskać wyspecjalizowany rysunek elementu.|
|[COleServerItem:: OnGetClipboardData](#ongetclipboarddata)|Wywoływane przez platformę, aby pobrać dane, które zostaną skopiowane do Schowka.|
|[COleServerItem:: OnGetExtent](#ongetextent)|Wywoływane przez platformę, by pobrać rozmiar elementu OLE.|
|[COleServerItem:: OnInitFromData](#oninitfromdata)|Wywoływane przez platformę, by zainicjować element OLE przy użyciu zawartości określonego obiektu transferu danych.|
|[COleServerItem:: OnQueryUpdateItems](#onqueryupdateitems)|Wywołuje się, by określić, czy wszystkie elementy połączone wymagają aktualizacji.|
|[COleServerItem:: OnRenderData](#onrenderdata)|Pobiera dane w ramach opóźnionego renderowania.|
|[COleServerItem:: OnRenderFileData](#onrenderfiledata)|Pobiera dane do obiektu `CFile` w ramach opóźnionego renderowania.|
|[COleServerItem:: OnRenderGlobalData](#onrenderglobaldata)|Pobiera dane do HGLOBAL w ramach opóźnionego renderowania.|
|[COleServerItem:: OnSetColorScheme](#onsetcolorscheme)|Wywołuje się, by ustawić schemat kolorów elementu.|
|[COleServerItem:: OnSetData](#onsetdata)|Wywołuje się, by ustawić dane elementu.|
|[COleServerItem:: OnSetExtent](#onsetextent)|Wywoływane przez platformę, aby ustawić rozmiar elementu OLE.|
|[COleServerItem:: OnUpdate](#onupdate)|Wywoływana, gdy część dokumentu, w której znajduje się element, jest zmieniana.|
|[COleServerItem:: OnUpdateItems](#onupdateitems)|Wywołuje się, by zaktualizować pamięć podręczną prezentacji dla wszystkich elementów w dokumencie serwera.|
|[COleServerItem:: setitemname](#setitemname)|Ustawia nazwę elementu. Używany tylko do elementów połączonych.|

### <a name="protected-methods"></a>Metody chronione

|Name (Nazwa)|Opis|
|----------|-----------------|
|[COleServerItem:: GetDataSource](#getdatasource)|Pobiera obiekt używany do przechowywania formatów konwersji.|
|[COleServerItem:: OnHide](#onhide)|Wywoływane przez platformę, by ukryć element OLE.|
|[COleServerItem:: OnOpen](#onopen)|Wywoływane przez platformę, by wyświetlić element OLE w osobnym oknie najwyższego poziomu.|
|[COleServerItem:: OnShow](#onshow)|Wywoływana, gdy kontener żąda pokazywania elementu.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Name (Nazwa)|Opis|
|----------|-----------------|
|[COleServerItem:: m_sizeExtent](#m_sizeextent)|Informuje serwer o tym, ile elementów OLE jest widocznych.|

## <a name="remarks"></a>Uwagi

Połączony element może reprezentować niektóre lub wszystkie dokumenty serwera. Element osadzony zawsze reprezentuje cały dokument serwera.

Klasa `COleServerItem` definiuje kilka funkcji składowych, które są wywoływane przez dynamicznie dołączane biblioteki (dll) systemu OLE, zazwyczaj w odpowiedzi na żądania z aplikacji kontenera. Te funkcje Członkowskie umożliwiają aplikacji kontenera przetwarzać element pośrednio na różne sposoby, takie jak wyświetlanie, wykonywanie zleceń lub pobieranie danych w różnych formatach.

Aby użyć `COleServerItem`, należy utworzyć z niej klasę i zaimplementować [OnDraw](#ondraw) i [serializować](../../mfc/reference/cobject-class.md#serialize) funkcje składowe. Funkcja `OnDraw` zapewnia reprezentację elementu w postaci metapliku, co pozwala na jego wyświetlanie, gdy aplikacja kontenera otworzy dokument złożony. Funkcja `Serialize` `CObject` zapewnia natywną reprezentację elementu, umożliwiając przeniesienie elementu osadzonego między aplikacjami serwera i kontenera. [OnGetExtent](#ongetextent) zapewnia naturalny rozmiar elementu do kontenera, co umożliwia kontenerowi rozmiar elementu.

Aby uzyskać więcej informacji o serwerach i powiązanych tematach, zobacz artykuł [serwery: implementowanie serwera](../../mfc/servers-implementing-a-server.md) i "Tworzenie aplikacji kontenera/serwera" w [kontenerze artykułu: funkcje zaawansowane](../../mfc/containers-advanced-features.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

`COleServerItem`

## <a name="requirements"></a>Wymagania

**Nagłówek:** Afxole. h

##  <a name="addotherclipboarddata"></a>COleServerItem:: AddOtherClipboardData

Wywołaj tę funkcję, aby umieścić prezentacje i formaty konwersji dla elementu OLE w określonym obiekcie `COleDataSource`.

```
void AddOtherClipboardData(COleDataSource* pDataSource);
```

### <a name="parameters"></a>Parametry

*pDataSource*<br/>
Wskaźnik do obiektu `COleDataSource`, w którym należy umieścić dane.

### <a name="remarks"></a>Uwagi

Funkcja członkowska [OnDraw](#ondraw) musi być zaimplementowana w celu udostępnienia formatu prezentacji (obrazu metapliku) dla elementu. Aby obsługiwać inne formaty konwersji, należy zarejestrować je przy użyciu obiektu [by uzyskać COleDataSource](../../mfc/reference/coledatasource-class.md) zwróconego przez [GetDataSource](#getdatasource) i zastąpić funkcję członkowską [OnRenderData](#onrenderdata) w celu zapewnienia danych w formatach, które mają być obsługiwane.

##  <a name="coleserveritem"></a>COleServerItem:: COleServerItem

Konstruuje obiekt `COleServerItem` i dodaje go do kolekcji dokumentów dokumentu na serwerze.

```
COleServerItem(
    COleServerDoc* pServerDoc,
    BOOL bAutoDelete);
```

### <a name="parameters"></a>Parametry

*pServerDoc*<br/>
Wskaźnik do dokumentu, który będzie zawierać nowy element.

*bAutoDelete*<br/>
Flaga oznaczająca, czy obiekt może zostać usunięty po wydaniu linku do niego. Ustaw tę wartość na FALSE, jeśli obiekt `COleServerItem` jest integralną częścią danych dokumentu, które należy usunąć. Ustaw tę wartość na TRUE, jeśli obiekt jest strukturą pomocniczą służącą do identyfikowania zakresu w danych dokumentu, który może zostać usunięty przez platformę.

##  <a name="copytoclipboard"></a>COleServerItem:: CopyToClipboard

Wywołaj tę funkcję, aby skopiować element OLE do Schowka.

```
void CopyToClipboard(BOOL bIncludeLink = FALSE);
```

### <a name="parameters"></a>Parametry

*bIncludeLink*<br/>
Ustaw tę wartość na TRUE, jeśli dane łącza mają zostać skopiowane do Schowka. Ustaw tę wartość na FALSE, jeśli aplikacja serwera nie obsługuje linków.

### <a name="remarks"></a>Uwagi

Funkcja używa funkcji składowej [OnGetClipboardData](#ongetclipboarddata) do tworzenia obiektu [by uzyskać COleDataSource](../../mfc/reference/coledatasource-class.md) zawierającego dane elementu OLE w obsługiwanych formatach. Funkcja umieszcza obiekt `COleDataSource` w schowku przy użyciu funkcji [by uzyskać COleDataSource:: setClipboard](../../mfc/reference/coledatasource-class.md#setclipboard) . Obiekt `COleDataSource` zawiera dane natywne elementu i jego reprezentację w formacie CF_METAFILEPICT, a także dane we wszystkich formatach konwersji wybranych do obsługi. Aby ta funkcja członkowska działała, musisz mieć zaimplementowane funkcje [serializacji](../../mfc/reference/cobject-class.md#serialize) i [OnDraw](#ondraw) .

##  <a name="dodragdrop"></a>COleServerItem::D oDragDrop

Wywołaj funkcję elementu członkowskiego `DoDragDrop`, aby wykonać operację przeciągania i upuszczania.

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
Prostokąt elementu na ekranie (w pikselach) względem obszaru klienckiego.

*ptOffset*<br/>
Przesunięcie od *lpItemRect* , w którym położenie myszy było w czasie przeciągania.

*bIncludeLink*<br/>
Ustaw tę wartość na TRUE, jeśli dane łącza mają zostać skopiowane do Schowka. Ustaw wartość FALSE, jeśli aplikacja nie obsługuje linków.

*dwEffects*<br/>
Określa wpływ, przez który Źródło przeciągane będzie dozwolone w operacji przeciągania (kombinacji kopiowania, przenoszenia i łączenia).

*lpRectStartDrag*<br/>
Wskaźnik do prostokąta, który definiuje, gdzie w rzeczywistości zostanie rozpoczęte przeciąganie. Aby uzyskać więcej informacji zobacz następujące sekcji uwag.

### <a name="return-value"></a>Wartość zwrócona

Wartość z wyliczenia DROPEFFECT. W przypadku DROPEFFECT_MOVE należy usunąć oryginalne dane.

### <a name="remarks"></a>Uwagi

Operacja przeciągania i upuszczania nie rozpocznie się natychmiast. Czeka, aż kursor myszy opuści prostokąt określony przez *lpRectStartDrag* lub dopóki nie upłynie określona liczba milisekund. Jeśli *lpRectStartDrag* ma wartość null, używany jest prostokąt domyślny, aby przeciągać się, gdy wskaźnik myszy zostanie przesunięty o jeden piksel.

Czas opóźnienia jest określany przez ustawienie klucza rejestru. Można zmienić czas opóźnienia przez wywołanie [CWinApp:: WriteProfileString](../../mfc/reference/cwinapp-class.md#writeprofilestring) lub [CWinApp:: WriteProfileInt](../../mfc/reference/cwinapp-class.md#writeprofileint). Jeśli czas opóźnienia nie zostanie określony, zostanie użyta wartość domyślna 200 milisekund. Czas opóźnienia przeciągania jest przechowywany w następujący sposób:

- Czas opóźnienia przeciągania systemu Windows NT jest przechowywany w HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Windows\NT\CurrentVersion\IniFileMapping\win.ini\Windows\DragDelay.

- Czas opóźnienia przeciągania systemu Windows 3. x jest przechowywany w WIN. Plik INI, w sekcji [Windows}.

- Czas opóźnienia przeciągania systemu Windows 95/98 jest przechowywany w pamięci podręcznej w wersji zakupionej. Nośnika.

Aby uzyskać więcej informacji na temat sposobu przechowywania informacji o opóźnieniu przeciągania w rejestrze lub. Plik INI, zobacz [WriteProfileString](/windows/win32/api/winbase/nf-winbase-writeprofilestringw) w Windows SDK.

##  <a name="getclipboarddata"></a>COleServerItem:: GetClipboardData

Wywołaj tę funkcję, aby wypełnić określony obiekt [by uzyskać COleDataSource](../../mfc/reference/coledatasource-class.md) wszystkimi danymi, które zostałyby skopiowane do Schowka w przypadku wywołania [CopyToClipboard](#copytoclipboard) (te same dane byłyby transferowane także w przypadku wywołania [DoDragDrop](#dodragdrop)).

```
void GetClipboardData(
    COleDataSource* pDataSource,
    BOOL bIncludeLink = FALSE,
    LPPOINT lpOffset = NULL,
    LPSIZE lpSize = NULL);
```

### <a name="parameters"></a>Parametry

*pDataSource*<br/>
Wskaźnik do obiektu `COleDataSource`, który będzie otrzymywał dane elementu OLE we wszystkich obsługiwanych formatach.

*bIncludeLink*<br/>
Ma wartość TRUE, jeśli dane łącza mają zostać skopiowane do Schowka. FAŁSZ, jeśli aplikacja serwera nie obsługuje linków.

*lpOffset*<br/>
Przesunięcie (w pikselach) kursora myszy od początku obiektu.

*lpSize*<br/>
Rozmiar obiektu w pikselach.

### <a name="remarks"></a>Uwagi

Ta funkcja wywołuje funkcję elementu członkowskiego [GetEmbedSourceData](#getembedsourcedata) , aby uzyskać dane natywne dla elementu OLE i wywołuje funkcję członkowską [AddOtherClipboardData](#addotherclipboarddata) w celu pobrania formatu prezentacji i wszystkich obsługiwanych formatów konwersji. Jeśli *bIncludeLink* ma wartość true, funkcja wywołuje również [GetLinkSourceData](#getlinksourcedata) w celu pobrania danych linku dla elementu.

Zastąp tę funkcję, jeśli chcesz umieścić formaty w obiekcie `COleDataSource` przed lub po tych formatach dostarczonych przez `CopyToClipboard`.

##  <a name="getdatasource"></a>COleServerItem:: GetDataSource

Wywołaj tę funkcję, aby uzyskać obiekt [by uzyskać COleDataSource](../../mfc/reference/coledatasource-class.md) używany do przechowywania formatów konwersji obsługiwanych przez aplikację serwera.

```
COleDataSource* GetDataSource();
```

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do obiektu `COleDataSource` używany do przechowywania formatów konwersji.

### <a name="remarks"></a>Uwagi

Jeśli aplikacja serwera ma oferować dane w różnych formatach podczas operacji transferu danych, należy zarejestrować te formaty przy użyciu obiektu `COleDataSource` zwróconego przez tę funkcję. Na przykład, jeśli chcesz podać CF_TEXT reprezentację elementu OLE dla Schowka lub operacji przeciągania i upuszczania, należy zarejestrować format z obiektem `COleDataSource` ta funkcja zwraca, a następnie zastąpić funkcję elementu członkowskiego `OnRenderXxxData`, aby zapewnić dane.

##  <a name="getdocument"></a>COleServerItem:: GetDocument

Wywołaj tę funkcję, aby uzyskać wskaźnik do dokumentu zawierającego element.

```
COleServerDoc* GetDocument() const;
```

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do dokumentu zawierającego element; Wartość NULL, jeśli element nie jest częścią dokumentu.

### <a name="remarks"></a>Uwagi

Pozwala to na dostęp do dokumentu serwera, który został przesłany jako argument do konstruktora `COleServerItem`.

##  <a name="getembedsourcedata"></a>COleServerItem:: GetEmbedSourceData

Wywołaj tę funkcję, aby uzyskać CF_EMBEDSOURCE dane dla elementu OLE.

```
void GetEmbedSourceData(LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>Parametry

*lpStgMedium*<br/>
Wskaźnik do struktury [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) , która będzie odbierać CF_EMBEDSOURCE dane dla elementu OLE.

### <a name="remarks"></a>Uwagi

Ten format zawiera dane natywne elementu. Aby ta funkcja działała poprawnie, musi być zaimplementowana funkcja członkowska `Serialize`.

Następnie można dodać wynik do źródła danych przy użyciu [by uzyskać COleDataSource:: CacheData](../../mfc/reference/coledatasource-class.md#cachedata). Ta funkcja jest wywoływana automatycznie przez [COleServerItem:: OnGetClipboardData](#ongetclipboarddata).

Aby uzyskać więcej informacji, zobacz [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) w Windows SDK.

##  <a name="getitemname"></a>COleServerItem:: getitemname

Wywołaj tę funkcję, aby pobrać nazwę elementu.

```
const CString& GetItemName() const;
```

### <a name="return-value"></a>Wartość zwrócona

Nazwa elementu .

### <a name="remarks"></a>Uwagi

Ta funkcja jest zazwyczaj wywoływana tylko dla połączonych elementów.

##  <a name="getlinksourcedata"></a>COleServerItem:: GetLinkSourceData

Wywołaj tę funkcję, aby uzyskać CF_LINKSOURCE dane dla elementu OLE.

```
BOOL GetLinkSourceData(LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>Parametry

*lpStgMedium*<br/>
Wskaźnik do struktury [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) , która będzie odbierać CF_LINKSOURCE dane dla elementu OLE.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ten format obejmuje CLSID opisujące typ elementu OLE i informacje, które są konieczne do zlokalizowania dokumentu zawierającego element OLE.

Następnie można dodać wynik do źródła danych z [by uzyskać COleDataSource:: CacheData](../../mfc/reference/coledatasource-class.md#cachedata). Ta funkcja jest wywoływana automatycznie przez [OnGetClipboardData](#ongetclipboarddata).

Aby uzyskać więcej informacji, zobacz [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) w Windows SDK.

##  <a name="getobjectdescriptordata"></a>COleServerItem:: GetObjectDescriptorData

Wywołaj tę funkcję, aby uzyskać CF_OBJECTDESCRIPTOR dane dla elementu OLE.

```
void GetObjectDescriptorData(
    LPPOINT lpOffset,
    LPSIZE lpSize,
    LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>Parametry

*lpOffset*<br/>
Przesunięcie kliknięcia myszą w lewym górnym rogu elementu OLE. Może mieć wartość NULL.

*lpSize*<br/>
Rozmiar elementu OLE. Może mieć wartość NULL.

*lpStgMedium*<br/>
Wskaźnik do struktury [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) , która będzie odbierać CF_OBJECTDESCRIPTOR dane dla elementu OLE.

### <a name="remarks"></a>Uwagi

Informacje są kopiowane do struktury `STGMEDIUM` wskazywanej przez *lpStgMedium*. Ten format zawiera informacje, które są zbędne w oknie dialogowym wklejanie specjalne.

Aby uzyskać więcej informacji, zobacz [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) w Windows SDK.

##  <a name="isconnected"></a>COleServerItem:: IsConnected

Wywołaj tę funkcję, aby sprawdzić, czy element OLE jest połączony.

```
BOOL IsConnected() const;
```

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli element jest połączony; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Element OLE jest traktowany jako połączony, jeśli jeden lub więcej kontenerów zawiera odwołania do elementu. Element jest połączony, jeśli jego liczba odwołań jest większa niż 0 lub jeśli jest elementem osadzonym.

##  <a name="islinkeditem"></a>COleServerItem:: IsLinkedItem

Wywołaj tę funkcję, aby zobaczyć, czy element OLE jest elementem połączonym.

```
BOOL IsLinkedItem() const;
```

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli element jest elementem połączonym; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Element jest połączony, jeśli element jest prawidłowy i nie jest zwracany na liście elementów osadzonych dokumentu. Połączony element może lub nie może być połączony z kontenerem.

Często należy używać tej samej klasy dla elementów połączonych i osadzonych. `IsLinkedItem` pozwala tworzyć elementy połączone w sposób inny niż elementy osadzone, chociaż wiele razy jest powszechny kod.

##  <a name="m_sizeextent"></a>COleServerItem:: m_sizeExtent

Ten element członkowski informuje serwer o tym, ile z obiektów jest widocznych w dokumencie kontenera.

```
CSize m_sizeExtent;
```

### <a name="remarks"></a>Uwagi

Domyślna implementacja [OnSetExtent](#onsetextent) ustawia ten element członkowski.

##  <a name="notifychanged"></a>COleServerItem:: NotifyChanged

Wywołaj tę funkcję po zmianie połączonego elementu.

```
void NotifyChanged(DVASPECT nDrawAspect = DVASPECT_CONTENT);
```

### <a name="parameters"></a>Parametry

*nDrawAspect*<br/>
Wartość z wyliczenia DVASPECT, która wskazuje, który aspekt elementu OLE został zmieniony. Ten parametr może mieć jedną z następujących wartości:

- Element DVASPECT_CONTENT jest reprezentowany w taki sposób, że może być wyświetlany jako osadzony obiekt wewnątrz jego kontenera.

- Element DVASPECT_THUMBNAIL jest renderowany w reprezentacji "miniatury", dzięki czemu będzie można go wyświetlić w narzędziu do przeglądania.

- Element DVASPECT_ICON jest reprezentowany przez ikonę.

- Element DVASPECT_DOCPRINT jest reprezentowany tak, jakby był wydrukowany przy użyciu polecenia Drukuj z menu plik.

### <a name="remarks"></a>Uwagi

Jeśli element kontenera jest połączony z dokumentem z automatycznym łączem, element zostanie zaktualizowany w celu odzwierciedlenia zmian. W przypadku aplikacji kontenera pisanych przy użyciu biblioteka MFC [COleClientItem:: OnChange](../../mfc/reference/coleclientitem-class.md#onchange) jest wywoływana w odpowiedzi.

##  <a name="ondoverb"></a>COleServerItem:: OnDoVerb

Wywoływane przez platformę, by wykonać określone zlecenie.

```
virtual void OnDoVerb(LONG iVerb);
```

### <a name="parameters"></a>Parametry

*iVerb*<br/>
Określa zlecenie do wykonania. Może to być jeden z następujących:

|Wartość|Znaczenie|Symbol|
|-----------|-------------|------------|
|0|Primary — Zlecenie|OLEIVERB_PRIMARY|
|1|Zlecenie pomocnicze|(Brak)|
|- 1|Wyświetl element do edycji|OLEIVERB_SHOW|
|- 2|Edytuj element w osobnym oknie|OLEIVERB_OPEN|
|- 3|Ukryj element|OLEIVERB_HIDE|

Wartość-1 jest zwykle aliasem dla innego zlecenia. Jeśli Edycja Open nie jest obsługiwana, wartość-2 ma ten sam skutek co-1. Aby uzyskać dodatkowe wartości, zobacz [IOleObject::D overb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) w Windows SDK.

### <a name="remarks"></a>Uwagi

Jeśli aplikacja kontenera została zapisywana przy użyciu biblioteka MFC, ta funkcja jest wywoływana, gdy wywoływana jest funkcja członkowska [COleClientItem:: Activate](../../mfc/reference/coleclientitem-class.md#activate) odpowiedniego obiektu `COleClientItem`. Domyślna implementacja wywołuje funkcję elementu członkowskiego [OnShow](#onshow) , jeśli określono zlecenie podstawowe lub OLEIVERB_SHOW, [OnOpen](#onopen) , jeśli określono zlecenie pomocnicze lub OLEIVERB_OPEN, i [onhide](#onhide) , jeśli określono OLEIVERB_HIDE. Domyślne wywołania implementacji `OnShow`, jeśli *iVerb* nie jest jednym z czasowników wymienionych powyżej.

Przesłoń tę funkcję, jeśli zlecenie podstawowe nie wyświetla elementu. Na przykład jeśli element jest nagraniem dźwiękowym i jego podstawowe zlecenie jest odtwarzane, nie trzeba wyświetlać aplikacji serwerowej w celu odtwarzania elementu.

Aby uzyskać więcej informacji, zobacz [IOleObject::D overb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) w Windows SDK.

##  <a name="ondraw"></a>COleServerItem:: OnDraw

Wywoływane przez platformę, aby renderować element OLE w metaplik.

```
virtual BOOL OnDraw(
    CDC* pDC,
    CSize& rSize) = 0;
```

### <a name="parameters"></a>Parametry

*Domeny*<br/>
Wskaźnik do obiektu [przechwytywania](../../mfc/reference/cdc-class.md) , na którym ma zostać narysowany element. Kontekst wyświetlania jest automatycznie połączony z kontekstem wyświetlania atrybutów, aby można było wywoływać funkcje atrybutów, mimo że spowodowałoby to specyficzny dla urządzenia metaplik.

*Elementu rsize*<br/>
Rozmiar w jednostkach HIMETRIC, w którym ma zostać narysowany metaplik.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli element został pomyślnie narysowany; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Reprezentacja elementu OLE w postaci metapliku jest używana do wyświetlania elementu w aplikacji kontenera. Jeśli aplikacja kontenera została zapisywana przy użyciu biblioteka MFC, metaplik jest używany przez funkcję [rysowania](../../mfc/reference/coleclientitem-class.md#draw) elementu członkowskiego odpowiedniego obiektu [COleClientItem](../../mfc/reference/coleclientitem-class.md) . Nie istnieje domyślna implementacja. Należy zastąpić tę funkcję, aby narysować element w określonym kontekście urządzenia.

##  <a name="ondrawex"></a>COleServerItem:: przesłonięcie ondrawex

Wywoływane przez platformę dla całego rysunku.

```
virtual BOOL OnDrawEx(
    CDC* pDC,
    DVASPECT nDrawAspect,
    CSize& rSize);
```

### <a name="parameters"></a>Parametry

*Domeny*<br/>
Wskaźnik do obiektu [przechwytywania](../../mfc/reference/cdc-class.md) , na którym ma zostać narysowany element. Kontroler domeny jest automatycznie połączony z atrybutem DC, aby można było wywoływać funkcje atrybutów, mimo że spowodowałoby to specyficzny dla urządzenia metaplik.

*nDrawAspect*<br/>
Wartość z wyliczenia DVASPECT. Ten parametr może mieć jedną z następujących wartości:

- Element DVASPECT_CONTENT jest reprezentowany w taki sposób, że może być wyświetlany jako osadzony obiekt wewnątrz jego kontenera.

- Element DVASPECT_THUMBNAIL jest renderowany w reprezentacji "miniatury", dzięki czemu będzie można go wyświetlić w narzędziu do przeglądania.

- Element DVASPECT_ICON jest reprezentowany przez ikonę.

- Element DVASPECT_DOCPRINT jest reprezentowany tak, jakby był wydrukowany przy użyciu polecenia Drukuj z menu plik.

*Elementu rsize*<br/>
Rozmiar elementu w jednostkach HIMETRIC.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli element został pomyślnie narysowany; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Domyślne wywołania implementacji `OnDraw`, gdy DVASPECT jest równa DVASPECT_CONTENT; w przeciwnym razie kończy się niepowodzeniem.

Zastąp tę funkcję, aby udostępnić dane prezentacji dla aspektów innych niż DVASPECT_CONTENT, takich jak DVASPECT_ICON lub DVASPECT_THUMBNAIL.

##  <a name="ongetclipboarddata"></a>COleServerItem:: OnGetClipboardData

Wywoływane przez platformę, aby uzyskać `COleDataSource` obiekt zawierający wszystkie dane, które byłyby umieszczane w schowku przez wywołanie funkcji składowej [CopyToClipboard](#copytoclipboard) .

```
virtual COleDataSource* OnGetClipboardData(
    BOOL bIncludeLink,
    LPPOINT lpOffset,
    LPSIZE lpSize);
```

### <a name="parameters"></a>Parametry

*bIncludeLink*<br/>
Ustaw tę wartość na TRUE, jeśli dane łącza mają zostać skopiowane do Schowka. Ustaw tę wartość na FALSE, jeśli aplikacja serwera nie obsługuje linków.

*lpOffset*<br/>
Przesunięcie kursora myszy od początku obiektu w pikselach.

*lpSize*<br/>
Rozmiar obiektu w pikselach.

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do obiektu [by uzyskać COleDataSource](../../mfc/reference/coledatasource-class.md) zawierającego dane ze schowka.

### <a name="remarks"></a>Uwagi

Domyślna implementacja tej funkcji wywołuje [GetClipboardData](#getclipboarddata).

##  <a name="ongetextent"></a>COleServerItem:: OnGetExtent

Wywoływane przez platformę, by pobrać rozmiar (w jednostkach HIMETRIC) elementu OLE.

```
virtual BOOL OnGetExtent(
    DVASPECT nDrawAspect,
    CSize& rSize);
```

### <a name="parameters"></a>Parametry

*nDrawAspect*<br/>
Określa aspekt elementu OLE, którego granice mają zostać pobrane. Ten parametr może mieć jedną z następujących wartości:

- Element DVASPECT_CONTENT jest reprezentowany w taki sposób, że może być wyświetlany jako osadzony obiekt wewnątrz jego kontenera.

- Element DVASPECT_THUMBNAIL jest renderowany w reprezentacji "miniatury", dzięki czemu będzie można go wyświetlić w narzędziu do przeglądania.

- Element DVASPECT_ICON jest reprezentowany przez ikonę.

- Element DVASPECT_DOCPRINT jest reprezentowany tak, jakby był wydrukowany przy użyciu polecenia Drukuj z menu plik.

*Elementu rsize*<br/>
Odwołanie do obiektu `CSize`, który będzie otrzymywał rozmiar elementu OLE.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli aplikacja kontenera została zapisywana przy użyciu biblioteka MFC, ta funkcja jest wywoływana, gdy [wywoływana jest funkcja członkowska](../../mfc/reference/coleclientitem-class.md#getextent) elementu `COleClientItem` obiektu. Domyślna implementacja nie robi nic. Należy zaimplementować ją samodzielnie. Zastąp tę funkcję, jeśli chcesz przeprowadzić przetwarzanie specjalne podczas obsługi żądania rozmiaru elementu OLE.

##  <a name="onhide"></a>COleServerItem:: OnHide

Wywoływane przez platformę, by ukryć element OLE.

```
virtual void OnHide();
```

### <a name="remarks"></a>Uwagi

Domyślne wywołania `COleServerDoc::OnShowDocument( FALSE )`. Funkcja powiadamia również kontener, że element OLE został ukryty. Przesłoń tę funkcję, jeśli chcesz przeprowadzić przetwarzanie specjalne podczas ukrywania elementu OLE.

##  <a name="oninitfromdata"></a>COleServerItem:: OnInitFromData

Wywoływane przez platformę, by zainicjować element OLE przy użyciu zawartości *pDataObject*.

```
virtual BOOL OnInitFromData(
    COleDataObject* pDataObject,
    BOOL bCreation);
```

### <a name="parameters"></a>Parametry

*pDataObject*<br/>
Wskaźnik do obiektu danych OLE zawierającego dane w różnych formatach do inicjowania elementu OLE.

*bCreation*<br/>
Ma wartość TRUE, jeśli funkcja jest wywoływana w celu zainicjowania elementu OLE, który jest nowo utworzony przez aplikację kontenera. FAŁSZ, jeśli funkcja jest wywoływana, aby zastąpić zawartość już istniejącego elementu OLE.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli *bCreation* ma wartość true, ta funkcja jest wywoływana, jeśli kontener implementuje nowy obiekt w oparciu o bieżące zaznaczenie. Wybrane dane są używane podczas tworzenia nowego elementu OLE. Na przykład podczas wybierania zakresu komórek w programie arkusza kalkulacyjnego, a następnie przy użyciu Wstaw nowy obiekt do tworzenia wykresu na podstawie wartości z wybranego zakresu. Domyślna implementacja nie robi nic. Przesłoń tę funkcję, aby wybrać akceptowalny format od tych oferowanych przez *pDataObject* i ZAINICJOWAĆ element OLE na podstawie dostarczonych danych. Jest to zaawansowany możliwy do zaawansowania.

Aby uzyskać więcej informacji, zobacz [IOleObject:: InitFromData](/windows/win32/api/oleidl/nf-oleidl-ioleobject-initfromdata) w Windows SDK.

##  <a name="onopen"></a>COleServerItem:: OnOpen

Wywoływane przez platformę, by wyświetlić element OLE w osobnym wystąpieniu aplikacji serwera, a nie na miejscu.

```
virtual void OnOpen();
```

### <a name="remarks"></a>Uwagi

Domyślna implementacja uaktywnia pierwsze okno ramki zawierające dokument zawierający element OLE; Jeśli aplikacja jest serwerem mini, domyślna implementacja pokazuje okno główne. Funkcja powiadamia również kontener, że element OLE został otwarty.

Przesłoń tę funkcję, jeśli chcesz przeprowadzić przetwarzanie specjalne podczas otwierania elementu OLE. Jest to szczególnie typowe w przypadku elementów połączonych, w których wybór ma zostać ustawiony na link, gdy zostanie on otwarty.

Aby uzyskać więcej informacji, zobacz [IOleClientSite:: OnShowWindow](/windows/win32/api/oleidl/nf-oleidl-ioleclientsite-onshowwindow) w Windows SDK.

##  <a name="onqueryupdateitems"></a>COleServerItem:: OnQueryUpdateItems

Wywoływane przez platformę, aby określić, czy dowolne połączone elementy w bieżącym dokumencie serwera są nieaktualne.

```
virtual BOOL OnQueryUpdateItems();
```

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli dokument zawiera elementy wymagające aktualizacji; 0, jeśli wszystkie elementy są aktualne.

### <a name="remarks"></a>Uwagi

Element jest nieaktualny, jeśli jego dokument źródłowy został zmieniony, ale połączony element nie został zaktualizowany w celu odzwierciedlenia zmian w dokumencie.

##  <a name="onrenderdata"></a>COleServerItem:: OnRenderData

Wywoływane przez platformę, by pobrać dane w określonym formacie.

```
virtual BOOL OnRenderData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>Parametry

*lpFormatEtc*<br/>
Wskazuje strukturę [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) , określając format, w którym informacje są żądane.

*lpStgMedium*<br/>
Wskazuje strukturę [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) , w której mają zostać zwrócone dane.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Określony format jest jednym wcześniej umieszczonym w obiekcie `COleDataSource` przy użyciu funkcji składowej [DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata) lub [DelayRenderFileData](../../mfc/reference/coledatasource-class.md#delayrenderfiledata) na potrzeby opóźnionego renderowania. Domyślna implementacja tej funkcji wywołuje odpowiednio [OnRenderFileData](#onrenderfiledata) lub [OnRenderGlobalData](#onrenderglobaldata), jeśli dostarczony nośnik magazynu jest plikiem lub pamięcią. Jeśli żaden z tych formatów nie zostanie podany, domyślna implementacja zwróci wartość 0 i nic nie robi.

Jeśli *lpStgMedium*-> *TYMED* jest TYMED_NULL, STGMEDIUM powinny być przydzielone i wypełniane jako określone przez *lpFormatEtc-> TYMED*. Jeśli nie TYMED_NULL, STGMEDIUM powinny być wypełnione danymi.

Jest to zaawansowany możliwy do zaawansowania. Zastąp tę funkcję, aby zapewnić dane w żądanym formacie i średnim. W zależności od danych warto zamiast tego zastąpić jedną z innych wersji tej funkcji. Jeśli dane są niewielkie i mają stały rozmiar, Zastąp `OnRenderGlobalData`. Jeśli dane są w pliku lub mają zmienny rozmiar, Przesłoń `OnRenderFileData`.

Aby uzyskać więcej informacji, zobacz [IDataObject:: GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata), [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1), [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)i [TYMED](/windows/win32/api/objidl/ne-objidl-tymed) w Windows SDK.

##  <a name="onrenderfiledata"></a>COleServerItem:: OnRenderFileData

Wywoływane przez platformę, by pobrać dane w określonym formacie, gdy nośnik magazynu jest plikiem.

```
virtual BOOL OnRenderFileData(
    LPFORMATETC lpFormatEtc,
    CFile* pFile);
```

### <a name="parameters"></a>Parametry

*lpFormatEtc*<br/>
Wskazuje strukturę [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) , określając format, w którym informacje są żądane.

*pFile*<br/>
Wskazuje obiekt `CFile`, w którym mają być renderowane dane.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Określony format jest jednym wcześniej umieszczonym w obiekcie `COleDataSource` przy użyciu funkcji składowej [DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata) do opóźnionego renderowania. Domyślna implementacja tej funkcji po prostu zwraca wartość FALSE.

Jest to zaawansowany możliwy do zaawansowania. Zastąp tę funkcję, aby zapewnić dane w żądanym formacie i średnim. W zależności od danych warto zamiast tego zastąpić jedną z innych wersji tej funkcji. Jeśli chcesz obsłużyć wiele nośników magazynowania, Zastąp [OnRenderData](#onrenderdata). Jeśli dane są w pliku lub mają zmienny rozmiar, Przesłoń [OnRenderFileData](#onrenderfiledata).

Aby uzyskać więcej informacji, zobacz [IDataObject:: GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) i [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) w Windows SDK.

##  <a name="onrenderglobaldata"></a>COleServerItem:: OnRenderGlobalData

Wywoływane przez platformę, aby pobrać dane w określonym formacie, gdy określony nośnik magazynu ma pamięć globalną.

```
virtual BOOL OnRenderGlobalData(
    LPFORMATETC lpFormatEtc,
    HGLOBAL* phGlobal);
```

### <a name="parameters"></a>Parametry

*lpFormatEtc*<br/>
Wskazuje strukturę [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) , określając format, w którym informacje są żądane.

*phGlobal*<br/>
Wskazuje dojście do pamięci globalnej, w której mają zostać zwrócone dane. Jeśli żadna pamięć nie została przypisana, ten parametr może mieć wartość NULL.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Określony format jest jednym wcześniej umieszczonym w obiekcie `COleDataSource` przy użyciu funkcji składowej [DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata) do opóźnionego renderowania. Domyślna implementacja tej funkcji po prostu zwraca wartość FALSE.

Jeśli *phGlobal* ma wartość null, należy alokować i zwrócić nową HGLOBAL w *phGlobal*. W przeciwnym razie HGLOBAL określona przez *phGlobal* powinna być wypełniony danymi. Ilość danych umieszczonych w HGLOBAL nie może przekraczać bieżącego rozmiaru bloku pamięci. Ponadto nie można zmienić przydziału bloku na większy rozmiar.

Jest to zaawansowany możliwy do zaawansowania. Zastąp tę funkcję, aby zapewnić dane w żądanym formacie i średnim. W zależności od danych warto zamiast tego zastąpić jedną z innych wersji tej funkcji. Jeśli chcesz obsłużyć wiele nośników magazynowania, Zastąp [OnRenderData](#onrenderdata). Jeśli dane są w pliku lub mają zmienny rozmiar, Przesłoń [OnRenderFileData](#onrenderfiledata).

Aby uzyskać więcej informacji, zobacz [IDataObject:: GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) i [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) w Windows SDK.

##  <a name="onsetcolorscheme"></a>COleServerItem:: OnSetColorScheme

Wywoływane przez platformę, by określić paletę kolorów, która będzie używana podczas edytowania elementu OLE.

```
virtual BOOL OnSetColorScheme(const LOGPALETTE* lpLogPalette);
```

### <a name="parameters"></a>Parametry

*lpLogPalette*<br/>
Wskaźnik do struktury [LOGPALETTE](/windows/win32/api/wingdi/ns-wingdi-logpalette) systemu Windows.

### <a name="return-value"></a>Wartość zwrócona

Różne od zera, jeśli jest używana paleta kolorów; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli aplikacja kontenera została zapisywana przy użyciu biblioteka MFC, ta funkcja jest wywoływana, gdy wywoływana jest funkcja [IOleObject:: SetColorScheme](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setcolorscheme) odpowiadającego obiektu `COleClientItem`. Domyślna implementacja zwraca wartość FALSE. Zastąp tę funkcję, jeśli chcesz użyć zalecanej palety. Aplikacja serwera nie jest wymagana do korzystania z sugerowanej palety.

Aby uzyskać więcej informacji, zobacz [IOleObject:: SetColorScheme](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setcolorscheme) w Windows SDK.

##  <a name="onsetdata"></a>COleServerItem:: OnSetData

Wywoływane przez platformę, aby zastąpić dane elementu OLE określonymi danymi.

```
virtual BOOL OnSetData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium,
    BOOL bRelease);
```

### <a name="parameters"></a>Parametry

*lpFormatEtc*<br/>
Wskaźnik do struktury [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) , który określa format danych.

*lpStgMedium*<br/>
Wskaźnik do struktury [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) , w której znajdują się dane.

*bRelease*<br/>
Wskazuje, kto ma własność nośnika magazynu po zakończeniu wywołania funkcji. Obiekt wywołujący decyduje, kto jest odpowiedzialny za wydanie zasobów przyznanych w imieniu nośnika magazynu. Obiekt wywołujący robi to przez ustawienie *bRelease*. Jeśli *bRelease* jest różna od zera, element serwera przejmuje własność, zwalniając nośnik po zakończeniu jego używania. Gdy *bRelease* jest równa 0, obiekt wywołujący zachowuje własność, a element serwera może korzystać z nośnika magazynu tylko w czasie trwania wywołania.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Element serwera nie przejmuje własności danych do momentu jego pomyślnego uzyskania. Oznacza to, że nie przyjmuje własności, jeśli zwróci wartość 0. Jeśli źródło danych przejmuje własność, zwalnia nośnik magazynu przez wywołanie funkcji [ReleaseStgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium) .

Domyślna implementacja nie robi nic. Zastąp tę funkcję, aby zastąpić dane elementu OLE określonymi danymi. Jest to zaawansowany możliwy do zaawansowania.

Aby uzyskać więcej informacji, zobacz [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1), [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)i [ReleaseStgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium) w Windows SDK.

##  <a name="onsetextent"></a>COleServerItem:: OnSetExtent

Wywoływane przez platformę w celu poinformowania elementu OLE o ile miejsca jest dostępne w dokumencie kontenera.

```
virtual BOOL OnSetExtent(
    DVASPECT nDrawAspect,
    const CSize& size);
```

### <a name="parameters"></a>Parametry

*nDrawAspect*<br/>
Określa aspekt elementu OLE, którego granice są określone. Ten parametr może mieć jedną z następujących wartości:

- Element DVASPECT_CONTENT jest reprezentowany w taki sposób, że może być wyświetlany jako osadzony obiekt wewnątrz jego kontenera.

- Element DVASPECT_THUMBNAIL jest renderowany w reprezentacji "miniatury", dzięki czemu będzie można go wyświetlić w narzędziu do przeglądania.

- Element DVASPECT_ICON jest reprezentowany przez ikonę.

- Element DVASPECT_DOCPRINT jest reprezentowany tak, jakby był wydrukowany przy użyciu polecenia Drukuj z menu plik.

*zmienia*<br/>
Struktura [CSizea](../../atl-mfc-shared/reference/csize-class.md) określająca nowy rozmiar elementu OLE.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli aplikacja kontenera została zapisywana przy użyciu biblioteka MFC, ta funkcja jest wywoływana, gdy [wywoływana jest funkcja członkowska](../../mfc/reference/coleclientitem-class.md#setextent) elementu `COleClientItem` obiektu. Domyślna implementacja ustawia element członkowski [m_sizeExtent](#m_sizeextent) na określony rozmiar, jeśli *nDrawAspect* jest DVASPECT_CONTENT; w przeciwnym razie zwraca wartość 0. Przesłoń tę funkcję, aby przeprowadzić przetwarzanie specjalne w przypadku zmiany rozmiaru elementu.

##  <a name="onshow"></a>COleServerItem:: OnShow

Wywoływane przez platformę, by nakazać aplikacji serwera wyświetlanie elementu OLE w miejscu.

```
virtual void OnShow();
```

### <a name="remarks"></a>Uwagi

Ta funkcja jest zazwyczaj wywoływana, gdy użytkownik aplikacji kontenera tworzy element lub wykonuje zlecenie, takie jak Edit, które wymaga wyświetlenia elementu. Domyślna implementacja aktywacji w miejscu. Jeśli to się nie powiedzie, funkcja wywołuje funkcję elementu członkowskiego `OnOpen`, aby wyświetlić element OLE w osobnym oknie.

Zastąp tę funkcję, jeśli chcesz przeprowadzić przetwarzanie specjalne w przypadku wyświetlenia elementu OLE.

##  <a name="onupdate"></a>COleServerItem:: OnUpdate

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
Wskaźnik do elementu, który zmodyfikował dokument. Może mieć wartość NULL.

*lHint*<br/>
Zawiera informacje na temat modyfikacji.

*pHint*<br/>
Wskaźnik do obiektu przechowującego informacje o modyfikacji.

*nDrawAspect*<br/>
Wartość z wyliczenia DVASPECT. Ten parametr może mieć jedną z następujących wartości:

- Element DVASPECT_CONTENT jest reprezentowany w taki sposób, że może być wyświetlany jako osadzony obiekt wewnątrz jego kontenera.

- Element DVASPECT_THUMBNAIL jest renderowany w reprezentacji "miniatury", dzięki czemu będzie można go wyświetlić w narzędziu do przeglądania.

- Element DVASPECT_ICON jest reprezentowany przez ikonę.

- Element DVASPECT_DOCPRINT jest reprezentowany tak, jakby był wydrukowany przy użyciu polecenia Drukuj z menu plik.

### <a name="remarks"></a>Uwagi

Domyślne wywołania implementacji [NotifyChanged](#notifychanged), niezależnie od wskazówki lub nadawcy.

##  <a name="onupdateitems"></a>COleServerItem:: OnUpdateItems

Wywoływane przez platformę, by zaktualizować wszystkie elementy w dokumencie serwera.

```
virtual void OnUpdateItems();
```

### <a name="remarks"></a>Uwagi

Domyślna implementacja wywołań [UpdateLink](../../mfc/reference/coleclientitem-class.md#updatelink) dla wszystkich obiektów `COleClientItem` w dokumencie.

##  <a name="setitemname"></a>COleServerItem:: setitemname

Wywołaj tę funkcję podczas tworzenia połączonego elementu, aby ustawić jego nazwę.

```
void SetItemName(LPCTSTR lpszItemName);
```

### <a name="parameters"></a>Parametry

*lpszItemName*<br/>
Wskaźnik na nową nazwę elementu.

### <a name="remarks"></a>Uwagi

Nazwa musi być unikatowa w obrębie dokumentu. Gdy aplikacja serwera jest wywoływana w celu edytowania elementu połączonego, aplikacja używa tej nazwy do znajdowania elementu. Nie trzeba wywoływać tej funkcji dla elementów osadzonych.

## <a name="see-also"></a>Zobacz też

[Przykład HIERSVR MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CDocItem](../../mfc/reference/cdocitem-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleClientItem](../../mfc/reference/coleclientitem-class.md)<br/>
[Klasa COleServerDoc](../../mfc/reference/coleserverdoc-class.md)<br/>
[Klasa COleTemplateServer](../../mfc/reference/coletemplateserver-class.md)
