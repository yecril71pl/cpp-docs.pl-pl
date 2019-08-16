---
title: Klasa COleServerDoc
ms.date: 11/04/2016
f1_keywords:
- COleServerDoc
- AFXOLE/COleServerDoc
- AFXOLE/COleServerDoc::COleServerDoc
- AFXOLE/COleServerDoc::ActivateDocObject
- AFXOLE/COleServerDoc::ActivateInPlace
- AFXOLE/COleServerDoc::DeactivateAndUndo
- AFXOLE/COleServerDoc::DiscardUndoState
- AFXOLE/COleServerDoc::GetClientSite
- AFXOLE/COleServerDoc::GetEmbeddedItem
- AFXOLE/COleServerDoc::GetItemClipRect
- AFXOLE/COleServerDoc::GetItemPosition
- AFXOLE/COleServerDoc::GetZoomFactor
- AFXOLE/COleServerDoc::IsDocObject
- AFXOLE/COleServerDoc::IsEmbedded
- AFXOLE/COleServerDoc::IsInPlaceActive
- AFXOLE/COleServerDoc::NotifyChanged
- AFXOLE/COleServerDoc::NotifyClosed
- AFXOLE/COleServerDoc::NotifyRename
- AFXOLE/COleServerDoc::NotifySaved
- AFXOLE/COleServerDoc::OnDeactivate
- AFXOLE/COleServerDoc::OnDeactivateUI
- AFXOLE/COleServerDoc::OnDocWindowActivate
- AFXOLE/COleServerDoc::OnResizeBorder
- AFXOLE/COleServerDoc::OnShowControlBars
- AFXOLE/COleServerDoc::OnUpdateDocument
- AFXOLE/COleServerDoc::RequestPositionChange
- AFXOLE/COleServerDoc::SaveEmbedding
- AFXOLE/COleServerDoc::ScrollContainerBy
- AFXOLE/COleServerDoc::UpdateAllItems
- AFXOLE/COleServerDoc::CreateInPlaceFrame
- AFXOLE/COleServerDoc::DestroyInPlaceFrame
- AFXOLE/COleServerDoc::GetDocObjectServer
- AFXOLE/COleServerDoc::OnClose
- AFXOLE/COleServerDoc::OnExecOleCmd
- AFXOLE/COleServerDoc::OnFrameWindowActivate
- AFXOLE/COleServerDoc::OnGetEmbeddedItem
- AFXOLE/COleServerDoc::OnReactivateAndUndo
- AFXOLE/COleServerDoc::OnSetHostNames
- AFXOLE/COleServerDoc::OnSetItemRects
- AFXOLE/COleServerDoc::OnShowDocument
helpviewer_keywords:
- COleServerDoc [MFC], COleServerDoc
- COleServerDoc [MFC], ActivateDocObject
- COleServerDoc [MFC], ActivateInPlace
- COleServerDoc [MFC], DeactivateAndUndo
- COleServerDoc [MFC], DiscardUndoState
- COleServerDoc [MFC], GetClientSite
- COleServerDoc [MFC], GetEmbeddedItem
- COleServerDoc [MFC], GetItemClipRect
- COleServerDoc [MFC], GetItemPosition
- COleServerDoc [MFC], GetZoomFactor
- COleServerDoc [MFC], IsDocObject
- COleServerDoc [MFC], IsEmbedded
- COleServerDoc [MFC], IsInPlaceActive
- COleServerDoc [MFC], NotifyChanged
- COleServerDoc [MFC], NotifyClosed
- COleServerDoc [MFC], NotifyRename
- COleServerDoc [MFC], NotifySaved
- COleServerDoc [MFC], OnDeactivate
- COleServerDoc [MFC], OnDeactivateUI
- COleServerDoc [MFC], OnDocWindowActivate
- COleServerDoc [MFC], OnResizeBorder
- COleServerDoc [MFC], OnShowControlBars
- COleServerDoc [MFC], OnUpdateDocument
- COleServerDoc [MFC], RequestPositionChange
- COleServerDoc [MFC], SaveEmbedding
- COleServerDoc [MFC], ScrollContainerBy
- COleServerDoc [MFC], UpdateAllItems
- COleServerDoc [MFC], CreateInPlaceFrame
- COleServerDoc [MFC], DestroyInPlaceFrame
- COleServerDoc [MFC], GetDocObjectServer
- COleServerDoc [MFC], OnClose
- COleServerDoc [MFC], OnExecOleCmd
- COleServerDoc [MFC], OnFrameWindowActivate
- COleServerDoc [MFC], OnGetEmbeddedItem
- COleServerDoc [MFC], OnReactivateAndUndo
- COleServerDoc [MFC], OnSetHostNames
- COleServerDoc [MFC], OnSetItemRects
- COleServerDoc [MFC], OnShowDocument
ms.assetid: a9cdd96a-e0ac-43bb-9203-2c29237e965c
ms.openlocfilehash: eec94a32fa0963d4cf2eccae0fb9e2423e75ffdc
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503813"
---
# <a name="coleserverdoc-class"></a>Klasa COleServerDoc

Klasa podstawowa dla dokumentów serwera OLE.

## <a name="syntax"></a>Składnia

