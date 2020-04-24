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
ms.openlocfilehash: bdb91168a7c0ae718ca7d7514448b55965186aa8
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753741"
---
# <a name="coleserveritem-class"></a>Klasa COleServerItem

Udostępnia interfejs serwera do elementów OLE.

## <a name="syntax"></a>Składnia

```
class COleServerItem : public CDocItem
```

## <a name="members"></a>Elementy członkowskie

### <a name="protected-constructors"></a>Konstruktory chronione

|Nazwa|Opis|
|----------|-----------------|
|[COleServerItem::COleServerItem](#coleserveritem)|Konstruuje `COleServerItem` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleServerItem::AddOtherClipboardData](#addotherclipboarddata)|Umieszcza formaty prezentacji i `COleDataSource` konwersji w obiekcie.|
|[COleServerItem::CopyToClipboard](#copytoclipboard)|Kopiuje element do Schowka.|
|[COleServerItem::DoDragDrop](#dodragdrop)|Wykonuje operację przeciągania i upuszczania.|
|[COleServerItem::GetClipboardData](#getclipboarddata)|Pobiera źródło danych do użycia w transferze danych (przeciąganie i upuszczanie lub Schowek).|
|[COleServerItem::GetDocument](#getdocument)|Zwraca dokument serwera zawierający element.|
|[COleServerItem::GetEmbedSourceData](#getembedsourcedata)|Pobiera dane CF_EMBEDSOURCE dla elementu OLE.|
|[COleServerItem::GetItemName](#getitemname)|Zwraca nazwę towaru. Używany tylko dla połączonych elementów.|
|[COleServerItem::GetLinkSourceData](#getlinksourcedata)|Pobiera dane CF_LINKSOURCE dla elementu OLE.|
|[COleServerItem::GetObjectDescriptorData](#getobjectdescriptordata)|Pobiera dane CF_OBJECTDESCRIPTOR dla elementu OLE.|
|[COleServerItem::IsConnected](#isconnected)|Wskazuje, czy element jest obecnie dołączony do aktywnego kontenera.|
|[COleServerItem::IsLinkedItem](#islinkeditem)|Wskazuje, czy element reprezentuje połączony element OLE.|
|[COleServerItem::NotifyZmieniony](#notifychanged)|Aktualizuje wszystkie kontenery za pomocą automatycznej aktualizacji łącza.|
|[COleServerItem::OnDoVerb](#ondoverb)|Wywoływany do wykonania zlecenia.|
|[COleServerItem::OnDraw](#ondraw)|Wywoływane, gdy kontener żąda narysować element; wymaganego wdrożenia.|
|[COleServerItem::OnDrawEx](#ondrawex)|Powołany do specjalistycznego rysunku przedmiotu.|
|[COleServerItem::OnGetClipboardData](#ongetclipboarddata)|Wywoływane przez strukturę, aby uzyskać dane, które zostaną skopiowane do Schowka.|
|[COleServerItem::OnGetExtent](#ongetextent)|Wywoływane przez strukturę, aby pobrać rozmiar elementu OLE.|
|[COleServerItem::OnInitFromData](#oninitfromdata)|Wywoływana przez strukturę do inicjowania elementu OLE przy użyciu zawartości określonego obiektu transferu danych.|
|[COleServerItem::OnQueryUpdateItems](#onqueryupdateitems)|Wywoływana w celu ustalenia, czy wszystkie połączone elementy wymagają aktualizacji.|
|[COleServerItem::OnRenderData](#onrenderdata)|Pobiera dane w ramach opóźnionego renderowania.|
|[COleServerItem::OnRenderFileData](#onrenderfiledata)|Pobiera dane do `CFile` obiektu w ramach opóźnionego renderowania.|
|[COleServerItem::OnRenderGlobalData](#onrenderglobaldata)|Pobiera dane do HGLOBAL w ramach opóźnionego renderowania.|
|[COleServerItem::OnSetColorScheme](#onsetcolorscheme)|Wywoływana w celu skonfigurowania schematu kolorów elementu.|
|[COleServerItem::OnSetData](#onsetdata)|Wywoływana w celu skonfigurowania danych elementu.|
|[COleServerItem::OnSetExtent](#onsetextent)|Wywoływane przez strukturę, aby ustawić rozmiar elementu OLE.|
|[COleServerItem::OnUpdate](#onupdate)|Wywoływana, gdy część dokumentu, do którego należy element, jest zmieniana.|
|[COleServerItem::OnUpdateItems](#onupdateitems)|Wywoływany, aby zaktualizować pamięć podręczną prezentacji wszystkich elementów w dokumencie serwera.|
|[COleServerItem::Nazwa zestawu](#setitemname)|Ustawia nazwę elementu. Używany tylko dla połączonych elementów.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[COleServerItem::GetDataSource](#getdatasource)|Pobiera obiekt używany do przechowywania formatów konwersji.|
|[COleServerItem::OnHide](#onhide)|Wywoływane przez strukturę, aby ukryć element OLE.|
|[COleServerItem::OnOpen](#onopen)|Wywoływane przez strukturę do wyświetlania elementu OLE w swoim własnym oknie najwyższego poziomu.|
|[COleServerItem::OnShow](#onshow)|Wywoływane, gdy kontener żąda wyświetlenia elementu.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[COleServerItem::m_sizeExtent](#m_sizeextent)|Informuje serwer o tym, jaka część elementu OLE jest widoczna.|

## <a name="remarks"></a>Uwagi

Połączony element może reprezentować część lub całość dokumentu serwera. Element osadzony zawsze reprezentuje cały dokument serwera.

Klasa `COleServerItem` definiuje kilka zastępowalnych funkcji elementów członkowskich, które są wywoływane przez biblioteki dynamiczne łącza ole (biblioteki DLL), zwykle w odpowiedzi na żądania z aplikacji kontenera. Te funkcje członkowskie umożliwiają aplikacji kontenera do manipulowania element pośrednio na różne sposoby, takie jak przez wyświetlanie go, wykonywanie jego zleceń lub pobieranie jego danych w różnych formatach.

Aby `COleServerItem`użyć , wyprowadzić klasę z niego i zaimplementować [OnDraw](#ondraw) i [Serialize](../../mfc/reference/cobject-class.md#serialize) funkcji członkowskich. Funkcja `OnDraw` zapewnia metaplik reprezentację elementu, umożliwiając wyświetlanie go, gdy aplikacja kontenera otwiera dokument złożony. Funkcja `Serialize` `CObject` zapewnia natywną reprezentację elementu, umożliwiając osadzony element do przeniesienia między serwerem i aplikacjami kontenera. [OnGetExtent](#ongetextent) zapewnia naturalny rozmiar elementu do kontenera, umożliwiając kontener do rozmiaru elementu.

Aby uzyskać więcej informacji na temat serwerów i powiązanych tematów, zobacz artykuł [Serwery: Implementowanie serwera](../../mfc/servers-implementing-a-server.md) i "Tworzenie aplikacji kontenera/serwera" w artykule [Kontenery: Funkcje zaawansowane](../../mfc/containers-advanced-features.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cdocitem](../../mfc/reference/cdocitem-class.md)

`COleServerItem`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxole.h

## <a name="coleserveritemaddotherclipboarddata"></a><a name="addotherclipboarddata"></a>COleServerItem::AddOtherClipboardData

Wywołanie tej funkcji, aby umieścić formaty prezentacji i `COleDataSource` konwersji dla elementu OLE w określonym obiekcie.

```cpp
void AddOtherClipboardData(COleDataSource* pDataSource);
```

### <a name="parameters"></a>Parametry

*pDataSource (źródło danych)*<br/>
Wskaźnik do `COleDataSource` obiektu, w którym dane powinny być umieszczone.

### <a name="remarks"></a>Uwagi

Aby zapewnić format prezentacji (obraz metapliku) elementu, należy zaimplementować funkcję elementu członkowskiego [OnDraw.](#ondraw) Aby obsługiwać inne formaty konwersji, zarejestruj je przy użyciu [obiektu COleDataSource](../../mfc/reference/coledatasource-class.md) zwróconego przez [GetDataSource](#getdatasource) i zastąpij funkcję elementu członkowskiego [OnRenderData,](#onrenderdata) aby zapewnić dane w formatach, które chcesz obsługiwać.

## <a name="coleserveritemcoleserveritem"></a><a name="coleserveritem"></a>COleServerItem::COleServerItem

Konstruuje `COleServerItem` obiekt i dodaje go do kolekcji elementów dokumentu dokumentu serwera.

```
COleServerItem(
    COleServerDoc* pServerDoc,
    BOOL bAutoDelete);
```

### <a name="parameters"></a>Parametry

*pServerDoc (100)*<br/>
Wskaźnik do dokumentu, który będzie zawierał nowy element.

*bAutoDelete*<br/>
Flaga wskazująca, czy obiekt może zostać usunięty po zwolnieniu łącza do niego. Ustaw wartość FAŁSZ, `COleServerItem` jeśli obiekt jest integralną częścią danych dokumentu, które należy usunąć. Ustaw wartość TRUE, jeśli obiekt jest strukturą pomocniczą używaną do identyfikowania zakresu w danych dokumentu, który może zostać usunięty przez platformę.

## <a name="coleserveritemcopytoclipboard"></a><a name="copytoclipboard"></a>COleServerItem::CopyToClipboard

Wywołanie tej funkcji, aby skopiować element OLE do Schowka.

```cpp
void CopyToClipboard(BOOL bIncludeLink = FALSE);
```

### <a name="parameters"></a>Parametry

*bIncludeLink*<br/>
Ustaw wartość TRUE, jeśli dane łącza mają zostać skopiowane do Schowka. Ustaw to na FALSE, jeśli aplikacja serwera nie obsługuje łączy.

### <a name="remarks"></a>Uwagi

Funkcja używa [OnGetClipboardData](#ongetclipboarddata) funkcji elementu członkowskiego do [utworzenia COleDataSource](../../mfc/reference/coledatasource-class.md) obiektu zawierającego dane elementu OLE w obsługiwanych formatach. Funkcja następnie umieszcza `COleDataSource` obiekt w Schowku za pomocą [funkcji COleDataSource::SetClipboard.](../../mfc/reference/coledatasource-class.md#setclipboard) Obiekt `COleDataSource` zawiera dane natywne elementu i jego reprezentację w formacie CF_METAFILEPICT, a także dane w dowolnych formatach konwersji, które chcesz obsługiwać. Musisz zaimplementować [Serialize](../../mfc/reference/cobject-class.md#serialize) i [OnDraw](#ondraw) dla tej funkcji elementu członkowskiego do pracy.

## <a name="coleserveritemdodragdrop"></a><a name="dodragdrop"></a>COleServerItem::DoDragDrop

Wywołanie `DoDragDrop` funkcji elementu członkowskiego, aby wykonać operację przeciągania i upuszczania.

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
Prostokąt elementu na ekranie, w pikselach, względem obszaru klienta.

*ptOffset (polski)*<br/>
Przesunięcie z *lpItemRect* gdzie pozycja myszy był w czasie przeciągania.

*bIncludeLink*<br/>
Ustaw wartość TRUE, jeśli dane łącza mają zostać skopiowane do Schowka. Ustaw go na FALSE, jeśli aplikacja nie obsługuje łączy.

*dwEfektyty*<br/>
Określa efekty, na które pozwoli źródło przeciągania w operacji przeciągania (kombinacja Kopiuj, Przenieś i Połącz).

*lpRectStartDrag*<br/>
Wskaźnik do prostokąta, który definiuje, gdzie faktycznie rozpoczyna się przeciąganie. Aby uzyskać więcej informacji zobacz następujące sekcji uwag.

### <a name="return-value"></a>Wartość zwracana

Wartość z wyliczenia DROPEFFECT. Jeśli jest DROPEFFECT_MOVE, oryginalne dane powinny zostać usunięte.

### <a name="remarks"></a>Uwagi

Operacja przeciągania i upuszczania nie rozpoczyna się natychmiast. Czeka, aż kursor myszy opuści prostokąt określony przez *lpRectStartDrag* lub do określonej liczby milisekund minęło. Jeśli *lpRectStartDrag* ma wartość NULL, używany jest domyślny prostokąt, aby przeciąganie rozpoczyna się, gdy kursor myszy przesuwa się o jeden piksel.

Czas opóźnienia jest określony przez ustawienie klucza rejestru. Czas opóźnienia można zmienić, wywołując [CWinApp::WriteProfileString](../../mfc/reference/cwinapp-class.md#writeprofilestring) lub [CWinApp::WriteProfileInt](../../mfc/reference/cwinapp-class.md#writeprofileint). Jeśli nie określisz czasu opóźnienia, używana jest wartość domyślna 200 milisekund. Czas opóźnienia przeciągania jest przechowywany w następujący sposób:

- Czas opóźnienia przeciągania systemu Windows NT jest przechowywany w HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\NT\CurrentVersion\IniFileMapping\win.ini\Windows\DragDelay.

- Czas opóźnienia przeciągania systemu Windows 3.x jest przechowywany w win. INI w sekcji [Windows}.

- Czas opóźnienia przeciągania systemu Windows 95/98 jest przechowywany w buforowanej wersji programu WIN. Ini.

Aby uzyskać więcej informacji o tym, jak informacje o opóźnieniu przeciągania są przechowywane w rejestrze lub pliku . INI, zobacz [WriteProfileString](/windows/win32/api/winbase/nf-winbase-writeprofilestringw) w windows SDK.

## <a name="coleserveritemgetclipboarddata"></a><a name="getclipboarddata"></a>COleServerItem::GetClipboardData

Wywołanie tej funkcji, aby wypełnić określony obiekt [COleDataSource](../../mfc/reference/coledatasource-class.md) ze wszystkimi danymi, które zostaną skopiowane do Schowka, jeśli nazwano [CopyToClipboard](#copytoclipboard) (te same dane będą również przesyłane, jeśli nazywasz [DoDragDrop](#dodragdrop)).

```cpp
void GetClipboardData(
    COleDataSource* pDataSource,
    BOOL bIncludeLink = FALSE,
    LPPOINT lpOffset = NULL,
    LPSIZE lpSize = NULL);
```

### <a name="parameters"></a>Parametry

*pDataSource (źródło danych)*<br/>
Wskaźnik do `COleDataSource` obiektu, który otrzyma dane elementu OLE we wszystkich obsługiwanych formatach.

*bIncludeLink*<br/>
PRAWDA, jeśli dane łącza powinny zostać skopiowane do Schowka. FAŁSZ, jeśli aplikacja serwera nie obsługuje łączy.

*lpOffset (zestaw lpOffset)*<br/>
Przesunięcie w pikselach kursora myszy od początku powstania obiektu.

*lpSize (rozmiar)*<br/>
Rozmiar obiektu w pikselach.

### <a name="remarks"></a>Uwagi

Ta funkcja wywołuje funkcję elementu członkowskiego [GetEmbedSourceData,](#getembedsourcedata) aby uzyskać dane macierzyste dla elementu OLE i wywołuje funkcję elementu członkowskiego [AddOtherClipboardData,](#addotherclipboarddata) aby uzyskać format prezentacji i wszystkie obsługiwane formaty konwersji. Jeśli *bIncludeLink* jest TRUE, funkcja wywołuje również [GetLinkSourceData,](#getlinksourcedata) aby uzyskać dane łącza dla elementu.

Zastąp tę funkcję, jeśli chcesz `COleDataSource` umieścić formaty w obiekcie `CopyToClipboard`przed lub po formatach dostarczonych przez program .

## <a name="coleserveritemgetdatasource"></a><a name="getdatasource"></a>COleServerItem::GetDataSource

Wywołanie tej funkcji, aby uzyskać [COleDataSource](../../mfc/reference/coledatasource-class.md) obiekt używany do przechowywania formatów konwersji, które obsługuje aplikacja serwera.

```
COleDataSource* GetDataSource();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `COleDataSource` obiektu używanego do przechowywania formatów konwersji.

### <a name="remarks"></a>Uwagi

Jeśli chcesz, aby aplikacja serwera oferowała dane w różnych formatach podczas operacji `COleDataSource` transferu danych, zarejestruj te formaty z obiektem zwróconym przez tę funkcję. Na przykład jeśli chcesz podać CF_TEXT reprezentację elementu OLE dla operacji Schowka lub operacji przeciągania `COleDataSource` i upuszczania, należy zarejestrować `OnRenderXxxData` format z obiektem zwraca, a następnie zastąpić funkcję elementu członkowskiego, aby zapewnić dane.

## <a name="coleserveritemgetdocument"></a><a name="getdocument"></a>COleServerItem::GetDocument

Wywołanie tej funkcji, aby uzyskać wskaźnik do dokumentu, który zawiera element.

```
COleServerDoc* GetDocument() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do dokumentu, który zawiera element; NULL, jeśli element nie jest częścią dokumentu.

### <a name="remarks"></a>Uwagi

Dzięki temu dostęp do dokumentu serwera, który `COleServerItem` został przekazany jako argument do konstruktora.

## <a name="coleserveritemgetembedsourcedata"></a><a name="getembedsourcedata"></a>COleServerItem::GetEmbedSourceData

Wywołanie tej funkcji, aby uzyskać dane CF_EMBEDSOURCE dla elementu OLE.

```cpp
void GetEmbedSourceData(LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>Parametry

*lpStgMedium*<br/>
Wskaźnik do [struktury STGMEDIUM,](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) która otrzyma CF_EMBEDSOURCE danych dla elementu OLE.

### <a name="remarks"></a>Uwagi

Ten format zawiera dane natywne elementu. Aby ta funkcja `Serialize` działała poprawnie, musi zostać zaimplementowana funkcja elementu członkowskiego.

Wynik można następnie dodać do źródła danych przy użyciu [COleDataSource::CacheData](../../mfc/reference/coledatasource-class.md#cachedata). Ta funkcja jest wywoływana automatycznie przez [COleServerItem::OnGetClipboardData](#ongetclipboarddata).

Aby uzyskać więcej informacji, zobacz [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) w windows SDK.

## <a name="coleserveritemgetitemname"></a><a name="getitemname"></a>COleServerItem::GetItemName

Wywołanie tej funkcji, aby uzyskać nazwę elementu.

```
const CString& GetItemName() const;
```

### <a name="return-value"></a>Wartość zwracana

Nazwa elementu .

### <a name="remarks"></a>Uwagi

Zazwyczaj ta funkcja jest wywoływana tylko dla elementów połączonych.

## <a name="coleserveritemgetlinksourcedata"></a><a name="getlinksourcedata"></a>COleServerItem::GetLinkSourceData

Wywołanie tej funkcji, aby uzyskać CF_LINKSOURCE danych dla elementu OLE.

```
BOOL GetLinkSourceData(LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>Parametry

*lpStgMedium*<br/>
Wskaźnik do [struktury STGMEDIUM,](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) która otrzyma CF_LINKSOURCE danych dla elementu OLE.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ten format zawiera identyfikator CLSID opisujący typ elementu OLE i informacje potrzebne do zlokalizowania dokumentu zawierającego element OLE.

Wynik można następnie dodać do źródła danych za pomocą [COleDataSource::CacheData](../../mfc/reference/coledatasource-class.md#cachedata). Ta funkcja jest wywoływana automatycznie przez [OnGetClipboardData](#ongetclipboarddata).

Aby uzyskać więcej informacji, zobacz [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) w windows SDK.

## <a name="coleserveritemgetobjectdescriptordata"></a><a name="getobjectdescriptordata"></a>COleServerItem::GetObjectDescriptorData

Wywołanie tej funkcji, aby uzyskać dane CF_OBJECTDESCRIPTOR dla elementu OLE.

```cpp
void GetObjectDescriptorData(
    LPPOINT lpOffset,
    LPSIZE lpSize,
    LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>Parametry

*lpOffset (zestaw lpOffset)*<br/>
Przesunięcie kliknięcia myszą od lewego górnego rogu elementu OLE. Może mieć wartość NULL.

*lpSize (rozmiar)*<br/>
Rozmiar towaru OLE. Może mieć wartość NULL.

*lpStgMedium*<br/>
Wskaźnik do [struktury STGMEDIUM,](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) która otrzyma CF_OBJECTDESCRIPTOR danych dla elementu OLE.

### <a name="remarks"></a>Uwagi

Informacje są kopiowane `STGMEDIUM` do struktury wskazanej przez *lpStgMedium*. Format ten zawiera informacje potrzebne do okna dialogowego Wklej specjalnie.

Aby uzyskać więcej informacji, zobacz [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) w windows SDK.

## <a name="coleserveritemisconnected"></a><a name="isconnected"></a>COleServerItem::IsConnected

Wywołanie tej funkcji, aby sprawdzić, czy element OLE jest podłączony.

```
BOOL IsConnected() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli element jest podłączony; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Element OLE jest uważany za połączony, jeśli jeden lub więcej kontenerów ma odwołania do towaru. Element jest połączony, jeśli jego liczba odwołań jest większa niż 0 lub jeśli jest elementem osadzonym.

## <a name="coleserveritemislinkeditem"></a><a name="islinkeditem"></a>COleServerItem::IsLinkedItem

Wywołanie tej funkcji, aby sprawdzić, czy element OLE jest elementem połączonym.

```
BOOL IsLinkedItem() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli element jest elementem połączonym; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Element jest połączony, jeśli element jest prawidłowy i nie jest zwracany na liście osadzonych elementów dokumentu. Połączony element może lub nie może być podłączony do kontenera.

Często używa się tej samej klasy dla elementów połączonych i osadzonych. `IsLinkedItem`umożliwia, aby połączone elementy zachowywały się inaczej niż elementy osadzone, chociaż wiele razy kod jest wspólny.

## <a name="coleserveritemm_sizeextent"></a><a name="m_sizeextent"></a>COleServerItem::m_sizeExtent

Ten element członkowski informuje serwer, jaka część obiektu jest widoczna w dokumencie kontenera.

```
CSize m_sizeExtent;
```

### <a name="remarks"></a>Uwagi

Domyślna implementacja [OnSetExtent](#onsetextent) ustawia ten element członkowski.

## <a name="coleserveritemnotifychanged"></a><a name="notifychanged"></a>COleServerItem::NotifyZmieniony

Wywołanie tej funkcji po zmianie połączonego elementu.

```cpp
void NotifyChanged(DVASPECT nDrawAspect = DVASPECT_CONTENT);
```

### <a name="parameters"></a>Parametry

*nDrawAspect*<br/>
Wartość z wyliczenia DVASPECT, która wskazuje, który aspekt elementu OLE został zmieniony. Ten parametr może mieć dowolną z następujących wartości:

- DVASPECT_CONTENT Element jest reprezentowany w taki sposób, że może być wyświetlany jako obiekt osadzony wewnątrz jego kontenera.

- DVASPECT_THUMBNAIL Element jest renderowany w reprezentacji "miniatury", dzięki czemu może być wyświetlany w narzędziu do przeglądania.

- DVASPECT_ICON Element jest reprezentowany przez ikonę.

- DVASPECT_DOCPRINT Element jest reprezentowany tak, jakby był drukowany za pomocą polecenia Drukuj z menu Plik.

### <a name="remarks"></a>Uwagi

Jeśli element kontenera jest połączony z dokumentem za pomocą łącza automatycznego, element jest aktualizowany w celu odzwierciedlenia zmian. W aplikacjach kontenera napisanych przy użyciu biblioteki klas Microsoft Foundation, [COleClientItem::OnChange](../../mfc/reference/coleclientitem-class.md#onchange) jest wywoływana w odpowiedzi.

## <a name="coleserveritemondoverb"></a><a name="ondoverb"></a>COleServerItem::OnDoVerb

Wywoływane przez strukturę do wykonania określonego zlecenia.

```
virtual void OnDoVerb(LONG iVerb);
```

### <a name="parameters"></a>Parametry

*iVerb*<br/>
Określa zlecenie do wykonania. Może to być dowolna z następujących czynności:

|Wartość|Znaczenie|Symbol|
|-----------|-------------|------------|
|0|Primary — Zlecenie|OLEIVERB_PRIMARY|
|1|Czasownik wtórny|(Brak)|
|- 1|Element wyświetlania do edycji|OLEIVERB_SHOW|
|- 2|Edytowanie elementu w osobnym oknie|OLEIVERB_OPEN|
|- 3|Ukryj element|OLEIVERB_HIDE|

Wartość -1 jest zazwyczaj aliasem dla innego zlecenia. Jeśli otwarta edycja nie jest obsługiwana, -2 ma taki sam efekt jak -1. Aby uzyskać dodatkowe wartości, zobacz [IOleObject::DoVerb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) w windows SDK.

### <a name="remarks"></a>Uwagi

Jeśli aplikacja kontenera została napisana za pomocą biblioteki klas Microsoft Foundation, ta funkcja jest wywoływana, gdy wywoływana jest funkcja [COleClientItem::Activate](../../mfc/reference/coleclientitem-class.md#activate) elementu członkowskiego odpowiedniego `COleClientItem` obiektu. Domyślna implementacja wywołuje [OnShow](#onshow) funkcji elementu członkowskiego, jeśli jest określony zlecenie podstawowe lub OLEIVERB_SHOW, [OnOpen,](#onopen) jeśli określono zerówka pomocniczego lub OLEIVERB_OPEN, i [OnHide,](#onhide) jeśli określono OLEIVERB_HIDE. Domyślna implementacja wywołuje, `OnShow` jeśli *iVerb* nie jest jednym z zleceń wymienionych powyżej.

Zastądź tę funkcję, jeśli zlecenie podstawowe nie pokazuje elementu. Na przykład jeśli element jest nagrywanie dźwięku i jego podstawowym zleceniem jest Odtwórz, nie trzeba wyświetlać aplikacji serwera, aby odtworzyć element.

Aby uzyskać więcej informacji, zobacz [IOleObject::DoVerb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) w windows SDK.

## <a name="coleserveritemondraw"></a><a name="ondraw"></a>COleServerItem::OnDraw

Wywoływana przez strukturę do renderowania elementu OLE w metaplik.

```
virtual BOOL OnDraw(
    CDC* pDC,
    CSize& rSize) = 0;
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Wskaźnik do obiektu [CDC,](../../mfc/reference/cdc-class.md) na którym ma być rysowany element. Kontekst wyświetlania jest automatycznie połączony z kontekstem wyświetlania atrybutów, dzięki czemu można wywołać funkcje atrybutów, chociaż w ten sposób spowoduje to, że metaplik jest specyficzny dla urządzenia.

*rSize (rozmiar)*<br/>
Rozmiar, w jednostkach HIMETRIC, w których należy narysować metaplik.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli element został pomyślnie narysowany; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Reprezentacja metapliku elementu OLE jest używana do wyświetlania elementu w aplikacji kontenera. Jeśli aplikacja kontenera została napisana za pomocą biblioteki klas Microsoft Foundation, metaplik jest używany przez funkcję [draw](../../mfc/reference/coleclientitem-class.md#draw) elementu członkowskiego odpowiedniego obiektu [COleClientItem.](../../mfc/reference/coleclientitem-class.md) Nie ma implementacji domyślnej. Należy zastąpić tę funkcję, aby narysować element w określonym kontekście urządzenia.

## <a name="coleserveritemondrawex"></a><a name="ondrawex"></a>COleServerItem::OnDrawEx

Wywoływana przez ramy dla wszystkich rysunków.

```
virtual BOOL OnDrawEx(
    CDC* pDC,
    DVASPECT nDrawAspect,
    CSize& rSize);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Wskaźnik do obiektu [CDC,](../../mfc/reference/cdc-class.md) na którym ma być rysowany element. Kontroler domeny jest automatycznie połączony z kontrolerem domeny atrybutu, dzięki czemu można wywołać funkcje atrybutów, chociaż w ten sposób spowoduje, że metaplik specyficzne dla urządzenia.

*nDrawAspect*<br/>
Wartość z wyliczenia DVASPECT. Ten parametr może mieć dowolną z następujących wartości:

- DVASPECT_CONTENT Element jest reprezentowany w taki sposób, że może być wyświetlany jako obiekt osadzony wewnątrz jego kontenera.

- DVASPECT_THUMBNAIL Element jest renderowany w reprezentacji "miniatury", dzięki czemu może być wyświetlany w narzędziu do przeglądania.

- DVASPECT_ICON Element jest reprezentowany przez ikonę.

- DVASPECT_DOCPRINT Element jest reprezentowany tak, jakby był drukowany za pomocą polecenia Drukuj z menu Plik.

*rSize (rozmiar)*<br/>
Rozmiar towaru w jednostkach HIMETRIC.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli element został pomyślnie narysowany; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Domyślna implementacja wywołuje, `OnDraw` gdy DVASPECT jest równa DVASPECT_CONTENT; w przeciwnym razie to się nie powiedzie.

Zastąp tę funkcję, aby zapewnić dane prezentacji dla aspektów innych niż DVASPECT_CONTENT, takich jak DVASPECT_ICON lub DVASPECT_THUMBNAIL.

## <a name="coleserveritemongetclipboarddata"></a><a name="ongetclipboarddata"></a>COleServerItem::OnGetClipboardData

Wywoływane przez strukturę, `COleDataSource` aby uzyskać obiekt zawierający wszystkie dane, które zostaną umieszczone w Schowku przez wywołanie [copytoclipboard](#copytoclipboard) funkcji elementu członkowskiego.

```
virtual COleDataSource* OnGetClipboardData(
    BOOL bIncludeLink,
    LPPOINT lpOffset,
    LPSIZE lpSize);
```

### <a name="parameters"></a>Parametry

*bIncludeLink*<br/>
Ustaw wartość TRUE, jeśli dane łącza mają zostać skopiowane do Schowka. Ustaw to na FALSE, jeśli aplikacja serwera nie obsługuje łączy.

*lpOffset (zestaw lpOffset)*<br/>
Przesunięcie kursora myszy od początku powstania obiektu w pikselach.

*lpSize (rozmiar)*<br/>
Rozmiar obiektu w pikselach.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do [obiektu COleDataSource](../../mfc/reference/coledatasource-class.md) zawierającego dane Schowka.

### <a name="remarks"></a>Uwagi

Domyślna implementacja tej funkcji wywołuje [GetClipboardData](#getclipboarddata).

## <a name="coleserveritemongetextent"></a><a name="ongetextent"></a>COleServerItem::OnGetExtent

Wywoływana przez strukturę, aby pobrać rozmiar( w jednostkach HIMETRIC) towaru OLE.

```
virtual BOOL OnGetExtent(
    DVASPECT nDrawAspect,
    CSize& rSize);
```

### <a name="parameters"></a>Parametry

*nDrawAspect*<br/>
Określa aspekt elementu OLE, którego granice mają zostać pobrane. Ten parametr może mieć dowolną z następujących wartości:

- DVASPECT_CONTENT Element jest reprezentowany w taki sposób, że może być wyświetlany jako obiekt osadzony wewnątrz jego kontenera.

- DVASPECT_THUMBNAIL Element jest renderowany w reprezentacji "miniatury", dzięki czemu może być wyświetlany w narzędziu do przeglądania.

- DVASPECT_ICON Element jest reprezentowany przez ikonę.

- DVASPECT_DOCPRINT Element jest reprezentowany tak, jakby był drukowany za pomocą polecenia Drukuj z menu Plik.

*rSize (rozmiar)*<br/>
Odwołanie do `CSize` obiektu, który otrzyma rozmiar elementu OLE.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli aplikacja kontenera została napisana za pomocą biblioteki klas Programu Microsoft Foundation, `COleClientItem` ta funkcja jest wywoływana, gdy wywoływana jest funkcja elementu członkowskiego [GetExtent](../../mfc/reference/coleclientitem-class.md#getextent) odpowiedniego obiektu. Domyślna implementacja nic nie robi. Musisz zaimplementować go samodzielnie. Zastąd w tej funkcji, jeśli chcesz wykonać specjalne przetwarzanie podczas obsługi żądania rozmiaru elementu OLE.

## <a name="coleserveritemonhide"></a><a name="onhide"></a>COleServerItem::OnHide

Wywoływane przez strukturę, aby ukryć element OLE.

```
virtual void OnHide();
```

### <a name="remarks"></a>Uwagi

Wywołania `COleServerDoc::OnShowDocument( FALSE )`domyślne . Funkcja powiadamia również kontener, że element OLE został ukryty. Zastąd w tej funkcji, jeśli chcesz wykonać specjalne przetwarzanie podczas ukrywania elementu OLE.

## <a name="coleserveritemoninitfromdata"></a><a name="oninitfromdata"></a>COleServerItem::OnInitFromData

Wywoływana przez strukturę do inicjowania elementu OLE przy użyciu zawartości *pDataObject*.

```
virtual BOOL OnInitFromData(
    COleDataObject* pDataObject,
    BOOL bCreation);
```

### <a name="parameters"></a>Parametry

*pDataObject (1000)*<br/>
Wskaźnik do obiektu danych OLE zawierającego dane w różnych formatach w celu zainicjowania elementu OLE.

*bTworzenie*<br/>
PRAWDA, jeśli funkcja jest wywoływana do inicjowania elementu OLE nowo tworzone przez aplikację kontenera. FAŁSZ, jeśli funkcja jest wywoływana w celu zastąpienia zawartości już istniejącego elementu OLE.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli *bCreation* jest PRAWDA, ta funkcja jest wywoływana, jeśli kontener implementuje Wstaw nowy obiekt na podstawie bieżącego zaznaczenia. Wybrane dane są używane podczas tworzenia nowego elementu OLE. Na przykład podczas wybierania zakresu komórek w programie arkusza kalkulacyjnego, a następnie za pomocą opcji Wstaw nowy obiekt, aby utworzyć wykres na podstawie wartości w wybranym zakresie. Domyślna implementacja nic nie robi. Zastąp tę funkcję, aby wybrać akceptowalny format z tych oferowanych przez *pDataObject* i zainicjować element OLE na podstawie dostarczonych danych. Jest to zaawansowane zastąpienie.

Aby uzyskać więcej informacji, zobacz [IOleObject::InitFromData](/windows/win32/api/oleidl/nf-oleidl-ioleobject-initfromdata) w windows SDK.

## <a name="coleserveritemonopen"></a><a name="onopen"></a>COleServerItem::OnOpen

Wywoływane przez strukturę do wyświetlania elementu OLE w osobnym wystąpieniu aplikacji serwera, a nie w miejscu.

```
virtual void OnOpen();
```

### <a name="remarks"></a>Uwagi

Domyślna implementacja aktywuje pierwsze okno ramki wyświetlające dokument zawierający element OLE; jeśli aplikacja jest mini-serwerem, domyślna implementacja pokazuje okno główne. Funkcja powiadamia również kontener, że element OLE został otwarty.

Zastąd w tej funkcji należy wykonać specjalne przetwarzanie podczas otwierania elementu OLE. Jest to szczególnie typowe w przypadku elementów połączonych, w których chcesz ustawić zaznaczenie na łącze po jego otwarciu.

Aby uzyskać więcej informacji, zobacz [IOleClientSite::OnShowWindow](/windows/win32/api/oleidl/nf-oleidl-ioleclientsite-onshowwindow) w windows SDK.

## <a name="coleserveritemonqueryupdateitems"></a><a name="onqueryupdateitems"></a>COleServerItem::OnQueryUpdateItems

Wywoływane przez strukturę, aby ustalić, czy wszystkie połączone elementy w bieżącym dokumencie serwera są nieaktualne.

```
virtual BOOL OnQueryUpdateItems();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli dokument zawiera elementy wymagające aktualizacji; 0, jeśli wszystkie elementy są aktualne.

### <a name="remarks"></a>Uwagi

Element jest nieaktualny, jeśli jego dokument źródłowy został zmieniony, ale połączony element nie został zaktualizowany w celu odzwierciedlenia zmian w dokumencie.

## <a name="coleserveritemonrenderdata"></a><a name="onrenderdata"></a>COleServerItem::OnRenderData

Wywoływane przez strukturę do pobierania danych w określonym formacie.

```
virtual BOOL OnRenderData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>Parametry

*lpFormatEtc*<br/>
Wskazuje strukturę [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) określającą format, w którym wymagane są informacje.

*lpStgMedium*<br/>
Wskazuje strukturę [STGMEDIUM,](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) w której dane mają być zwracane.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Określony format to jeden wcześniej `COleDataSource` umieszczony w obiekcie przy użyciu [delayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata) lub [DelayRenderFileData](../../mfc/reference/coledatasource-class.md#delayrenderfiledata) funkcji członkowskiej do opóźnionego renderowania. Domyślna implementacja tej funkcji wywołuje [OnRenderFileData](#onrenderfiledata) lub [OnRenderGlobalData](#onrenderglobaldata), odpowiednio, jeśli dostarczony nośnik pamięci jest plikiem lub pamięcią. Jeśli żaden z tych formatów nie jest dostarczany, domyślna implementacja zwraca 0 i nic nie robi.

Jeżeli *lpStgMedium*-> *tymed* jest TYMED_NULL, STGMEDIUM powinien być przydzielony i wypełniony zgodnie z *lpFormatEtc->tymed*. Jeśli nie TYMED_NULL, STGMEDIUM należy wypełnić danymi.

Jest to zaawansowane zastąpienie. Zastąp tę funkcję, aby podać dane w żądanym formacie i nośniku. W zależności od danych można zastąpić jedną z innych wersji tej funkcji. Jeśli dane są małe i stałe, `OnRenderGlobalData`należy zastąpić . Jeśli dane są w pliku lub mają zmienny `OnRenderFileData`rozmiar, należy zastąpić .

Aby uzyskać więcej informacji, zobacz [IDataObject::GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata), [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1), [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)i [TYMED](/windows/win32/api/objidl/ne-objidl-tymed) w windows SDK.

## <a name="coleserveritemonrenderfiledata"></a><a name="onrenderfiledata"></a>COleServerItem::OnRenderFileData

Wywoływane przez strukturę do pobierania danych w określonym formacie, gdy nośnikiem jest plik.

```
virtual BOOL OnRenderFileData(
    LPFORMATETC lpFormatEtc,
    CFile* pFile);
```

### <a name="parameters"></a>Parametry

*lpFormatEtc*<br/>
Wskazuje strukturę [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) określającą format, w którym wymagane są informacje.

*p Plik*<br/>
Wskazuje obiekt, `CFile` w którym mają być renderowane dane.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Określony format to jeden wcześniej `COleDataSource` umieszczony w obiekcie przy użyciu [delayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata) funkcji elementu członkowskiego do opóźnionego renderowania. Domyślna implementacja tej funkcji po prostu zwraca FALSE.

Jest to zaawansowane zastąpienie. Zastąp tę funkcję, aby podać dane w żądanym formacie i nośniku. W zależności od danych można zastąpić jedną z innych wersji tej funkcji. Jeśli chcesz obsłużyć wiele nośników pamięci masowej, należy zastąpić [onrenderdata](#onrenderdata). Jeśli dane są w pliku lub mają zmienny rozmiar, należy zastąpić [onrenderfiledata](#onrenderfiledata).

Aby uzyskać więcej informacji, zobacz [IDataObject::GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) i [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) w windows SDK.

## <a name="coleserveritemonrenderglobaldata"></a><a name="onrenderglobaldata"></a>COleServerItem::OnRenderGlobalData

Wywoływana przez strukturę do pobierania danych w określonym formacie, gdy określonym nośnikiem pamięci jest pamięć globalna.

```
virtual BOOL OnRenderGlobalData(
    LPFORMATETC lpFormatEtc,
    HGLOBAL* phGlobal);
```

### <a name="parameters"></a>Parametry

*lpFormatEtc*<br/>
Wskazuje strukturę [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) określającą format, w którym wymagane są informacje.

*phGlobal (własówce)*<br/>
Wskazuje dojście do pamięci globalnej, w której mają być zwracane dane. Jeśli nie przydzielono pamięci, ten parametr może mieć wartość NULL.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Określony format to jeden wcześniej `COleDataSource` umieszczony w obiekcie przy użyciu [delayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata) funkcji elementu członkowskiego do opóźnionego renderowania. Domyślna implementacja tej funkcji po prostu zwraca FALSE.

Jeśli *phGlobal* ma wartość NULL, nowy HGLOBAL powinien zostać przydzielony i zwrócony w *phGlobal*. W przeciwnym razie HGLOBAL określony przez *phGlobal* powinien być wypełniony danymi. Ilość danych umieszczonych w HGLOBAL nie może przekraczać bieżącego rozmiaru bloku pamięci. Ponadto bloku nie można ponownie przydzielić do większego rozmiaru.

Jest to zaawansowane zastąpienie. Zastąp tę funkcję, aby podać dane w żądanym formacie i nośniku. W zależności od danych można zastąpić jedną z innych wersji tej funkcji. Jeśli chcesz obsłużyć wiele nośników pamięci masowej, należy zastąpić [onrenderdata](#onrenderdata). Jeśli dane są w pliku lub mają zmienny rozmiar, należy zastąpić [onrenderfiledata](#onrenderfiledata).

Aby uzyskać więcej informacji, zobacz [IDataObject::GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) i [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) w windows SDK.

## <a name="coleserveritemonsetcolorscheme"></a><a name="onsetcolorscheme"></a>COleServerItem::OnSetColorScheme

Wywoływana przez strukturę, aby określić paletę kolorów, która ma być używana podczas edytowania elementu OLE.

```
virtual BOOL OnSetColorScheme(const LOGPALETTE* lpLogPalette);
```

### <a name="parameters"></a>Parametry

*lpLogPalette (lpLogPalette)*<br/>
Wskaźnik do struktury [LOGPALETTE](/windows/win32/api/wingdi/ns-wingdi-logpalette) systemu Windows.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli używana jest paleta kolorów; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli aplikacja kontenera została napisana przy użyciu biblioteki klas Programu Microsoft Foundation, ta funkcja jest wywoływana, `COleClientItem` gdy wywoływana jest funkcja [IOleObject::SetColorScheme](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setcolorscheme) odpowiedniego obiektu. Domyślna implementacja zwraca WARTOŚĆ FAŁSZ. Zastąpokaj tę funkcję, jeśli chcesz użyć zalecanej palety. Aplikacja serwera nie jest wymagana do korzystania z sugerowanej palety.

Aby uzyskać więcej informacji, zobacz [IOleObject::SetColorScheme](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setcolorscheme) w zestawie Windows SDK.

## <a name="coleserveritemonsetdata"></a><a name="onsetdata"></a>COleServerItem::OnSetData

Wywoływane przez strukturę, aby zastąpić dane elementu OLE z określonymi danymi.

```
virtual BOOL OnSetData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium,
    BOOL bRelease);
```

### <a name="parameters"></a>Parametry

*lpFormatEtc*<br/>
Wskaźnik do struktury [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) określającej format danych.

*lpStgMedium*<br/>
Wskaźnik do struktury [STGMEDIUM,](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) w której znajdują się dane.

*Brelease*<br/>
Wskazuje, kto jest właścicielem nośnika danych po zakończeniu wywołania funkcji. Osoba wywołująca decyduje, kto jest odpowiedzialny za zwolnienie zasobów przydzielonych w imieniu nośnika danych. Wywołujący robi to, ustawiając *bWyzwaj*. Jeśli *bWyzwanie* jest niezerowe, element serwera przejmuje na własność, zwalniając nośnik po zakończeniu używania go. Gdy *bWyzwanie* wynosi 0, obiekt wywołujący zachowuje własność, a element serwera może używać nośnika magazynu tylko na czas trwania wywołania.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Element serwera nie przejmie na własność danych, dopóki nie pomyślnie je uzyskał. Oznacza to, że nie bierze na siebie, jeśli zwraca 0. Jeśli źródło danych przejmuje na własność, zwalnia nośnik pamięci masowej, wywołując [funkcję ReleaseStgMedium.](/windows/win32/api/ole2/nf-ole2-releasestgmedium)

Domyślna implementacja nic nie robi. Zastąp tę funkcję, aby zastąpić dane elementu OLE określonymi danymi. Jest to zaawansowane zastąpienie.

Aby uzyskać więcej informacji, zobacz [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1), [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)i [ReleaseStgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium) w windows SDK.

## <a name="coleserveritemonsetextent"></a><a name="onsetextent"></a>COleServerItem::OnSetExtent

Wywoływane przez platformę, aby poinformować element OLE, ile miejsca jest dostępne dla niego w dokumencie kontenera.

```
virtual BOOL OnSetExtent(
    DVASPECT nDrawAspect,
    const CSize& size);
```

### <a name="parameters"></a>Parametry

*nDrawAspect*<br/>
Określa aspekt elementu OLE, którego granice są określone. Ten parametr może mieć dowolną z następujących wartości:

- DVASPECT_CONTENT Element jest reprezentowany w taki sposób, że może być wyświetlany jako obiekt osadzony wewnątrz jego kontenera.

- DVASPECT_THUMBNAIL Element jest renderowany w reprezentacji "miniatury", dzięki czemu może być wyświetlany w narzędziu do przeglądania.

- DVASPECT_ICON Element jest reprezentowany przez ikonę.

- DVASPECT_DOCPRINT Element jest reprezentowany tak, jakby był drukowany za pomocą polecenia Drukuj z menu Plik.

*Rozmiar*<br/>
Struktura [CSize](../../atl-mfc-shared/reference/csize-class.md) określająca nowy rozmiar elementu OLE.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli aplikacja kontenera została napisana za pomocą biblioteki klas Programu Microsoft Foundation, `COleClientItem` ta funkcja jest wywoływana, gdy wywoływana jest funkcja elementu członkowskiego [SetExtent](../../mfc/reference/coleclientitem-class.md#setextent) odpowiedniego obiektu. Domyślna implementacja ustawia [m_sizeExtent](#m_sizeextent) element członkowski na określony rozmiar, jeśli *nDrawAspect* jest DVASPECT_CONTENT; w przeciwnym razie zwraca 0. Zastąd w tej funkcji należy wykonać specjalne przetwarzanie po zmianie rozmiaru elementu.

## <a name="coleserveritemonshow"></a><a name="onshow"></a>COleServerItem::OnShow

Wywoływane przez strukturę, aby poinstruować aplikację serwera do wyświetlania elementu OLE w miejscu.

```
virtual void OnShow();
```

### <a name="remarks"></a>Uwagi

Ta funkcja jest zazwyczaj wywoływana, gdy użytkownik aplikacji kontenera tworzy element lub wykonuje zlecenie, takie jak Edit, który wymaga elementu, który ma być wyświetlany. Domyślna implementacja próbuje aktywacji w miejscu. Jeśli to się nie `OnOpen` powiedzie, funkcja wywołuje funkcję elementu członkowskiego, aby wyświetlić element OLE w osobnym oknie.

Zastąd w tej funkcji, jeśli chcesz wykonać specjalne przetwarzanie, gdy wyświetlany jest element OLE.

## <a name="coleserveritemonupdate"></a><a name="onupdate"></a>COleServerItem::OnUpdate

Wywoływana przez strukturę, gdy element został zmodyfikowany.

```
virtual void OnUpdate(
    COleServerItem* pSender,
    LPARAM lHint,
    CObject* pHint,
    DVASPECT nDrawAspect);
```

### <a name="parameters"></a>Parametry

*pSender (nadawca)*<br/>
Wskaźnik do elementu, który zmodyfikował dokument. Może mieć wartość NULL.

*Lhint*<br/>
Zawiera informacje o modyfikacji.

*Phint*<br/>
Wskaźnik do obiektu przechowującego informacje o modyfikacji.

*nDrawAspect*<br/>
Wartość z wyliczenia DVASPECT. Ten parametr może mieć jedną z następujących wartości:

- DVASPECT_CONTENT Element jest reprezentowany w taki sposób, że może być wyświetlany jako obiekt osadzony wewnątrz jego kontenera.

- DVASPECT_THUMBNAIL Element jest renderowany w reprezentacji "miniatury", dzięki czemu może być wyświetlany w narzędziu do przeglądania.

- DVASPECT_ICON Element jest reprezentowany przez ikonę.

- DVASPECT_DOCPRINT Element jest reprezentowany tak, jakby był drukowany za pomocą polecenia Drukuj z menu Plik.

### <a name="remarks"></a>Uwagi

Domyślna implementacja wywołuje [NotifyChanged](#notifychanged), niezależnie od wskazówki lub nadawcy.

## <a name="coleserveritemonupdateitems"></a><a name="onupdateitems"></a>COleServerItem::OnUpdateItems

Wywoływana przez strukturę, aby zaktualizować wszystkie elementy w dokumencie serwera.

```
virtual void OnUpdateItems();
```

### <a name="remarks"></a>Uwagi

Domyślna implementacja wywołuje `COleClientItem` [UpdateLink](../../mfc/reference/coleclientitem-class.md#updatelink) dla wszystkich obiektów w dokumencie.

## <a name="coleserveritemsetitemname"></a><a name="setitemname"></a>COleServerItem::Nazwa zestawu

Wywołanie tej funkcji podczas tworzenia połączonego elementu, aby ustawić jego nazwę.

```cpp
void SetItemName(LPCTSTR lpszItemName);
```

### <a name="parameters"></a>Parametry

*lpszItemName*<br/>
Wskaźnik do nowej nazwy elementu.

### <a name="remarks"></a>Uwagi

Nazwa musi być unikatowa w dokumencie. Gdy aplikacja serwera jest wywoływana do edytowania elementu połączonego, aplikacja używa tej nazwy, aby znaleźć element. Nie trzeba wywoływać tej funkcji dla elementów osadzonych.

## <a name="see-also"></a>Zobacz też

[Przykładowy HIERSVR MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CDocItem](../../mfc/reference/cdocitem-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleClientItem](../../mfc/reference/coleclientitem-class.md)<br/>
[Klasa COleServerDoc](../../mfc/reference/coleserverdoc-class.md)<br/>
[Klasa COleTemplateServer](../../mfc/reference/coletemplateserver-class.md)
