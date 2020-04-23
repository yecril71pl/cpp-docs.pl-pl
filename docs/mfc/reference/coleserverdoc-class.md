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
ms.openlocfilehash: 8e75ec5c00c614a225a059a2b3cf97a7a307c61c
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753776"
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
|[COleServerDoc::DeaktywowaćAndUndo](#deactivateandundo)|Dezaktywuje interfejs użytkownika serwera.|
|[COleServerDoc::DiscardUndoState](#discardundostate)|Odrzuca informacje o stanie cofania.|
|[COleServerDoc::GetClientSite](#getclientsite)|Pobiera wskaźnik do interfejsu `IOleClientSite` źródłowego.|
|[COleServerDoc::GetEmbeddedItem](#getembeddeditem)|Zwraca wskaźnik do elementu reprezentującego cały dokument.|
|[COleServerDoc::GetItemClipRect](#getitemcliprect)|Zwraca bieżący prostokąt przycinania do edycji w miejscu.|
|[COleServerDoc::GetItemPosition](#getitemposition)|Zwraca bieżący prostokąt położenia, względem obszaru klienta aplikacji kontenera, do edycji w miejscu.|
|[COleServerDoc::GetZoomFactor](#getzoomfactor)|Zwraca współczynnik powiększenia w pikselach.|
|[COleServerDoc::IsDocObject](#isdocobject)|Określa, czy dokument jest DocObject.|
|[COleServerDoc::IsEmbedded](#isembedded)|Wskazuje, czy dokument jest osadzony w dokumencie kontenera, czy jest uruchomiony w trybie autonomicznym.|
|[COleServerDoc::IsInPlaceActive](#isinplaceactive)|Zwraca wartość PRAWDA, jeśli element jest aktualnie aktywowany na swoim miejscu.|
|[COleServerDoc::NotifyZmieniony](#notifychanged)|Powiadamia kontenery, że użytkownik zmienił dokument.|
|[COleServerDoc::NotifyClosed](#notifyclosed)|Powiadamia kontenery, że użytkownik zamknął dokument.|
|[COleServerDoc::NotifyRename](#notifyrename)|Powiadamia kontenery, że użytkownik zmienił nazwę dokumentu.|
|[COleServerDoc::NotifySaved](#notifysaved)|Powiadamia kontenery, że użytkownik zapisał dokument.|
|[COleServerDoc::OnDeaktywacji](#ondeactivate)|Wywoływane przez strukturę, gdy użytkownik dezaktywuje element, który został aktywowany w miejscu.|
|[COleServerDoc::OnDeactivateui](#ondeactivateui)|Wywoływana przez strukturę do niszczenia formantów i innych elementów interfejsu użytkownika utworzonych do aktywacji w miejscu.|
|[COleServerDoc::OnDocWindowActivate](#ondocwindowactivate)|Wywoływana przez strukturę, gdy okno ramki dokumentu kontenera jest aktywowany lub dezaktywowany.|
|[COleServerDoc::OnResizeBorder](#onresizeborder)|Wywoływana przez strukturę, gdy rozmiar okna ramki lub okna dokumentu aplikacji kontenera jest zmieniany.|
|[COleServerDoc::OnShowControlBars](#onshowcontrolbars)|Wywoływana przez strukturę do pokazywania lub ukrywania pasków sterowania do edycji w miejscu.|
|[COleServerDoc::OnUpdateDocument](#onupdatedocument)|Wywoływane przez platformę, gdy dokument serwera, który jest elementem osadzonym jest zapisywany, aktualizowanie kopii kontenera elementu.|
|[COleServerDoc::RequestPositionChange](#requestpositionchange)|Zmienia położenie ramki edycji w miejscu.|
|[COleServerDoc::SaveEmbedding](#saveembedding)|Informuje aplikację kontenera, aby zapisać dokument.|
|[COleServerDoc::ScrollContainerBy](#scrollcontainerby)|Przewija dokument kontenera.|
|[COleServerDoc::UpdateAllItems](#updateallitems)|Powiadamia kontenery, że użytkownik zmienił dokument.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[COleServerDoc::CreateInPlaceFrame](#createinplaceframe)|Wywoływana przez strukturę, aby utworzyć okno ramki do edycji w miejscu.|
|[COleServerDoc::DestroyInPlaceFrame](#destroyinplaceframe)|Wywoływana przez strukturę, aby zniszczyć okno ramki do edycji w miejscu.|
|[COleServerDoc::Serwer GetDocObjectServer](#getdocobjectserver)|Zastąpuj tę funkcję, aby utworzyć nowy `CDocObjectServer` obiekt i wskazać, że ten dokument jest kontenerem DocObject.|
|[COleServerDoc::OnKrówka](#onclose)|Wywoływane przez strukturę, gdy kontener żąda zamknięcia dokumentu.|
|[COleServerDoc::OnExecOleCmd](#onexecolecmd)|Wykonuje określone polecenie lub wyświetla pomoc dla polecenia.|
|[COleServerDoc::OnFrameWindowActivate](#onframewindowactivate)|Wywoływana przez strukturę, gdy okno ramki kontenera jest aktywowany lub dezaktywowany.|
|[COleServerDoc::OnGetEmbeddedItem](#ongetembeddeditem)|Wywołany, `COleServerItem` aby uzyskać, który reprezentuje cały dokument; używane do uzyskania elementu osadzonego. Wymagana implementacja.|
|[COleServerDoc::OnReactivateAndUndo](#onreactivateandundo)|Wywoływana przez strukturę, aby cofnąć zmiany wprowadzone podczas edycji w miejscu.|
|[COleServerDoc::OnSetHostNames](#onsethostnames)|Wywoływane przez strukturę, gdy kontener ustawia tytuł okna dla obiektu osadzonego.|
|[COleServerDoc::OnSetItemRects](#onsetitemrects)|Wywoływana przez strukturę do umieszczania okna ramki edycji w miejscu w oknie aplikacji kontenera.|
|[COleServerDoc::OnShowDocument](#onshowdocument)|Wywoływana przez strukturę, aby pokazać lub ukryć dokument.|

## <a name="remarks"></a>Uwagi

Dokument serwera może zawierać obiekty [COleServerItem,](../../mfc/reference/coleserveritem-class.md) które reprezentują interfejs serwera do elementów osadzonych lub połączonych. Gdy aplikacja serwera jest uruchamiana przez kontener do edycji elementu osadzonego, element jest ładowany jako własny dokument serwera; `COleServerDoc` obiekt zawiera tylko `COleServerItem` jeden obiekt, składający się z całego dokumentu. Gdy aplikacja serwera jest uruchamiana przez kontener w celu edycji elementu połączonego, istniejący dokument jest ładowany z dysku; część zawartości dokumentu jest podświetlona, aby wskazać połączony element.

`COleServerDoc`obiekty mogą również zawierać elementy [COleClientItem](../../mfc/reference/coleclientitem-class.md) klasy. Dzięki temu można tworzyć aplikacje serwera kontenera. Struktura zapewnia funkcje, aby `COleClientItem` prawidłowo przechowywać `COleServerItem` elementy podczas obsługi obiektów.

Jeśli aplikacja serwera nie obsługuje łączy, dokument serwera zawsze będzie zawierał tylko jeden element serwera, który reprezentuje cały osadzony obiekt jako dokument. Jeśli aplikacja serwera obsługuje łącza, musi utworzyć element serwera za każdym razem, gdy zaznaczenie jest kopiowane do Schowka.

Aby `COleServerDoc`użyć , wyprowadzić klasę z niego i zaimplementować [OnGetEmbeddedItem funkcji członkowskiej,](#ongetembeddeditem) która umożliwia serwerowi do obsługi elementów osadzonych. Wywodź `COleServerItem` klasę, aby zaimplementować elementy w `OnGetEmbeddedItem`dokumentach i zwróć obiekty tej klasy z .

Aby obsługiwać `COleServerDoc` połączone elementy, udostępnia [ongetlinkeditem funkcji członkowskiej.](../../mfc/reference/colelinkingdoc-class.md#ongetlinkeditem) Można użyć domyślnej implementacji lub zastąpić go, jeśli masz własny sposób zarządzania elementami dokumentu.

Potrzebujesz jednej `COleServerDoc`klasy pochodnej dla każdego typu dokumentu serwera, który obsługuje aplikacja. Na przykład jeśli aplikacja serwera obsługuje arkusze i wykresy, potrzebne są dwie `COleServerDoc`klasy pochodne.

Aby uzyskać więcej informacji na temat serwerów, zobacz artykuł [Serwery: Implementowanie serwera](../../mfc/servers-implementing-a-server.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cdocument](../../mfc/reference/cdocument-class.md)

[Coledocument](../../mfc/reference/coledocument-class.md)

[Colelinkingdoc](../../mfc/reference/colelinkingdoc-class.md)

`COleServerDoc`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxole.h

## <a name="coleserverdocactivatedocobject"></a><a name="activatedocobject"></a>COleServerDoc::ActivateDocObject

Aktywuje skojarzony dokument DocObject.

```cpp
void ActivateDocObject();
```

### <a name="remarks"></a>Uwagi

Domyślnie `COleServerDoc` nie obsługuje aktywnych dokumentów (nazywanych również DocObjects). Aby włączyć tę obsługę, zobacz [GetDocObjectServer](#getdocobjectserver) i klasa [CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md).

## <a name="coleserverdocactivateinplace"></a><a name="activateinplace"></a>COleServerDoc::ActivateInPlace

Aktywuje element do edycji w miejscu.

```
BOOL ActivateInPlace();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0, co oznacza, że element jest całkowicie otwarty.

### <a name="remarks"></a>Uwagi

Ta funkcja wykonuje wszystkie operacje niezbędne do aktywacji w miejscu. Tworzy okno ramki w miejscu, aktywuje go i rozmiary go do elementu, konfiguruje udostępnione menu i inne kontrolki, przewija element do widoku i ustawia fokus do okna ramki w miejscu.

Ta funkcja jest wywoływana przez domyślną implementację [COleServerItem::OnShow](../../mfc/reference/coleserveritem-class.md#onshow). Wywołanie tej funkcji, jeśli aplikacja obsługuje inny zlecenie aktywacji w miejscu (takich jak Play).

## <a name="coleserverdoccoleserverdoc"></a><a name="coleserverdoc"></a>COleServerDoc::COleServerDoc

Konstruuje `COleServerDoc` obiekt bez łączenia się z bibliotekami DLL systemu OLE.

```
COleServerDoc();
```

### <a name="remarks"></a>Uwagi

Aby otworzyć komunikację z OLE, należy wywołać [COleLinkingDoc::Register.](../../mfc/reference/colelinkingdoc-class.md#register) Jeśli używasz [COleTemplateServer](../../mfc/reference/coletemplateserver-class.md) w `COleLinkingDoc::Register` aplikacji, jest `COleLinkingDoc`wywoływana przez `OnNewDocument` `OnOpenDocument`implementacji `OnSaveDocument`, i .

## <a name="coleserverdoccreateinplaceframe"></a><a name="createinplaceframe"></a>COleServerDoc::CreateInPlaceFrame

Struktura wywołuje tę funkcję, aby utworzyć okno ramki do edycji w miejscu.

```
virtual COleIPFrameWnd* CreateInPlaceFrame(CWnd* pParentWnd);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Wskaźnik do okna nadrzędnego aplikacji kontenera.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do okna ramki w miejscu lub NULL, jeśli nie powiedzie się.

### <a name="remarks"></a>Uwagi

Domyślna implementacja używa informacji określonych w szablonie dokumentu do utworzenia ramki. Używany widok jest pierwszym widokiem utworzonym dla dokumentu. Ten widok jest tymczasowo odłączony od oryginalnej ramki i dołączony do nowo utworzonej ramki.

Jest to zaawansowane zastąpienie.

## <a name="coleserverdocdeactivateandundo"></a><a name="deactivateandundo"></a>COleServerDoc::DeaktywowaćAndUndo

Wywołanie tej funkcji, jeśli aplikacja obsługuje Cofnij i użytkownik wybiera Cofnij po aktywowaniu elementu, ale przed edycją.

```
BOOL DeactivateAndUndo();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero na sukces; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli aplikacja kontenera jest napisana przy użyciu biblioteki klas Programu Microsoft Foundation, wywołanie tej funkcji powoduje [wywołanie COleClientItem::OnDeactivateAndUndo,](../../mfc/reference/coleclientitem-class.md#ondeactivateandundo) który dezaktywuje interfejs użytkownika serwera.

## <a name="coleserverdocdestroyinplaceframe"></a><a name="destroyinplaceframe"></a>COleServerDoc::DestroyInPlaceFrame

Struktura wywołuje tę funkcję, aby zniszczyć okno ramki w miejscu i przywrócić okno dokumentu aplikacji serwera do stanu przed aktywacją w miejscu.

```
virtual void DestroyInPlaceFrame(COleIPFrameWnd* pFrameWnd);
```

### <a name="parameters"></a>Parametry

*pFrameWnd (pFrameWnd)*<br/>
Wskaźnik do okna ramki w miejscu, które ma zostać zniszczone.

### <a name="remarks"></a>Uwagi

Jest to zaawansowane zastąpienie.

## <a name="coleserverdocdiscardundostate"></a><a name="discardundostate"></a>COleServerDoc::DiscardUndoState

Jeśli użytkownik wykonuje operację edycji, których nie można cofnąć, wywołanie tej funkcji, aby wymusić aplikacji kontenera, aby odrzucić jego informacje o stanie cofania.

```
BOOL DiscardUndoState();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero na sukces; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja jest podana, dzięki czemu serwery obsługujące Cofanie mogą zwolnić zasoby, które w przeciwnym razie byłyby używane przez informacje o stanie cofania, które nie mogą być używane.

## <a name="coleserverdocgetclientsite"></a><a name="getclientsite"></a>COleServerDoc::GetClientSite

Pobiera wskaźnik do interfejsu `IOleClientSite` źródłowego.

```
LPOLECLIENTSITE GetClientSite() const;
```

### <a name="return-value"></a>Wartość zwracana

Pobiera wskaźnik do podstawowego interfejsu [IOleClientSite.](/windows/win32/api/oleidl/nn-oleidl-ioleclientsite)

## <a name="coleserverdocgetdocobjectserver"></a><a name="getdocobjectserver"></a>COleServerDoc::Serwer GetDocObjectServer

Zastąd w tej `CDocObjectServer` funkcji należy utworzyć nowy element i zwrócić do niego wskaźnik.

```
virtual CDocObjectServer* GetDocObjectServer(LPOLEDOCUMENTSITE pDocSite);
```

### <a name="parameters"></a>Parametry

*pDocSite*<br/>
Wskaźnik do `IOleDocumentSite` interfejsu, który połączy ten dokument z serwerem.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CDocObjectServer`; NULL, jeśli operacja nie powiodła się.

### <a name="remarks"></a>Uwagi

Po aktywowaniu serwera DocObject zwracany wskaźnik nienakalny pokazuje, że klient może obsługiwać docObjects. Domyślna implementacja zwraca wartość NULL.

Typowa implementacja dla dokumentu, który obsługuje DocObjects po prostu przydzielić nowy `CDocObjectServer` obiekt i zwrócić go do obiektu wywołującego. Przykład:

[!code-cpp[NVC_MFCOleServer#3](../../mfc/codesnippet/cpp/coleserverdoc-class_1.cpp)]

## <a name="coleserverdocgetembeddeditem"></a><a name="getembeddeditem"></a>COleServerDoc::GetEmbeddedItem

Wywołanie tej funkcji, aby uzyskać wskaźnik do elementu reprezentującego cały dokument.

```
COleServerItem* GetEmbeddedItem();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do elementu reprezentującego cały dokument; NULL, jeśli operacja nie powiodła się.

### <a name="remarks"></a>Uwagi

Wywołuje [COleServerDoc::OnGetEmbeddedItem](#ongetembeddeditem), wirtualną funkcję bez implementacji domyślnej.

## <a name="coleserverdocgetitemcliprect"></a><a name="getitemcliprect"></a>COleServerDoc::GetItemClipRect

Wywołanie `GetItemClipRect` funkcji elementu członkowskiego, aby uzyskać współrzędne clipping-prostokąt elementu, który jest edytowany w miejscu.

```cpp
void GetItemClipRect(LPRECT lpClipRect) const;
```

### <a name="parameters"></a>Parametry

*lpClipRect*<br/>
Wskaźnik do `RECT` struktury `CRect` lub obiektu, aby otrzymać współrzędne clipping-prostokąt elementu.

### <a name="remarks"></a>Uwagi

Współrzędne znajdują się w pikselach względem obszaru klienta okna aplikacji kontenera.

Rysunek nie powinien odbywać się poza prostokątem przycinającym. Zwykle rysunek jest automatycznie ograniczony. Ta funkcja służy do określania, czy użytkownik przewinął poza widoczną część dokumentu; Jeśli tak, przewiń dokument kontenera w razie potrzeby za pomocą wywołania [ScrollContainerBy](#scrollcontainerby).

## <a name="coleserverdocgetitemposition"></a><a name="getitemposition"></a>COleServerDoc::GetItemPosition

Wywołanie `GetItemPosition` funkcji elementu członkowskiego, aby uzyskać współrzędne elementu edytowane w miejscu.

```cpp
void GetItemPosition(LPRECT lpPosRect) const;
```

### <a name="parameters"></a>Parametry

*lpPosRect*<br/>
Wskaźnik do `RECT` struktury `CRect` lub obiektu, aby otrzymać współrzędne elementu.

### <a name="remarks"></a>Uwagi

Współrzędne znajdują się w pikselach względem obszaru klienta okna aplikacji kontenera.

Położenie elementu można porównać z bieżącym prostokątem przycinającym, aby określić stopień, w jakim element jest widoczny (lub niewidoczny) na ekranie.

## <a name="coleserverdocgetzoomfactor"></a><a name="getzoomfactor"></a>COleServerDoc::GetZoomFactor

Funkcja `GetZoomFactor` elementu członkowskiego określa "współczynnik powiększenia" elementu, który został aktywowany do edycji w miejscu.

```
BOOL GetZoomFactor(
    LPSIZE lpSizeNum = NULL,
    LPSIZE lpSizeDenom = NULL,
    LPCRECT lpPosRect = NULL) const;
```

### <a name="parameters"></a>Parametry

*lpSizeNum*<br/>
Wskaźnik do obiektu `CSize` klasy, który będzie trzymał licznik współczynnika powiększenia. Może mieć wartość NULL.

*lpSizeDenom*<br/>
Wskaźnik do obiektu `CSize` klasy, który będzie zawierać mianownik współczynnika powiększenia. Może mieć wartość NULL.

*lpPosRect*<br/>
Wskaźnik do obiektu `CRect` klasy, który opisuje nową pozycję elementu. Jeśli ten argument ma wartość NULL, funkcja używa bieżącej pozycji elementu.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli element jest aktywowany do edycji w miejscu, a jego współczynnik powiększenia jest inny niż 100% (1:1); w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Współczynnik powiększenia w pikselach jest proporcją rozmiaru elementu do jego bieżącego zasięgu. Jeśli aplikacja kontenera nie ustawiła zakresu elementu, używany jest jego naturalny zasięg (określony przez [COleServerItem::OnGetExtent).](../../mfc/reference/coleserveritem-class.md#ongetextent)

Funkcja ustawia swoje pierwsze dwa argumenty na licznik i mianownik elementu "współczynnik powiększenia". Jeśli element nie jest edytowany w miejscu, funkcja ustawia te argumenty na wartość domyślną 100% (lub 1:1) i zwraca zero. Aby uzyskać więcej informacji, zobacz Uwaga techniczna 40, [MFC/OLE Zmiana rozmiaru i powiększanie](../../mfc/tn040-mfc-ole-in-place-resizing-and-zooming.md).

## <a name="coleserverdocisdocobject"></a><a name="isdocobject"></a>COleServerDoc::IsDocObject

Określa, czy dokument jest DocObject.

```
BOOL IsDocObject() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli dokument jest DocObject; w przeciwnym razie FALSE.

## <a name="coleserverdocisembedded"></a><a name="isembedded"></a>COleServerDoc::IsEmbedded

Wywołanie `IsEmbedded` funkcji elementu członkowskiego, aby ustalić, czy dokument reprezentuje obiekt osadzony w kontenerze.

```
BOOL IsEmbedded() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, `COleServerDoc` jeśli obiekt jest dokumentem reprezentującym obiekt osadzony w kontenerze; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Dokument załadowany z pliku nie jest osadzony, chociaż może być manipulowany przez aplikację kontenera jako łącze. Dokument osadzony w dokumencie kontenera jest uważany za osadzony.

## <a name="coleserverdocisinplaceactive"></a><a name="isinplaceactive"></a>COleServerDoc::IsInPlaceActive

Wywołanie `IsInPlaceActive` funkcji elementu członkowskiego, aby ustalić, czy element jest obecnie w stanie aktywnym w miejscu.

```
BOOL IsInPlaceActive() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, `COleServerDoc` jeśli obiekt jest aktywny na miejscu; w przeciwnym razie 0.

## <a name="coleserverdocnotifychanged"></a><a name="notifychanged"></a>COleServerDoc::NotifyZmieniony

Wywołanie tej funkcji, aby powiadomić wszystkie połączone elementy połączone z dokumentem, że dokument został zmieniony.

```cpp
void NotifyChanged();
```

### <a name="remarks"></a>Uwagi

Zazwyczaj ta funkcja jest wywoływana po zmianie przez użytkownika niektórych atrybutów globalnych, takich jak wymiary dokumentu serwera. Jeśli element OLE jest połączony z dokumentem z automatycznym łączem, element jest aktualizowany w celu odzwierciedlenia zmian. W aplikacjach kontenera napisanych za pomocą biblioteki klas `COleClientItem` Microsoft Foundation wywoływana jest funkcja elementu członkowskiego [OnChange.](../../mfc/reference/coleclientitem-class.md#onchange)

> [!NOTE]
> Ta funkcja jest dołączona do zgodności z OLE 1. Nowe aplikacje powinny używać [UpdateAllItems](#updateallitems).

## <a name="coleserverdocnotifyclosed"></a><a name="notifyclosed"></a>COleServerDoc::NotifyClosed

Wywołanie tej funkcji, aby powiadomić kontenery, że dokument został zamknięty.

```cpp
void NotifyClosed();
```

### <a name="remarks"></a>Uwagi

Gdy użytkownik wybierze polecenie Zamknij z `NotifyClosed` menu Plik, jest wywoływana przez `COleServerDoc`implementację [oncloseDocument](../../mfc/reference/cdocument-class.md#onclosedocument) funkcji elementu członkowskiego. W aplikacjach kontenera napisanych za pomocą biblioteki klas `COleClientItem` Microsoft Foundation wywoływana jest funkcja elementu członkowskiego [OnChange.](../../mfc/reference/coleclientitem-class.md#onchange)

## <a name="coleserverdocnotifyrename"></a><a name="notifyrename"></a>COleServerDoc::NotifyRename

Wywołanie tej funkcji po zmianie nazwy dokumentu serwera przez użytkownika.

```cpp
void NotifyRename(LPCTSTR lpszNewName);
```

### <a name="parameters"></a>Parametry

*lpszNewName*<br/>
Wskaźnik do ciągu określającego nową nazwę dokumentu serwera; jest to zazwyczaj w pełni kwalifikowana ścieżka.

### <a name="remarks"></a>Uwagi

Gdy użytkownik wybierze polecenie Zapisz jako z `NotifyRename` menu `COleServerDoc`Plik, jest wywoływana przez implementację funkcji elementu członkowskiego [OnSaveDocument.](../../mfc/reference/cdocument-class.md#onsavedocument) Ta funkcja powiadamia biblioteki DLL systemu OLE, które z kolei powiadamiają kontenery. W aplikacjach kontenera napisanych za pomocą biblioteki klas `COleClientItem` Microsoft Foundation wywoływana jest funkcja elementu członkowskiego [OnChange.](../../mfc/reference/coleclientitem-class.md#onchange)

## <a name="coleserverdocnotifysaved"></a><a name="notifysaved"></a>COleServerDoc::NotifySaved

Wywołanie tej funkcji po zapisaniu dokumentu serwera przez użytkownika.

```cpp
void NotifySaved();
```

### <a name="remarks"></a>Uwagi

Gdy użytkownik wybierze polecenie Zapisz z `NotifySaved` menu Plik, `COleServerDoc`jest wywoływana przez implementację [OnSaveDocument](../../mfc/reference/cdocument-class.md#onsavedocument). Ta funkcja powiadamia biblioteki DLL systemu OLE, które z kolei powiadamiają kontenery. W aplikacjach kontenera napisanych za pomocą biblioteki klas `COleClientItem` Microsoft Foundation wywoływana jest funkcja elementu członkowskiego [OnChange.](../../mfc/reference/coleclientitem-class.md#onchange)

## <a name="coleserverdoconclose"></a><a name="onclose"></a>COleServerDoc::OnKrówka

Wywoływane przez strukturę, gdy kontener żąda zamknięcia dokumentu serwera.

```
virtual void OnClose(OLECLOSE dwCloseOption);
```

### <a name="parameters"></a>Parametry

*dwCloseOption (Kolosaopcja)*<br/>
Wartość z wyliczenia OLECLOSE. Ten parametr może mieć jedną z następujących wartości:

- OLECLOSE_SAVEIFDIRTY Plik jest zapisywany, jeśli został zmodyfikowany.

- OLECLOSE_NOSAVE Plik jest zamykany bez zapisywania.

- OLECLOSE_PROMPTSAVE Jeśli plik został zmodyfikowany, użytkownik jest monitowany o zapisanie go.

### <a name="remarks"></a>Uwagi

Domyślna implementacja wywołuje `CDocument::OnCloseDocument`.

Aby uzyskać więcej informacji i dodatkowe wartości, zobacz [OLECLOSE](/windows/win32/api/oleidl/ne-oleidl-oleclose) w windows SDK.

## <a name="coleserverdocondeactivate"></a><a name="ondeactivate"></a>COleServerDoc::OnDeaktywacji

Wywoływana przez platformę, gdy użytkownik dezaktywuje osadzony lub połączony element, który jest obecnie aktywny w miejscu.

```
virtual void OnDeactivate();
```

### <a name="remarks"></a>Uwagi

Ta funkcja przywraca interfejs użytkownika aplikacji kontenera do stanu pierwotnego i niszczy wszystkie menu i inne formanty, które zostały utworzone w celu aktywacji w miejscu.

Informacje o stanie cofania powinny być bezwarunkowo zwalniane w tym momencie.

Aby uzyskać więcej informacji, zobacz artykuł [Aktywacja](../../mfc/activation-cpp.md)..

## <a name="coleserverdocondeactivateui"></a><a name="ondeactivateui"></a>COleServerDoc::OnDeactivateui

Wywoływane, gdy użytkownik dezaktywuje element, który został aktywowany w miejscu.

```
virtual void OnDeactivateUI(BOOL bUndoable);
```

### <a name="parameters"></a>Parametry

*bDagowalsz*<br/>
Określa, czy zmiany edycji można cofnąć.

### <a name="remarks"></a>Uwagi

Ta funkcja przywraca interfejs użytkownika aplikacji kontenera do stanu pierwotnego, ukrywając wszystkie menu i inne formanty, które zostały utworzone w celu aktywacji w miejscu.

Struktura zawsze ustawia *bOdowanie* na FAŁSZ. Jeśli serwer obsługuje cofanie i istnieje operacja, którą można cofnąć, należy wywołać implementację klasy podstawowej z *zestawem bUndoable* na TRUE.

## <a name="coleserverdocondocwindowactivate"></a><a name="ondocwindowactivate"></a>COleServerDoc::OnDocWindowActivate

Struktura wywołuje tę funkcję, aby aktywować lub dezaktywować okno dokumentu do edycji w miejscu.

```
virtual void OnDocWindowActivate(BOOL bActivate);
```

### <a name="parameters"></a>Parametry

*bAktywowanie*<br/>
Określa, czy okno dokumentu ma być aktywowane, czy dezaktywowane.

### <a name="remarks"></a>Uwagi

Domyślna implementacja usuwa lub dodaje elementy interfejsu użytkownika na poziomie ramki, zgodnie z potrzebami. Zastąd w tej funkcji należy wykonać dodatkowe czynności, gdy dokument zawierający element jest aktywowany lub dezaktywowany.

Aby uzyskać więcej informacji, zobacz artykuł [Aktywacja](../../mfc/activation-cpp.md)..

## <a name="coleserverdoconexecolecmd"></a><a name="onexecolecmd"></a>COleServerDoc::OnExecOleCmd

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

*pguidCmdGroup (Grupa pguidCmd)*<br/>
Wskaźnik do identyfikatora GUID, który identyfikuje zestaw poleceń. Może być null, aby wskazać domyślną grupę poleceń.

*nCmdID (identyfikator nCmdID)*<br/>
Polecenie do wykonania. Musi znajdować się w grupie identyfikowanej przez *pguidCmdGroup*.

*nCmdExecOut*<br/>
Sposób, w jaki obiekt powinien wykonać polecenie, co najmniej jedną z następujących wartości z wyliczenia OLECMDEXECOPT:

OLECMDEXECOPT_DODEFAULT

OLECMDEXECOPT_PROMPTUSER

OLECMDEXECOPT_DONTPROMPTUSER

OLECMDEXECOPT_SHOWHELP

*pvarargIn (polski)*<br/>
Wskaźnik do VARIANTARG zawierający argumenty wejściowe dla polecenia. Może mieć wartość NULL.

*pvarargOut (polski)*<br/>
Wskaźnik do VARIANTARG, aby otrzymać wartości zwracane dane wyjściowe z polecenia. Może mieć wartość NULL.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK, jeśli zakończy się pomyślnie; w przeciwnym razie jeden z następujących kodów błędów:

|Wartość|Opis|
|-----------|-----------------|
|E_unexpected|Wystąpił nieoczekiwany błąd|
|E_fail|błąd instalacji|
|E_notimpl|Wskazuje, że MFC powinien próbować przetłumaczyć i wysłać polecenie|
|OLECMDERR_E_UNKNOWNGROUP|*pguidCmdGroup* nie jest NULL, ale nie określa rozpoznanej grupy poleceń|
|OLECMDERR_E_NOTSUPPORTED|*nCmdID* nie jest rozpoznawany jako prawidłowe polecenie w grupie *pguidCmdGroup*|
|OLECMDERR_DISABLED|Polecenie zidentyfikowane przez *nCmdID* jest wyłączone i nie można go wykonać|
|OLECMDERR_NOHELP|Dzwoniący poprosił o pomoc w komendzie zidentyfikowanej przez *nCmdID,* ale nie ma pomocy|
|OLECMDERR_CANCELED|Użytkownik anulował wykonanie|

### <a name="remarks"></a>Uwagi

`COleCmdUI`może służyć do włączania, aktualizowania i ustawiania innych właściwości poleceń interfejsu użytkownika DocObject. Po zainicjowaniu poleceń można je wykonać `OnExecOleCmd`za pomocą pliku .

Struktura wywołuje funkcję przed próbą przetłumaczenia i wysłania polecenia dokumentu OLE. Nie trzeba zastępować tej funkcji do obsługi standardowych poleceń dokumentu OLE, ale należy podać zastąpienie tej funkcji, jeśli chcesz obsługiwać własne polecenia niestandardowe lub obsługiwać polecenia, które akceptują parametry lub zwracają wyniki.

Większość poleceń nie przyjmuje argumentów ani wartości zwracanych. Dla większości poleceń wywołujący może przekazać NULLs dla *pvarargIn* i *pvarargOut*. W przypadku poleceń, które oczekują wartości wejściowych, wywołujący może zadeklarować i zainicjować zmienną VARIANTARG i przekazać wskaźnik do zmiennej w *pvarargIn*. Dla poleceń, które wymagają pojedynczej wartości, argument może być przechowywany bezpośrednio w VARIANTARG i przekazywane do funkcji. W variantarg należy zapakować wiele argumentów przy użyciu `IDispatch` jednego z obsługiwanych typów (takich jak SAFEARRAY).

Podobnie, jeśli polecenie zwraca argumenty wywołującego oczekuje się zadeklarować VARIANTARG, zainicjować go do VT_EMPTY i przekazać jego adres w *pvarargOut*. Jeśli polecenie zwraca pojedynczą wartość, obiekt może przechowywać tę wartość bezpośrednio w *pvarargOut*. Wiele wartości wyjściowych musi być zapakowane w jakiś sposób odpowiedni dla VARIANTARG.

Implementacja klasy podstawowej tej funkcji będzie chodzić OLE_COMMAND_MAP struktur skojarzonych z celem polecenia i spróbuj wysłać polecenie do odpowiedniego programu obsługi. Implementacja klasy podstawowej działa tylko z poleceniami, które nie akceptują argumentów ani nie zwracają wartości. Jeśli trzeba obsługiwać polecenia, które akceptują argumenty lub zwraca wartości, należy zastąpić tę funkcję i pracować z *pvarargIn* i *pvarargOut* parametrów samodzielnie.

## <a name="coleserverdoconframewindowactivate"></a><a name="onframewindowactivate"></a>COleServerDoc::OnFrameWindowActivate

Struktura wywołuje tę funkcję, gdy okno ramki aplikacji kontenera jest aktywowany lub dezaktywowany.

```
virtual void OnFrameWindowActivate(BOOL bActivate);
```

### <a name="parameters"></a>Parametry

*bAktywowanie*<br/>
Określa, czy okno ramki ma być aktywowane, czy dezaktywowane.

### <a name="remarks"></a>Uwagi

Domyślna implementacja anuluje wszystkie tryby pomocy, w których może znajdować się okno ramki. Zastąd w tej funkcji należy wykonać specjalne przetwarzanie, gdy okno ramki jest aktywowane lub dezaktywowane.

Aby uzyskać więcej informacji, zobacz artykuł [Aktywacja](../../mfc/activation-cpp.md)..

## <a name="coleserverdocongetembeddeditem"></a><a name="ongetembeddeditem"></a>COleServerDoc::OnGetEmbeddedItem

Wywoływana przez platformę, gdy aplikacja kontenera wywołuje aplikację serwera w celu utworzenia lub edycji elementu osadzonego.

```
virtual COleServerItem* OnGetEmbeddedItem() = 0;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do elementu reprezentującego cały dokument; NULL, jeśli operacja nie powiodła się.

### <a name="remarks"></a>Uwagi

Nie ma implementacji domyślnej. Należy zastąpić tę funkcję, aby zwrócić element reprezentujący cały dokument. Ta zwracana wartość powinna `COleServerItem`być obiektem klasy pochodnej.

## <a name="coleserverdoconreactivateandundo"></a><a name="onreactivateandundo"></a>COleServerDoc::OnReactivateAndUndo

Struktura wywołuje tę funkcję, gdy użytkownik zdecyduje się cofnąć zmiany wprowadzone do elementu, który został aktywowany w miejscu, zmienione, a następnie dezaktywowane.

```
virtual BOOL OnReactivateAndUndo();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Domyślna implementacja nie robi nic z wyjątkiem zwracanie FALSE, aby wskazać błąd.

Zastąp tę funkcję, jeśli aplikacja obsługuje cofanie. Zazwyczaj można wykonać operację cofania, a następnie `ActivateInPlace`aktywować element, wywołując . Jeśli aplikacja kontenera jest napisana za pomocą `COleClientItem::ReactivateAndUndo` biblioteki klas Programu Microsoft Foundation, wywołanie powoduje, że ta funkcja ma zostać wywołana.

## <a name="coleserverdoconresizeborder"></a><a name="onresizeborder"></a>COleServerDoc::OnResizeBorder

Struktura wywołuje tę funkcję, gdy okna ramki aplikacji kontenera zmienić rozmiar.

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
Wskaźnik do obiektu `IOleInPlaceUIWindow` klasy, która jest właścicielem bieżącej sesji edycji w miejscu.

*bFrame (Ramka)*<br/>
PRAWDA, jeśli *lpUIWindow* wskazuje okno ramki najwyższego poziomu aplikacji kontenera lub FALSE, jeśli *lpUIWindow* wskazuje okno ramki na poziomie dokumentu aplikacji kontenera.

### <a name="remarks"></a>Uwagi

Ta funkcja umożliwia zmiany rozmiaru i dopasowywanie pasków narzędzi i innych elementów interfejsu użytkownika zgodnie z nowym rozmiarem okna.

Aby uzyskać więcej informacji, zobacz [IOleInPlaceUIWindow](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceuiwindow) w windows SDK.

Jest to zaawansowane zastąpienie.

## <a name="coleserverdoconsethostnames"></a><a name="onsethostnames"></a>COleServerDoc::OnSetHostNames

Wywoływane przez strukturę, gdy kontener ustawia lub zmienia nazwy hosta dla tego dokumentu.

```
virtual void OnSetHostNames(
    LPCTSTR lpszHost,
    LPCTSTR lpszHostObj);
```

### <a name="parameters"></a>Parametry

*lpszHost (lpszHost)*<br/>
Wskaźnik do ciągu, który określa nazwę aplikacji kontenera.

*lpszHostObj*<br/>
Wskaźnik do ciągu, który określa nazwę kontenera dla dokumentu.

### <a name="remarks"></a>Uwagi

Domyślna implementacja zmienia tytuł dokumentu dla wszystkich widoków odnoszących się do tego dokumentu.

Zastąd w tej funkcji, jeśli aplikacja ustawia tytuły za pomocą innego mechanizmu.

## <a name="coleserverdoconsetitemrects"></a><a name="onsetitemrects"></a>COleServerDoc::OnSetItemRects

Struktura wywołuje tę funkcję, aby umieścić okno ramki edycji w miejscu w oknie ramki aplikacji kontenera.

```
virtual void OnSetItemRects(
    LPCRECT lpPosRect,
    LPCRECT lpClipRect);
```

### <a name="parameters"></a>Parametry

*lpPosRect*<br/>
Wskaźnik do `RECT` struktury `CRect` lub obiektu, który określa położenie okna ramki w miejscu względem obszaru klienta aplikacji kontenera.

*lpClipRect*<br/>
Wskaźnik do `RECT` struktury `CRect` lub obiektu, który określa prostokąt przycinania okna ramki w miejscu względem obszaru klienta aplikacji kontenera.

### <a name="remarks"></a>Uwagi

W razie potrzeby zastąpozuj tę funkcję, aby zaktualizować współczynnik powiększenia widoku.

Ta funkcja jest zwykle wywoływana w odpowiedzi na wywołanie, `RequestPositionChange` chociaż może być wywoływana w dowolnym momencie przez kontener, aby zażądać zmiany pozycji dla elementu w miejscu.

## <a name="coleserverdoconshowcontrolbars"></a><a name="onshowcontrolbars"></a>COleServerDoc::OnShowControlBars

Struktura wywołuje tę funkcję, aby pokazać lub ukryć paski sterowania aplikacji serwera skojarzone z oknem ramki identyfikowanym przez *pFrameWnd*.

```
virtual void OnShowControlBars(
    CFrameWnd* pFrameWnd,
    BOOL bShow);
```

### <a name="parameters"></a>Parametry

*pFrameWnd (pFrameWnd)*<br/>
Wskaźnik do okna ramki, którego paski sterujące powinny być ukryte lub pokazane.

*bPokaż*<br/>
Określa, czy paski sterowania są wyświetlane czy ukryte.

### <a name="remarks"></a>Uwagi

Domyślna implementacja wylicza wszystkie paski formantu należące do tego okna ramki i ukrywa je lub pokazuje.

## <a name="coleserverdoconshowdocument"></a><a name="onshowdocument"></a>COleServerDoc::OnShowDocument

Struktura wywołuje `OnShowDocument` funkcję, gdy dokument serwera musi być ukryty lub wyświetlany.

```
virtual void OnShowDocument(BOOL bShow);
```

### <a name="parameters"></a>Parametry

*bPokaż*<br/>
Określa, czy interfejs użytkownika dokumentu ma być wyświetlany, czy ukryty.

### <a name="remarks"></a>Uwagi

Jeśli *bShow* jest TRUE, domyślna implementacja aktywuje aplikację serwera, jeśli to konieczne, i powoduje, że aplikacja kontenera przewinąć okno, tak aby element był widoczny. Jeśli *bShow* jest FALSE, domyślna implementacja dezaktywuje element za pośrednictwem wywołania `OnDeactivate`, a następnie niszczy lub ukrywa wszystkie okna ramki, które zostały utworzone dla dokumentu, z wyjątkiem pierwszego. Jeśli nie pozostają widoczne dokumenty, domyślna implementacja ukrywa aplikację serwera.

## <a name="coleserverdoconupdatedocument"></a><a name="onupdatedocument"></a>COleServerDoc::OnUpdateDocument

Wywoływane przez strukturę podczas zapisywania dokumentu, który jest elementem osadzonym w dokumencie złożonym.

```
virtual BOOL OnUpdateDocument();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli dokument został pomyślnie zaktualizowany; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Domyślna implementacja wywołuje funkcje członkowskie [COleServerDoc::NotifySaved](#notifysaved) i [COleServerDoc::SaveEmbedding,](#saveembedding) a następnie oznacza dokument jako czysty. Zastąd w tej funkcji należy wykonać specjalne przetwarzanie podczas aktualizowania elementu osadzonego.

## <a name="coleserverdocrequestpositionchange"></a><a name="requestpositionchange"></a>COleServerDoc::RequestPositionChange

Wywołanie tej funkcji elementu członkowskiego, aby aplikacja kontenera zmienić pozycję elementu.

```cpp
void RequestPositionChange(LPCRECT lpPosRect);
```

### <a name="parameters"></a>Parametry

*lpPosRect*<br/>
Wskaźnik do `RECT` struktury `CRect` lub obiektu zawierającego nową pozycję elementu.

### <a name="remarks"></a>Uwagi

Ta funkcja jest zwykle wywoływana (w połączeniu z) `UpdateAllItems`po zmianie danych w aktywnym elemencie w miejscu. Po tym wywołaniu kontener może lub nie `OnSetItemRects`może wykonać zmiany, wywołując . Wynikowe położenie może się różnić od żądanej.

## <a name="coleserverdocsaveembedding"></a><a name="saveembedding"></a>COleServerDoc::SaveEmbedding

Wywołanie tej funkcji, aby poinformować aplikację kontenera, aby zapisać obiekt osadzony.

```cpp
void SaveEmbedding();
```

### <a name="remarks"></a>Uwagi

Ta funkcja jest wywoływana automatycznie z . `OnUpdateDocument` Należy zauważyć, że ta funkcja powoduje, że element ma być aktualizowany na dysku, więc jest zwykle wywoływana tylko w wyniku akcji określonego użytkownika.

## <a name="coleserverdocscrollcontainerby"></a><a name="scrollcontainerby"></a>COleServerDoc::ScrollContainerBy

Wywołanie `ScrollContainerBy` funkcji elementu członkowskiego, aby przewinąć dokument kontenera `sizeScroll`o kwotę, w pikselach, wskazywanych przez .

```
BOOL ScrollContainerBy(CSize sizeScroll);
```

### <a name="parameters"></a>Parametry

*rozmiarScroll*<br/>
Wskazuje, jak daleko dokument kontenera ma być przewijany.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wartości dodatnie wskazują przewijanie w dół i w prawo; wartości ujemne wskazują przewijanie w górę i w lewo.

## <a name="coleserverdocupdateallitems"></a><a name="updateallitems"></a>COleServerDoc::UpdateAllItems

Wywołanie tej funkcji, aby powiadomić wszystkie połączone elementy połączone z dokumentem, że dokument został zmieniony.

```cpp
void UpdateAllItems(
    COleServerItem* pSender,
    LPARAM lHint = 0L,
    CObject* pHint = NULL,
    DVASPECT nDrawAspect = DVASPECT_CONTENT);
```

### <a name="parameters"></a>Parametry

*pSender (nadawca)*<br/>
Wskaźnik do elementu, który zmodyfikował dokument, lub NULL, jeśli wszystkie elementy mają zostać zaktualizowane.

*Lhint*<br/>
Zawiera informacje o modyfikacji.

*Phint*<br/>
Wskaźnik do obiektu przechowującego informacje o modyfikacji.

*nDrawAspect*<br/>
Określa sposób rysowania elementu. Jest to wartość z wyliczenia DVASPECT. Ten parametr może mieć jedną z następujących wartości:

- DVASPECT_CONTENT Element jest reprezentowany w taki sposób, że może być wyświetlany jako obiekt osadzony wewnątrz jego kontenera.

- DVASPECT_THUMBNAIL Element jest renderowany w reprezentacji "miniatury", dzięki czemu może być wyświetlany w narzędziu do przeglądania.

- DVASPECT_ICON Element jest reprezentowany przez ikonę.

- DVASPECT_DOCPRINT Element jest reprezentowany tak, jakby był drukowany za pomocą polecenia Drukuj z menu Plik.

### <a name="remarks"></a>Uwagi

Zazwyczaj wywołanie tej funkcji po zmianie przez użytkownika dokumentu serwera. Jeśli element OLE jest połączony z dokumentem z automatycznym łączem, element jest aktualizowany w celu odzwierciedlenia zmian. W aplikacjach kontenera napisanych za pomocą biblioteki klas `COleClientItem` Microsoft Foundation wywoływana jest funkcja elementu członkowskiego [OnChange.](../../mfc/reference/coleclientitem-class.md#onchange)

Ta funkcja `OnUpdate` wywołuje funkcję elementu członkowskiego dla każdego elementu dokumentu z wyjątkiem elementu wysyłającego, przekazując *pHint*, *lHint*i *nDrawAspect*. Te parametry służą do przekazywania informacji do elementów dotyczących modyfikacji wprowadzonych w dokumencie. Można zakodować informacje za pomocą *lHint* lub można zdefiniować klasę pochodną `CObject`do przechowywania informacji o modyfikacjach i przekazywania obiektu tej klasy za pomocą *pHint*. Zastąpić `OnUpdate` funkcję `COleServerItem`elementu członkowskiego w klasie pochodnej, aby zoptymalizować aktualizację każdego elementu w zależności od tego, czy jego prezentacja została zmieniona.

## <a name="see-also"></a>Zobacz też

[Przykładowy HIERSVR MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleDocument](../../mfc/reference/coledocument-class.md)<br/>
[Klasa COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)<br/>
[Klasa COleTemplateServer](../../mfc/reference/coletemplateserver-class.md)