```
class AFX_NOVTABLE COleServerDoc : public COleLinkingDoc
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleServerDoc::COleServerDoc](#coleserverdoc)|Konstruuje `COleServerDoc` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleServerDoc::ActivateDocObject](#activatedocobject)|Aktywuje skojarzony dokument DocObject.|
|[COleServerDoc::ActivateInPlace](#activateinplace)|Aktywuje dokument do edycji w miejscu.|
|[COleServerDoc::DeactivateAndUndo](#deactivateandundo)|Dezaktywuje interfejs użytkownika serwera.|
|[COleServerDoc::D iscardUndoState](#discardundostate)|Odrzuca informacje o stanie cofnięcia.|
|[COleServerDoc::GetClientSite](#getclientsite)|Pobiera wskaźnik do podstawowego `IOleClientSite` interfejsu.|
|[COleServerDoc::GetEmbeddedItem](#getembeddeditem)|Zwraca wskaźnik do elementu reprezentującego cały dokument.|
|[COleServerDoc::GetItemClipRect](#getitemcliprect)|Zwraca bieżący prostokąt wycinka do edycji w miejscu.|
|[COleServerDoc::GetItemPosition](#getitemposition)|Zwraca bieżący prostokąt położenia względem obszaru klienckiego aplikacji kontenera do edycji w miejscu.|
|[COleServerDoc::GetZoomFactor](#getzoomfactor)|Zwraca współczynnik powiększenia (w pikselach).|
|[COleServerDoc::IsDocObject](#isdocobject)|Określa, czy dokument jest DocObject.|
|[COleServerDoc:: isembedded](#isembedded)|Wskazuje, czy dokument jest osadzony w dokumencie kontenera lub jest uruchomiony autonomicznie.|
|[COleServerDoc::IsInPlaceActive](#isinplaceactive)|Zwraca wartość PRAWDA, jeśli element jest aktualnie aktywowany.|
|[COleServerDoc::NotifyChanged](#notifychanged)|Powiadamia kontenery, że dokument został zmieniony przez użytkownika.|
|[COleServerDoc::NotifyClosed](#notifyclosed)|Powiadamia kontenery, że użytkownik zamknął dokument.|
|[COleServerDoc::NotifyRename](#notifyrename)|Powiadamia kontenery, że użytkownik zmienił nazwę dokumentu.|
|[COleServerDoc::NotifySaved](#notifysaved)|Powiadamia kontenery, że użytkownik zapisał dokument.|
|[COleServerDoc:: OnDeactivate](#ondeactivate)|Wywoływane przez platformę, gdy użytkownik dezaktywuje element, który został aktywowany.|
|[COleServerDoc::OnDeactivateUI](#ondeactivateui)|Wywoływane przez platformę, aby zniszczyć kontrolki i inne elementy interfejsu użytkownika utworzone w ramach aktywacji w miejscu.|
|[COleServerDoc::OnDocWindowActivate](#ondocwindowactivate)|Wywoływane przez platformę, gdy okno ramki dokumentu kontenera jest aktywowane lub dezaktywowane.|
|[COleServerDoc::OnResizeBorder](#onresizeborder)|Wywoływane przez platformę, gdy zmieniany jest rozmiar okna ramki aplikacji kontenera lub okna dokumentu.|
|[COleServerDoc::OnShowControlBars](#onshowcontrolbars)|Wywoływane przez platformę, by pokazać lub ukryć paski kontroli do edycji w miejscu.|
|[COleServerDoc::OnUpdateDocument](#onupdatedocument)|Wywoływane przez platformę, gdy zostanie zapisany dokument serwera, który jest elementem osadzonym, co umożliwia zaktualizowanie kopii elementu kontenera.|
|[COleServerDoc::RequestPositionChange](#requestpositionchange)|Zmienia położenie ramki edycji w miejscu.|
|[COleServerDoc::SaveEmbedding](#saveembedding)|Instruuje aplikację kontenera, aby zapisywał dokument.|
|[COleServerDoc::ScrollContainerBy](#scrollcontainerby)|Przewija dokument kontenera.|
|[COleServerDoc::UpdateAllItems](#updateallitems)|Powiadamia kontenery, że dokument został zmieniony przez użytkownika.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[COleServerDoc::CreateInPlaceFrame](#createinplaceframe)|Wywoływane przez platformę, by utworzyć okno ramowe do edycji w miejscu.|
|[COleServerDoc::DestroyInPlaceFrame](#destroyinplaceframe)|Wywoływane przez platformę, aby zniszczyć okno ramowe do edycji w miejscu.|
|[COleServerDoc::GetDocObjectServer](#getdocobjectserver)|Przesłoń tę funkcję, aby utworzyć `CDocObjectServer` nowy obiekt i wskazać, że ten dokument jest kontenerem DocObject.|
|[COleServerDoc::OnClose](#onclose)|Wywoływane przez platformę, gdy kontener jest zażądał zamknięcia dokumentu.|
|[COleServerDoc::OnExecOleCmd](#onexecolecmd)|Wykonuje określone polecenie lub wyświetla pomoc dla polecenia.|
|[COleServerDoc::OnFrameWindowActivate](#onframewindowactivate)|Wywoływane przez platformę, gdy okno ramki kontenera jest aktywowane lub dezaktywowane.|
|[COleServerDoc::OnGetEmbeddedItem](#ongetembeddeditem)|Wywołuje się `COleServerItem` , by uzyskać element reprezentujący cały dokument; służy do uzyskiwania elementu osadzonego. Wymagana implementacja.|
|[COleServerDoc::OnReactivateAndUndo](#onreactivateandundo)|Wywoływane przez platformę, aby cofnąć zmiany wprowadzone podczas edycji w miejscu.|
|[COleServerDoc::OnSetHostNames](#onsethostnames)|Wywoływane przez platformę, gdy kontener ustawia tytuł okna dla osadzonego obiektu.|
|[COleServerDoc::OnSetItemRects](#onsetitemrects)|Wywoływane przez platformę w celu umieszczenia okna ramki edycji w miejscu w oknie aplikacji kontenera.|
|[COleServerDoc::OnShowDocument](#onshowdocument)|Wywoływane przez platformę w celu pokazania lub ukrycia dokumentu.|

## <a name="remarks"></a>Uwagi

Dokument serwera może zawierać obiekty [COleServerItem](../../mfc/reference/coleserveritem-class.md) reprezentujące interfejs serwera do elementów osadzonych lub połączonych. Gdy aplikacja serwera jest uruchamiana przez kontener w celu edycji elementu osadzonego, element jest ładowany jako własny dokument serwera; Obiekt zawiera tylko jeden `COleServerItem` obiekt, składający się z całego dokumentu. `COleServerDoc` Gdy aplikacja serwera jest uruchamiana przez kontener w celu edycji elementu połączonego, istniejący dokument jest ładowany z dysku; część zawartości dokumentu zostanie wyróżniona w celu wskazania połączonego elementu.

`COleServerDoc`obiekty mogą również zawierać elementy klasy [COleClientItem](../../mfc/reference/coleclientitem-class.md) . Dzięki temu można tworzyć aplikacje kontenerów serwerów. Struktura zawiera funkcje do prawidłowego przechowywania `COleClientItem` elementów podczas `COleServerItem` obsługi obiektów.

Jeśli aplikacja serwera nie obsługuje linków, dokument serwera zawsze będzie zawierać tylko jeden element serwera, który reprezentuje cały osadzony obiekt jako dokument. Jeśli aplikacja serwera obsługuje linki, należy utworzyć element na serwerze za każdym razem, gdy wybór zostanie skopiowany do Schowka.

Aby użyć `COleServerDoc`, należy utworzyć klasę z klasy i zaimplementować funkcję członkowską [OnGetEmbeddedItem](#ongetembeddeditem) , która umożliwia serwerowi obsługę elementów osadzonych. Utwórz klasę z `COleServerItem` , aby zaimplementować elementy w dokumentach i zwrócić obiekty tej klasy z `OnGetEmbeddedItem`.

Aby można było obsługiwać połączone `COleServerDoc` elementy, udostępnia funkcję członkowską [OnGetLinkedItem](../../mfc/reference/colelinkingdoc-class.md#ongetlinkeditem) . Możesz użyć domyślnej implementacji lub zastąpić ją, jeśli masz własny sposób zarządzania elementami dokumentu.

Wymagana `COleServerDoc`jest jednopochodna Klasa dla każdego typu dokumentu serwera obsługiwanego przez aplikację. Na przykład jeśli aplikacja serwera obsługuje arkusze kalkulacyjne i wykresy, potrzebne `COleServerDoc`są klasy pochodne.

Aby uzyskać więcej informacji na temat serwerów, zobacz [artykuł serwery: Implementowanie serwera](../../mfc/servers-implementing-a-server.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

[COleDocument](../../mfc/reference/coledocument-class.md)

[COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)

`COleServerDoc`

## <a name="requirements"></a>Wymagania

**Nagłówek:** Afxole. h

##  <a name="activatedocobject"></a>COleServerDoc::ActivateDocObject

Aktywuje skojarzony dokument DocObject.

```
void ActivateDocObject();
```

### <a name="remarks"></a>Uwagi

Domyślnie program `COleServerDoc` nie obsługuje dokumentów aktywnych (nazywanych również DocObjects). Aby włączyć tę pomoc techniczną, zobacz [GetDocObjectServer](#getdocobjectserver) i Class [CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md).

##  <a name="activateinplace"></a>COleServerDoc::ActivateInPlace

Aktywuje element do edycji w miejscu.

```
BOOL ActivateInPlace();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie wartość 0 oznacza, że element jest w pełni otwarty.

### <a name="remarks"></a>Uwagi

Ta funkcja wykonuje wszystkie operacje wymagane do aktywacji w miejscu. Tworzy okno ramki w miejscu, uaktywnia go i zmienia rozmiar dla elementu, konfiguruje menu udostępnione i inne kontrolki, przewija element do widoku i ustawia fokus w oknie ramka w miejscu.

Ta funkcja jest wywoływana przez domyślną implementację [COleServerItem:: OnShow](../../mfc/reference/coleserveritem-class.md#onshow). Wywołaj tę funkcję, jeśli aplikacja obsługuje kolejną metodę aktywacji w miejscu (na przykład Play).

##  <a name="coleserverdoc"></a>COleServerDoc::COleServerDoc

Konstruuje `COleServerDoc` obiekt bez łączenia się z biblioteką DLL systemu OLE.

```
COleServerDoc();
```

### <a name="remarks"></a>Uwagi

Musisz wywołać [COleLinkingDoc:: Register](../../mfc/reference/colelinkingdoc-class.md#register) , aby otworzyć komunikację z OLE. Jeśli używasz [element COleTemplateServer](../../mfc/reference/coletemplateserver-class.md) w aplikacji `COleLinkingDoc::Register` , jest on wywoływany `OnNewDocument`przez `COleLinkingDoc`implementację, `OnOpenDocument`i `OnSaveDocument`.

##  <a name="createinplaceframe"></a>COleServerDoc::CreateInPlaceFrame

Struktura wywołuje tę funkcję, aby utworzyć okno ramowe do edycji w miejscu.

```
virtual COleIPFrameWnd* CreateInPlaceFrame(CWnd* pParentWnd);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Wskaźnik do okna nadrzędnego aplikacji kontenera.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do okna ramki w miejscu lub wartości NULL w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Implementacja domyślna używa informacji określonych w szablonie dokumentu do utworzenia ramki. Używany widok to pierwszy widok utworzony dla dokumentu. Ten widok jest tymczasowo odłączony od oryginalnej ramki i dołączony do nowo utworzonej ramki.

Jest to zaawansowany możliwy do zaawansowania.

##  <a name="deactivateandundo"></a>COleServerDoc::D eactivateAndUndo

Wywołaj tę funkcję, jeśli aplikacja obsługuje cofanie, a użytkownik wybierze opcję Cofnij po aktywowaniu elementu, ale przed jego edycją.

```
BOOL DeactivateAndUndo();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe po powodzeniu; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli aplikacja kontenera jest zapisywana przy użyciu biblioteka MFC, wywołanie tej funkcji powoduje wywoływanie [COleClientItem:: OnDeactivateAndUndo](../../mfc/reference/coleclientitem-class.md#ondeactivateandundo) , który dezaktywuje interfejs użytkownika serwera.

##  <a name="destroyinplaceframe"></a>COleServerDoc::D estroyInPlaceFrame

Struktura wywołuje tę funkcję, aby zniszczyć okno ramowe w miejscu i zwrócić okno dokumentu aplikacji serwera do jego stanu przed aktywacją w miejscu.

```
virtual void DestroyInPlaceFrame(COleIPFrameWnd* pFrameWnd);
```

### <a name="parameters"></a>Parametry

*pFrameWnd*<br/>
Wskaźnik do okna ramki w miejscu do zniszczenia.

### <a name="remarks"></a>Uwagi

Jest to zaawansowany możliwy do zaawansowania.

##  <a name="discardundostate"></a>COleServerDoc::D iscardUndoState

Jeśli użytkownik wykonuje operację edycji, która nie może zostać cofnięta, Wywołaj tę funkcję, aby wymusić odrzucanie informacji o stanie cofnięcia przez aplikację kontenera.

```
BOOL DiscardUndoState();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe po powodzeniu; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja jest zapewniana w taki sposób, że serwery obsługujące cofanie mogą zwolnić zasoby, które w przeciwnym razie byłyby wykorzystane przez informacje o stanie cofnięcia, których nie można użyć.

##  <a name="getclientsite"></a>COleServerDoc::GetClientSite

Pobiera wskaźnik do podstawowego `IOleClientSite` interfejsu.

```
LPOLECLIENTSITE GetClientSite() const;
```

### <a name="return-value"></a>Wartość zwracana

Pobiera wskaźnik do podstawowego interfejsu [IOleClientSite](/windows/win32/api/oleidl/nn-oleidl-ioleclientsite) .

##  <a name="getdocobjectserver"></a>COleServerDoc::GetDocObjectServer

Przesłoń tę funkcję, aby utworzyć `CDocObjectServer` nowy element i zwrócić do niego wskaźnik.

```
virtual CDocObjectServer* GetDocObjectServer(LPOLEDOCUMENTSITE pDocSite);
```

### <a name="parameters"></a>Parametry

*pDocSite*<br/>
Wskaźnik do `IOleDocumentSite` interfejsu, który będzie łączyć ten dokument z serwerem.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CDocObjectServer`; Wartość NULL, jeśli operacja nie powiodła się.

### <a name="remarks"></a>Uwagi

Po aktywowaniu serwera DocObject zwracający wskaźnik o wartości innej niż NULL pokazuje, że klient może obsługiwać DocObjects. Domyślna implementacja zwraca wartość NULL.

Typowa implementacja dokumentu, który obsługuje DocObjects, spowoduje po prostu przydzielenie `CDocObjectServer` nowego obiektu i przywrócenie go do obiektu wywołującego. Na przykład:

[!code-cpp[NVC_MFCOleServer#3](../../mfc/codesnippet/cpp/coleserverdoc-class_1.cpp)]

##  <a name="getembeddeditem"></a>COleServerDoc::GetEmbeddedItem

Wywołaj tę funkcję, aby uzyskać wskaźnik do elementu reprezentującego cały dokument.

```
COleServerItem* GetEmbeddedItem();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do elementu reprezentującego cały dokument; Wartość NULL, jeśli operacja nie powiodła się.

### <a name="remarks"></a>Uwagi

Wywołuje [COleServerDoc:: OnGetEmbeddedItem](#ongetembeddeditem), funkcję wirtualną bez implementacji domyślnej.

##  <a name="getitemcliprect"></a>  COleServerDoc::GetItemClipRect

Wywołaj `GetItemClipRect` funkcję członkowską, aby uzyskać współrzędne prostokąta wycinka elementu, który jest edytowany w miejscu.

```
void GetItemClipRect(LPRECT lpClipRect) const;
```

### <a name="parameters"></a>Parametry

*lpClipRect*<br/>
Wskaźnik do `RECT` struktury `CRect` lub obiektu, aby uzyskać współrzędne prostokąta wycinka elementu.

### <a name="remarks"></a>Uwagi

Współrzędne są w pikselach względem obszaru klienckiego okna aplikacji kontenera.

Rysowanie nie powinno następować poza prostokątem przycinania. Zwykle rysowanie jest automatycznie ograniczone. Użyj tej funkcji, aby określić, czy użytkownik przewinie się poza widoczną częścią dokumentu; Jeśli tak, przewiń dokument kontenera w miarę potrzeby za pomocą wywołania [ScrollContainerBy](#scrollcontainerby).

##  <a name="getitemposition"></a>COleServerDoc::GetItemPosition

Wywołaj `GetItemPosition` funkcję członkowską, aby uzyskać współrzędne edytowanego elementu.

```
void GetItemPosition(LPRECT lpPosRect) const;
```

### <a name="parameters"></a>Parametry

*lpPosRect*<br/>
Wskaźnik do `RECT` struktury `CRect` lub obiektu, aby otrzymać współrzędne elementu.

### <a name="remarks"></a>Uwagi

Współrzędne są w pikselach względem obszaru klienckiego okna aplikacji kontenera.

Położenie elementu można porównać z bieżącym prostokątem przycinania, aby określić zakres, do którego element jest widoczny (lub niewidoczny) na ekranie.

##  <a name="getzoomfactor"></a>COleServerDoc::GetZoomFactor

Funkcja `GetZoomFactor` członkowska określa "współczynnik powiększenia" elementu, który został aktywowany do edycji w miejscu.

```
BOOL GetZoomFactor(
    LPSIZE lpSizeNum = NULL,
    LPSIZE lpSizeDenom = NULL,
    LPCRECT lpPosRect = NULL) const;
```

### <a name="parameters"></a>Parametry

*lpSizeNum*<br/>
Wskaźnik do obiektu klasy `CSize` , w którym będzie przechowywany licznik współczynnika powiększenia. Może mieć wartość NULL.

*lpSizeDenom*<br/>
Wskaźnik do obiektu klasy `CSize` , który będzie przechowywać mianownik współczynnika powiększenia. Może mieć wartość NULL.

*lpPosRect*<br/>
Wskaźnik do obiektu klasy `CRect` opisującego nową pozycję elementu. Jeśli ten argument ma wartość NULL, funkcja używa bieżącej pozycji elementu.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli element jest aktywowany do edycji w miejscu, a jego współczynnik powiększenia jest inny niż 100% (1:1); w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Współczynnik powiększenia (w pikselach) jest proporcją rozmiaru elementu do jego bieżącego zakresu. Jeśli aplikacja kontenera nie ustawił zakresu elementu, jest używany jego naturalny zakres (określony przez [COleServerItem:: OnGetExtent](../../mfc/reference/coleserveritem-class.md#ongetextent)).

Funkcja ustawia swoje pierwsze dwa argumenty do licznika i mianownika "współczynnika powiększenia" elementu. Jeśli element nie jest edytowany w miejscu, funkcja ustawia te argumenty na wartość domyślną 100% (lub 1:1) i zwraca zero. Aby uzyskać więcej informacji, zobacz Uwagi techniczne 40, [MFC/OLE w miejscu zmiany rozmiaru i](../../mfc/tn040-mfc-ole-in-place-resizing-and-zooming.md)powiększania.

##  <a name="isdocobject"></a>COleServerDoc::IsDocObject

Określa, czy dokument jest DocObject.

```
BOOL IsDocObject() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli dokument jest DocObject; w przeciwnym razie FALSE.

##  <a name="isembedded"></a>COleServerDoc:: isembedded

Wywołaj `IsEmbedded` funkcję członkowską, aby określić, czy dokument reprezentuje obiekt osadzony w kontenerze.

```
BOOL IsEmbedded() const;
```

### <a name="return-value"></a>Wartość zwracana

Różne od zera, `COleServerDoc` Jeśli obiekt jest dokumentem, który reprezentuje obiekt osadzony w kontenerze; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Dokument załadowany z pliku nie jest osadzony, mimo że może być manipulowany przez aplikację kontenera jako link. Dokument osadzony w dokumencie kontenera jest traktowany jako osadzony.

##  <a name="isinplaceactive"></a>COleServerDoc::IsInPlaceActive

Wywołaj `IsInPlaceActive` funkcję członkowską, aby określić, czy element jest obecnie w stanie aktywnym w miejscu.

```
BOOL IsInPlaceActive() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli `COleServerDoc` obiekt jest aktywny w miejscu; w przeciwnym razie 0.

##  <a name="notifychanged"></a>  COleServerDoc::NotifyChanged

Wywołaj tę funkcję, aby powiadomić wszystkie połączone elementy połączone z dokumentem, że dokument został zmieniony.

```
void NotifyChanged();
```

### <a name="remarks"></a>Uwagi

Zazwyczaj należy wywołać tę funkcję po zmianie przez użytkownika atrybutu globalnego, takiego jak wymiary dokumentu serwera. Jeśli element OLE jest połączony z dokumentem z automatycznym łączem, element zostanie zaktualizowany w celu odzwierciedlenia zmian. W przypadku aplikacji kontenerów pisanych przy użyciu biblioteka MFC [](../../mfc/reference/coleclientitem-class.md#onchange) wywoływana `COleClientItem` jest funkcja członkowska onchanga klasy.

> [!NOTE]
>  Ta funkcja jest dołączona do zgodności z mechanizmem OLE 1. Nowe aplikacje powinny używać [UpdateAllItems](#updateallitems).

##  <a name="notifyclosed"></a>COleServerDoc::NotifyClosed

Wywołaj tę funkcję, aby powiadomić kontenery, że dokument został zamknięty.

```
void NotifyClosed();
```

### <a name="remarks"></a>Uwagi

Gdy użytkownik wybierze polecenie Zamknij z menu plik, `NotifyClosed` jest wywoływana przez `COleServerDoc`implementację funkcji składowej [OnCloseDocument](../../mfc/reference/cdocument-class.md#onclosedocument) . W przypadku aplikacji kontenerów pisanych przy użyciu biblioteka MFC [](../../mfc/reference/coleclientitem-class.md#onchange) wywoływana `COleClientItem` jest funkcja członkowska onchanga klasy.

##  <a name="notifyrename"></a>COleServerDoc::NotifyRename

Wywołaj tę funkcję, gdy użytkownik zmienia nazwę dokumentu na serwerze.

```
void NotifyRename(LPCTSTR lpszNewName);
```

### <a name="parameters"></a>Parametry

*lpszNewName*<br/>
Wskaźnik na ciąg określający nową nazwę dokumentu serwera; zwykle jest to w pełni kwalifikowana ścieżka.

### <a name="remarks"></a>Uwagi

Gdy użytkownik wybierze polecenie Zapisz jako z menu plik, `NotifyRename` jest wywoływana przez `COleServerDoc`implementację funkcji składowej [OnSaveDocument](../../mfc/reference/cdocument-class.md#onsavedocument) . Ta funkcja powiadamia pliki DLL systemu OLE, które z kolei powiadamiają kontenery. W przypadku aplikacji kontenerów pisanych przy użyciu biblioteka MFC [](../../mfc/reference/coleclientitem-class.md#onchange) wywoływana `COleClientItem` jest funkcja członkowska onchanga klasy.

##  <a name="notifysaved"></a>COleServerDoc::NotifySaved

Wywołaj tę funkcję po zapisaniu dokumentu na serwerze przez użytkownika.

```
void NotifySaved();
```

### <a name="remarks"></a>Uwagi

Gdy użytkownik wybierze polecenie Zapisz z menu plik, `NotifySaved` zostanie wywołane przez `COleServerDoc`implementację [OnSaveDocument](../../mfc/reference/cdocument-class.md#onsavedocument). Ta funkcja powiadamia pliki DLL systemu OLE, które z kolei powiadamiają kontenery. W przypadku aplikacji kontenerów pisanych przy użyciu biblioteka MFC [](../../mfc/reference/coleclientitem-class.md#onchange) wywoływana `COleClientItem` jest funkcja członkowska onchanga klasy.

##  <a name="onclose"></a>COleServerDoc:: OnClose

Wywoływane przez platformę, gdy kontener żąda zamknięcia dokumentu serwera.

```
virtual void OnClose(OLECLOSE dwCloseOption);
```

### <a name="parameters"></a>Parametry

*dwCloseOption*<br/>
Wartość z wyliczenia OLECLOSE. Ten parametr może mieć jedną z następujących wartości:

- OLECLOSE_SAVEIFDIRTY plik jest zapisywany, jeśli został zmodyfikowany.

- OLECLOSE_NOSAVE plik jest zamknięty bez zapisywania.

- OLECLOSE_PROMPTSAVE Jeśli plik został zmodyfikowany, użytkownik jest monitowany o zapisanie go.

### <a name="remarks"></a>Uwagi

Domyślne wywołania `CDocument::OnCloseDocument`implementacji.

Aby uzyskać więcej informacji i dodatkowe wartości, zobacz [OLECLOSE](/windows/win32/api/oleidl/ne-oleidl-oleclose) w Windows SDK.

##  <a name="ondeactivate"></a>COleServerDoc:: OnDeactivate

Wywoływane przez platformę, gdy użytkownik dezaktywuje element osadzony lub połączony, który jest obecnie aktywny.

```
virtual void OnDeactivate();
```

### <a name="remarks"></a>Uwagi

Ta funkcja przywraca interfejs użytkownika aplikacji kontenera do jego oryginalnego stanu i niszczy wszystkie menu i inne kontrolki, które zostały utworzone dla aktywacji w miejscu.

Informacje o stanie cofania powinny być bezwarunkowo wydane w tym momencie.

Aby uzyskać więcej informacji, zobacz [Aktywacja](../../mfc/activation-cpp.md)artykułu.

##  <a name="ondeactivateui"></a>COleServerDoc::OnDeactivateUI

Wywoływana, gdy użytkownik dezaktywuje element, który został aktywowany w miejscu.

```
virtual void OnDeactivateUI(BOOL bUndoable);
```

### <a name="parameters"></a>Parametry

*bUndoable*<br/>
Określa, czy zmiany edycyjne mogą być cofnięte.

### <a name="remarks"></a>Uwagi

Ta funkcja przywraca interfejs użytkownika aplikacji kontenera do jego oryginalnego stanu, ukrywając wszystkie menu i inne kontrolki, które zostały utworzone dla aktywacji w miejscu.

Struktura zawsze ustawia *bUndoable* na false. Jeśli serwer obsługuje polecenie Cofnij i istnieje operacja, która może zostać cofnięta, wywołaj implementację klasy podstawowej z *bUndoable* ustawioną na wartość true.

##  <a name="ondocwindowactivate"></a>COleServerDoc::OnDocWindowActivate

Struktura wywołuje tę funkcję, aby aktywować lub dezaktywować okno dokumentu do edycji w miejscu.

```
virtual void OnDocWindowActivate(BOOL bActivate);
```

### <a name="parameters"></a>Parametry

*bActivate*<br/>
Określa, czy okno dokumentu ma zostać aktywowane czy dezaktywowane.

### <a name="remarks"></a>Uwagi

Implementacja domyślna usuwa lub dodaje elementy interfejsu użytkownika na poziomie ramki odpowiednio do potrzeb. Przesłoń tę funkcję, jeśli chcesz wykonać dodatkowe akcje, gdy dokument zawierający element zostanie aktywowany lub zdezaktywowany.

Aby uzyskać więcej informacji, zobacz [Aktywacja](../../mfc/activation-cpp.md)artykułu.

##  <a name="onexecolecmd"></a>COleServerDoc::OnExecOleCmd

Struktura wywołuje tę funkcję, aby wykonać określone polecenie lub wyświetlić pomoc dla polecenia.

```
virtual HRESULT OnExecOleCmd(
    const GUID* pguidCmdGroup,
    DWORD nCmdID,
    DWORD nCmdExecOpt,
    VARIANTARG* pvarargIn,
    VARIANTARG* pvarargOut);
```

### <a name="parameters"></a>Parametry

*pguidCmdGroup*<br/>
Wskaźnik do identyfikatora GUID, który identyfikuje zestaw poleceń. Może mieć wartość NULL, aby wskazać domyślną grupę poleceń.

*nCmdID*<br/>
Polecenie do wykonania. Musi znajdować się w grupie identyfikowanej przez *pguidCmdGroup*.

*nCmdExecOut*<br/>
Sposób, w jaki obiekt powinien wykonać polecenie, co najmniej jedną z następujących wartości z wyliczenia OLECMDEXECOPT:

OLECMDEXECOPT_DODEFAULT

OLECMDEXECOPT_PROMPTUSER

OLECMDEXECOPT_DONTPROMPTUSER

OLECMDEXECOPT_SHOWHELP

*pvarargIn*<br/>
Wskaźnik do elementu VARIANTARG zawierającego argumenty wejściowe dla polecenia. Może mieć wartość NULL.

*pvarargOut*<br/>
Wskaźnik do elementu VARIANTARG, aby otrzymać wyjściowe wartości zwracane z polecenia. Może mieć wartość NULL.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK, jeśli pomyślne; w przeciwnym razie jeden z następujących kodów błędów:

|Wartość|Opis|
|-----------|-----------------|
|E_UNEXPECTED|Wystąpił nieoczekiwany błąd|
|E_FAIL|Wystąpił błąd|
|E_NOTIMPL|Wskazuje, że biblioteka MFC powinna próbować przetłumaczyć i wysłać polecenie|
|OLECMDERR_E_UNKNOWNGROUP|*pguidCmdGroup* ma wartość różną od null, ale nie określa uznanej grupy poleceń|
|OLECMDERR_E_NOTSUPPORTED|*nCmdID* nie jest rozpoznawana jako prawidłowe polecenie w grupie *pguidCmdGroup*|
|OLECMDERR_DISABLED|Polecenie identyfikowane przez *nCmdID* jest wyłączone i nie można go wykonać|
|OLECMDERR_NOHELP|Obiekt wywołujący prosi o pomoc dotyczącą polecenia identyfikowanego przez *nCmdID* , ale pomoc nie jest dostępna|
|OLECMDERR_CANCELED|Użytkownik anulował wykonywanie|

### <a name="remarks"></a>Uwagi

`COleCmdUI`może służyć do włączania, aktualizowania i ustawiania innych właściwości poleceń interfejsu użytkownika DocObject. Po zainicjowaniu poleceń można wykonać je za pomocą `OnExecOleCmd`polecenia.

Struktura wywołuje funkcję przed podjęciem próby przetłumaczenia i wysłania polecenia dokumentu OLE. Nie musisz przesłonić tej funkcji do obsługi standardowych poleceń dokumentu OLE, ale musisz podać przesłonięcie tej funkcji, jeśli chcesz obsługiwać własne polecenia niestandardowe lub obsłużyć polecenia, które akceptują parametry lub zwracają wyniki.

Większość poleceń nie przyjmuje argumentów ani zwracanych wartości. W przypadku większości poleceń obiekt wywołujący może przekazać wartości NULL dla *pvarargIn* i *pvarargOut*. Dla poleceń, które oczekują wartości wejściowych, obiekt wywołujący może zadeklarować i zainicjować zmienną VARIANTARG i przekazać wskaźnik do zmiennej w *pvarargIn*. Dla poleceń, które wymagają pojedynczej wartości, argument może być przechowywany bezpośrednio w VARIANTARG i przekazywać do funkcji. Wiele argumentów musi być spakowanych w VARIANTARG przy użyciu jednego z obsługiwanych typów (takich jak `IDispatch` i SAFEARRAY).

Podobnie, jeśli polecenie zwraca argumenty, oczekiwano, że obiekt wywołujący deklaruje VARIANTARG, zainicjuj go VT_EMPTY i przekaż jego adres w *pvarargOut*. Jeśli polecenie zwraca pojedynczą wartość, obiekt może przechowywać tę wartość bezpośrednio w *pvarargOut*. Wiele wartości wyjściowych musi być spakowana w sposób odpowiedni dla VARIANTARG.

Implementacja klasy podstawowej tej funkcji spowoduje przeprowadzenie struktur OLE_COMMAND_MAP skojarzonych z elementem docelowym polecenia i próbę wysłania polecenia do odpowiedniej procedury obsługi. Implementacja klasy bazowej działa tylko z poleceniami, które nie akceptują argumentów ani zwracanych wartości. Jeśli musisz obsługiwać polecenia, które przyjmują argumenty lub wartości zwracane, należy przesłonić tę funkcję i wspólnie z parametrami *pvarargIn* i *pvarargOut* .

##  <a name="onframewindowactivate"></a>COleServerDoc::OnFrameWindowActivate

Struktura wywołuje tę funkcję, gdy okno ramki aplikacji kontenera jest aktywowane lub dezaktywowane.

```
virtual void OnFrameWindowActivate(BOOL bActivate);
```

### <a name="parameters"></a>Parametry

*bActivate*<br/>
Określa, czy okno ramki ma zostać aktywowane czy dezaktywowane.

### <a name="remarks"></a>Uwagi

Domyślna implementacja anuluje wszystkie tryby pomocy, w których może znajdować się okno ramek. Zastąp tę funkcję, jeśli chcesz przeprowadzić przetwarzanie specjalne, gdy okno ramki jest aktywowane lub dezaktywowane.

Aby uzyskać więcej informacji, zobacz [Aktywacja](../../mfc/activation-cpp.md)artykułu.

##  <a name="ongetembeddeditem"></a>COleServerDoc:: OnGetEmbeddedItem

Wywoływane przez platformę, gdy aplikacja kontenera wywołuje aplikację serwera, aby utworzyć lub edytować element osadzony.

```
virtual COleServerItem* OnGetEmbeddedItem() = 0;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do elementu reprezentującego cały dokument; Wartość NULL, jeśli operacja nie powiodła się.

### <a name="remarks"></a>Uwagi

Nie istnieje domyślna implementacja. Należy zastąpić tę funkcję, aby zwrócić element reprezentujący cały dokument. Ta wartość zwracana powinna być obiektem `COleServerItem`klasy pochodnej.

##  <a name="onreactivateandundo"></a>COleServerDoc::OnReactivateAndUndo

Struktura wywołuje tę funkcję, gdy użytkownik zdecyduje się cofnąć zmiany wprowadzone do elementu, który został aktywowany, zmieniony, a następnie zdezaktywowany.

```
virtual BOOL OnReactivateAndUndo();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Implementacja domyślna to Nothing, z wyjątkiem zwraca wartość FALSE, aby wskazać błąd.

Zastąp tę funkcję, jeśli aplikacja obsługuje cofanie. Zazwyczaj można wykonać operację cofania, a następnie aktywować element, wywołując `ActivateInPlace`metodę. Jeśli aplikacja kontenera jest zapisywana przy użyciu biblioteka MFC, wywołanie `COleClientItem::ReactivateAndUndo` powoduje wywołanie tej funkcji.

##  <a name="onresizeborder"></a>COleServerDoc::OnResizeBorder

Struktura wywołuje tę funkcję, gdy zmienia się rozmiar okien ramek aplikacji kontenera.

```
virtual void OnResizeBorder(
    LPCRECT lpRectBorder,
    LPOLEINPLACEUIWINDOW lpUIWindow,
    BOOL bFrame);
```

### <a name="parameters"></a>Parametry

*lpRectBorder*<br/>
Wskaźnik do `RECT` struktury `CRect` lub obiektu, który określa współrzędne obramowania.

*lpUIWindow*<br/>
Wskaźnik do obiektu klasy `IOleInPlaceUIWindow` , który jest właścicielem bieżącej sesji edycji w miejscu.

*bFrame*<br/>
Ma wartość TRUE, jeśli *lpUIWindow* wskazuje okno ramki najwyższego poziomu aplikacji kontenera lub wartość FAŁSZ, jeśli *lpUIWindow* wskazuje na okno ramki poziomu dokumentu aplikacji kontenera.

### <a name="remarks"></a>Uwagi

Ta funkcja zmienia rozmiar i dostosowuje paski narzędzi oraz inne elementy interfejsu użytkownika zgodnie z nowym rozmiarem okna.

Aby uzyskać więcej informacji, zobacz [IOleInPlaceUIWindow](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceuiwindow) w Windows SDK.

Jest to zaawansowany możliwy do zaawansowania.

##  <a name="onsethostnames"></a>COleServerDoc::OnSetHostNames

Wywoływane przez platformę, gdy kontener ustawia lub zmienia nazwy hostów dla tego dokumentu.

```
virtual void OnSetHostNames(
    LPCTSTR lpszHost,
    LPCTSTR lpszHostObj);
```

### <a name="parameters"></a>Parametry

*lpszHost*<br/>
Wskaźnik na ciąg, który określa nazwę aplikacji kontenera.

*lpszHostObj*<br/>
Wskaźnik na ciąg, który określa nazwę kontenera dla dokumentu.

### <a name="remarks"></a>Uwagi

Domyślna implementacja zmienia tytuł dokumentu dla wszystkich widoków odnoszących się do tego dokumentu.

Zastąp tę funkcję, jeśli aplikacja ustawi tytuły przy użyciu innego mechanizmu.

##  <a name="onsetitemrects"></a>COleServerDoc::OnSetItemRects

Struktura wywołuje tę funkcję, aby umieścić okno ramki edycji w miejscu w oknie ramka aplikacji kontenera.

```
virtual void OnSetItemRects(
    LPCRECT lpPosRect,
    LPCRECT lpClipRect);
```

### <a name="parameters"></a>Parametry

*lpPosRect*<br/>
Wskaźnik do `RECT` struktury `CRect` lub obiektu, który określa położenie okna ramki w miejscu względem obszaru klienckiego aplikacji kontenera.

*lpClipRect*<br/>
Wskaźnik do `RECT` struktury `CRect` lub obiektu, który określa prostokąt przycinania okna ramki w miejscu względem obszaru klienckiego aplikacji kontenera.

### <a name="remarks"></a>Uwagi

Zastąp tę funkcję, aby zaktualizować współczynnik powiększenia widoku, w razie potrzeby.

Ta funkcja jest zazwyczaj wywoływana w odpowiedzi na `RequestPositionChange` wywołanie, chociaż może być wywoływana w dowolnym momencie przez kontener, aby zażądać zmiany położenia dla elementu w miejscu.

##  <a name="onshowcontrolbars"></a>COleServerDoc::OnShowControlBars

Struktura wywołuje tę funkcję, aby pokazać lub ukryć paski kontroli aplikacji serwera skojarzone z oknem ramki identyfikowanym przez *pFrameWnd*.

```
virtual void OnShowControlBars(
    CFrameWnd* pFrameWnd,
    BOOL bShow);
```

### <a name="parameters"></a>Parametry

*pFrameWnd*<br/>
Wskaźnik do okna ramki, którego paski kontroli mają być ukryte lub pokazane.

*bShow*<br/>
Określa, czy paski kontroli są wyświetlane, czy ukryte.

### <a name="remarks"></a>Uwagi

Domyślna implementacja wylicza wszystkie paski kontroli należące do tego okna ramki i ukrywa je lub pokazuje.

##  <a name="onshowdocument"></a>COleServerDoc::OnShowDocument

Struktura wywołuje funkcję, `OnShowDocument` gdy dokument serwera musi być ukryty lub pokazany.

```
virtual void OnShowDocument(BOOL bShow);
```

### <a name="parameters"></a>Parametry

*bShow*<br/>
Określa, czy interfejs użytkownika do dokumentu ma być pokazywany czy ukryty.

### <a name="remarks"></a>Uwagi

Jeśli *bShow* ma wartość true, domyślna implementacja aktywuje aplikację serwera, jeśli to konieczne, i powoduje, że aplikacja kontenera przewinie swoje okno, aby element był widoczny. Jeśli *bShow* ma wartość false, implementacja domyślna dezaktywuje element za pomocą wywołania do `OnDeactivate`, a następnie niszczy lub ukrywa wszystkie okna ramowe, które zostały utworzone dla dokumentu, z wyjątkiem pierwszego. Jeśli żadne widoczne dokumenty nie zostaną zachowane, domyślna implementacja spowoduje ukrycie aplikacji serwera.

##  <a name="onupdatedocument"></a>COleServerDoc::OnUpdateDocument

Wywoływane przez platformę podczas zapisywania dokumentu, który jest elementem osadzonym w dokumencie złożonym.

```
virtual BOOL OnUpdateDocument();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli dokument został pomyślnie zaktualizowany; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Domyślna implementacja wywołuje funkcje członkowskie [COleServerDoc:: NotifySaved](#notifysaved) i [COleServerDoc:: SaveEmbedding](#saveembedding) , a następnie oznacza dokument jako czysty. Zastąp tę funkcję, jeśli chcesz przeprowadzić przetwarzanie specjalne podczas aktualizowania elementu osadzonego.

##  <a name="requestpositionchange"></a>COleServerDoc::RequestPositionChange

Wywołaj tę funkcję elementu członkowskiego, aby aplikacja kontenera zmieniła położenie elementu.

```
void RequestPositionChange(LPCRECT lpPosRect);
```

### <a name="parameters"></a>Parametry

*lpPosRect*<br/>
Wskaźnik do `RECT` struktury `CRect` lub obiektu zawierającego nowe położenie elementu.

### <a name="remarks"></a>Uwagi

Ta funkcja jest zwykle wywoływana (w połączeniu z `UpdateAllItems`), gdy zmieniono dane w miejscu aktywnym. Po tym wywołaniu kontener może lub nie może wykonać zmiany przez wywołanie metody `OnSetItemRects`. Pozycja w wyniku może się różnić od żądanego.

##  <a name="saveembedding"></a>COleServerDoc::SaveEmbedding

Wywołaj tę funkcję, aby poinformować aplikację kontenera o zapisaniu osadzonego obiektu.

```
void SaveEmbedding();
```

### <a name="remarks"></a>Uwagi

Ta funkcja jest wywoływana automatycznie z `OnUpdateDocument`programu. Należy zauważyć, że ta funkcja powoduje aktualizację elementu na dysku, więc jest zazwyczaj wywoływana tylko w wyniku określonej akcji użytkownika.

##  <a name="scrollcontainerby"></a>  COleServerDoc::ScrollContainerBy

Wywołaj funkcję `sizeScroll` elementuczłonkowskiego,abyprzewinąćdokumentkonteneraoilośćwpikselach`ScrollContainerBy` wskazywanych przez.

```
BOOL ScrollContainerBy(CSize sizeScroll);
```

### <a name="parameters"></a>Parametry

*sizeScroll*<br/>
Wskazuje, jak daleko jest dokument kontenera do przewinięcia.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wartości dodatnie oznaczają przewijanie w dół i w prawo; wartości ujemne oznaczają przewijanie w górę i w lewo.

##  <a name="updateallitems"></a>COleServerDoc::UpdateAllItems

Wywołaj tę funkcję, aby powiadomić wszystkie połączone elementy połączone z dokumentem, że dokument został zmieniony.

```
void UpdateAllItems(
    COleServerItem* pSender,
    LPARAM lHint = 0L,
    CObject* pHint = NULL,
    DVASPECT nDrawAspect = DVASPECT_CONTENT);
```

### <a name="parameters"></a>Parametry

*pSender*<br/>
Wskaźnik do elementu, który zmodyfikował dokument, lub wartość NULL, jeśli wszystkie elementy mają zostać zaktualizowane.

*lHint*<br/>
Zawiera informacje na temat modyfikacji.

*pHint*<br/>
Wskaźnik do obiektu przechowującego informacje o modyfikacji.

*nDrawAspect*<br/>
Określa sposób rysowania elementu. Jest to wartość z wyliczenia DVASPECT. Ten parametr może mieć jedną z następujących wartości:

- Element DVASPECT_CONTENT jest reprezentowany w taki sposób, że może być wyświetlany jako osadzony obiekt wewnątrz jego kontenera.

- Element DVASPECT_THUMBNAIL jest renderowany w reprezentacji "miniatury", aby można go było wyświetlić w narzędziu do przeglądania.

- Element DVASPECT_ICON jest reprezentowany przez ikonę.

- Element DVASPECT_DOCPRINT jest reprezentowany tak, jakby był wydrukowany przy użyciu polecenia Print z menu plik.

### <a name="remarks"></a>Uwagi

Ta funkcja jest zazwyczaj wywoływana po zmianie dokumentu serwera przez użytkownika. Jeśli element OLE jest połączony z dokumentem z automatycznym łączem, element zostanie zaktualizowany w celu odzwierciedlenia zmian. W przypadku aplikacji kontenerów pisanych przy użyciu biblioteka MFC [](../../mfc/reference/coleclientitem-class.md#onchange) wywoływana `COleClientItem` jest funkcja członkowska onchanga klasy.

`OnUpdate` Ta funkcja wywołuje funkcję członkowską dla każdego z elementów dokumentu z wyjątkiem elementu wysyłającego, przekazując *pHint*, *lHint*i *nDrawAspect*. Te parametry służą do przekazywania informacji o zmianach wprowadzonych do dokumentu. Można kodować informacje przy użyciu *lHint* lub zdefiniować `CObject`klasę pochodną do przechowywania informacji o zmianach i przekazać obiekt tej klasy przy użyciu *pHint*. Przesłoń funkcję `COleServerItem`członkowskąw klasie pochodnej, aby zoptymalizować aktualizację poszczególnych elementów w zależności od tego, czy prezentacja została zmieniona. `OnUpdate`

## <a name="see-also"></a>Zobacz także

[Przykład HIERSVR MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleDocument](../../mfc/reference/coledocument-class.md)<br/>
[Klasa COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)<br/>
[Klasa COleTemplateServer](../../mfc/reference/coletemplateserver-class.md)
