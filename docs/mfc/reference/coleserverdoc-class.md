---
title: COleServerDoc Class
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
ms.openlocfilehash: 4cada70723c7fadc9c91c40380b8a7e9fc46a07a
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58777262"
---
# <a name="coleserverdoc-class"></a>COleServerDoc Class

Klasa podstawowa dla dokumentów serwera OLE.

## <a name="syntax"></a>Składnia

```
class AFX_NOVTABLE COleServerDoc : public COleLinkingDoc
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleServerDoc::COleServerDoc](#coleserverdoc)|Konstruuje `COleServerDoc` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleServerDoc::ActivateDocObject](#activatedocobject)|Aktywuje powiązany dokument DocObject.|
|[COleServerDoc::ActivateInPlace](#activateinplace)|Aktywuje dokument do edycji w miejscu.|
|[COleServerDoc::DeactivateAndUndo](#deactivateandundo)|Dezaktywuje interfejs użytkownika serwera.|
|[COleServerDoc::DiscardUndoState](#discardundostate)|Odrzuca informacje o stanie cofania.|
|[COleServerDoc::GetClientSite](#getclientsite)|Pobiera wskaźnik do bazowego `IOleClientSite` interfejsu.|
|[COleServerDoc::GetEmbeddedItem](#getembeddeditem)|Zwraca wskaźnik do elementu, który reprezentuje cały dokument.|
|[COleServerDoc::GetItemClipRect](#getitemcliprect)|Zwraca bieżący prostokątnego wycinka do edycji w miejscu.|
|[COleServerDoc::GetItemPosition](#getitemposition)|Zwraca bieżący prostokąt pozycji, względem obszaru klienckiego aplikacji kontenera, do edycji w miejscu.|
|[COleServerDoc::GetZoomFactor](#getzoomfactor)|Zwraca wartość współczynnika powiększenia w pikselach.|
|[COleServerDoc::IsDocObject](#isdocobject)|Określa, czy dokument jest obiekt DocObject.|
|[COleServerDoc::IsEmbedded](#isembedded)|Wskazuje, czy dokument jest osadzony w dokumencie kontenera lub uruchomiony autonomiczny.|
|[COleServerDoc::IsInPlaceActive](#isinplaceactive)|Zwraca wartość PRAWDA, jeśli element jest aktywowany w miejscu.|
|[COleServerDoc::NotifyChanged](#notifychanged)|Powiadamia kontenerów, że użytkownik zmienił dokumentu.|
|[COleServerDoc::NotifyClosed](#notifyclosed)|Powiadamia kontenerów, że użytkownik zamknął dokumentu.|
|[COleServerDoc::NotifyRename](#notifyrename)|Powiadamia kontenerów, że użytkownik zmienił nazwę dokumentu.|
|[COleServerDoc::NotifySaved](#notifysaved)|Powiadamia kontenerów, że użytkownik został zapisany dokument.|
|[COleServerDoc::OnDeactivate](#ondeactivate)|Wywoływane przez platformę, gdy użytkownik dezaktywuje element, któremu został aktywowany w miejscu.|
|[COleServerDoc::OnDeactivateUI](#ondeactivateui)|Metoda wywoływana przez platformę, by zniszczyć formantów i innych elementów interfejsu użytkownika tworzone dla aktywacji w miejscu.|
|[COleServerDoc::OnDocWindowActivate](#ondocwindowactivate)|Wywoływane przez platformę, gdy okno ramowe dokumentów kontenera jest aktywowane lub dezaktywowane.|
|[COleServerDoc::OnResizeBorder](#onresizeborder)|Wywoływane przez platformę, gdy zmieniany jest rozmiar ramki okna lub okno dokumentu aplikacji kontenera.|
|[COleServerDoc::OnShowControlBars](#onshowcontrolbars)|Metoda wywoływana przez platformę, by pokazać lub ukryć paski sterowania do edycji w miejscu.|
|[COleServerDoc::OnUpdateDocument](#onupdatedocument)|Wywoływane przez platformę po zapisaniu dokumentu serwera, który jest element osadzony aktualizowanie kopii kontenera elementu.|
|[COleServerDoc::RequestPositionChange](#requestpositionchange)|Zmienia pozycję ramki edycji w miejscu.|
|[COleServerDoc::SaveEmbedding](#saveembedding)|Zawiera informacje dla aplikacji kontenera, aby zapisać dokument.|
|[COleServerDoc::ScrollContainerBy](#scrollcontainerby)|Przewija dokumentu kontenera.|
|[COleServerDoc::UpdateAllItems](#updateallitems)|Powiadamia kontenerów, że użytkownik zmienił dokumentu.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[COleServerDoc::CreateInPlaceFrame](#createinplaceframe)|Metoda wywoływana przez platformę, aby utworzyć ramkę okna do edycji w miejscu.|
|[COleServerDoc::DestroyInPlaceFrame](#destroyinplaceframe)|Metoda wywoływana przez platformę, by zniszczyć okno ramowe do edycji w miejscu.|
|[COleServerDoc::GetDocObjectServer](#getdocobjectserver)|Przesłonić tę funkcję, aby utworzyć nowy `CDocObjectServer` obiektu i wskazują, że ten dokument jest kontenerem DocObject.|
|[COleServerDoc::OnClose](#onclose)|Wywoływane przez platformę, gdy kontener żąda zamknąć dokument.|
|[COleServerDoc::OnExecOleCmd](#onexecolecmd)|Wykonuje określone polecenie lub wyświetla Pomoc dla polecenia.|
|[COleServerDoc::OnFrameWindowActivate](#onframewindowactivate)|Wywoływane przez platformę, gdy okno ramowe kontenera jest aktywowane lub dezaktywowane.|
|[COleServerDoc::OnGetEmbeddedItem](#ongetembeddeditem)|Wywołuje się, by pobrać `COleServerItem` który reprezentuje cały dokument; używany do uzyskiwania osadzonego elementu. Implementacja jest wymagana.|
|[COleServerDoc::OnReactivateAndUndo](#onreactivateandundo)|Metoda wywoływana przez platformę, by cofnąć zmiany wprowadzone podczas edycji w miejscu.|
|[COleServerDoc::OnSetHostNames](#onsethostnames)|Wywoływane przez platformę, gdy kontener Ustawia tytuł okna osadzonego obiektu.|
|[COleServerDoc::OnSetItemRects](#onsetitemrects)|Metoda wywoływana przez platformę, by położenie okna ramki edycji w miejscu w obrębie okna aplikacji kontenera.|
|[COleServerDoc::OnShowDocument](#onshowdocument)|Metoda wywoływana przez platformę, by pokazać lub ukryć dokumentu.|

## <a name="remarks"></a>Uwagi

Dokument serwera może zawierać [COleServerItem](../../mfc/reference/coleserveritem-class.md) obiektów, które reprezentują interfejs serwera elementów osadzony lub połączony. Po uruchomieniu aplikacji serwera przy użyciu kontenera, aby edytować element osadzony element jest ładowana jako swój własny dokument na serwerze; `COleServerDoc` obiekt zawiera co najmniej jeden `COleServerItem` obiekt, składający się z całego dokumentu. Po uruchomieniu aplikacji serwera przez kontener do edycji połączony element istniejący dokument jest ładowany z dysku część zawartości dokumentu jest wyróżniony, aby wskazać połączonego elementu.

`COleServerDoc` obiekty mogą również zawierać elementy [COleClientItem](../../mfc/reference/coleclientitem-class.md) klasy. Pozwala na tworzenie aplikacji kontenera serwera. Struktura udostępnia funkcje do przechowywania prawidłowo `COleClientItem` elementów podczas obsługi `COleServerItem` obiektów.

Jeśli aplikacja serwera nie obsługuje łącza, dokument serwera zawsze zawiera tylko jeden element serwera, który reprezentuje cały obiekt osadzony jako dokument. Jeśli aplikacja serwera obsługuje łącza, go należy utworzyć element serwera w każdym razem, gdy wybór zostanie skopiowany do Schowka.

Aby użyć `COleServerDoc`dziedziczyć po nim klasę i zaimplementować [OnGetEmbeddedItem](#ongetembeddeditem) funkcji elementu członkowskiego, która umożliwia serwerowi obsługi elementów osadzonych. Wyprowadzić klasę z `COleServerItem` do zaimplementowania elementy w dokumentach i zwracać obiekty tej klasy z `OnGetEmbeddedItem`.

Aby obsługiwać połączone elementy `COleServerDoc` zapewnia [OnGetLinkedItem](../../mfc/reference/colelinkingdoc-class.md#ongetlinkeditem) funkcja elementu członkowskiego. Można użyć w implementacji domyślnej lub go zastąpić, jeśli masz własny sposób zarządzania elementów dokumentu.

Potrzebna jest jedna `COleServerDoc`-klasy pochodnej, dla każdego typu serwera dokumentów obsługuje Twojej aplikacji. Na przykład, jeśli aplikacja serwera obsługuje arkuszy i wykresów, potrzebne są dwa `COleServerDoc`-klas pochodnych.

Aby uzyskać więcej informacji na serwerach, zobacz artykuł [serwerów: Implementowanie serwera](../../mfc/servers-implementing-a-server.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

[COleDocument](../../mfc/reference/coledocument-class.md)

[COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)

`COleServerDoc`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxole.h

##  <a name="activatedocobject"></a>  COleServerDoc::ActivateDocObject

Aktywuje powiązany dokument DocObject.

```
void ActivateDocObject();
```

### <a name="remarks"></a>Uwagi

Domyślnie `COleServerDoc` nie obsługuje dokumentów aktywnych (nazywane również DocObjects). Aby włączyć obsługę tego, zobacz [GetDocObjectServer](#getdocobjectserver) i klasa [CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md).

##  <a name="activateinplace"></a>  COleServerDoc::ActivateInPlace

Uaktywnia element do edycji w miejscu.

```
BOOL ActivateInPlace();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0, która wskazuje, czy element jest w pełni otwarty.

### <a name="remarks"></a>Uwagi

Ta funkcja wykonuje wszystkie czynności niezbędne do aktywacji w miejscu. Go tworzy okno ramowe w miejscu, aktywuje go i rozmiarach go do elementu, konfiguruje udostępnionego menu i inne formanty, przewinąć element w celu wyświetlenia i ustawia fokus okno ramowe w miejscu.

Ta funkcja jest wywoływana przez domyślną implementację elementu [COleServerItem::OnShow](../../mfc/reference/coleserveritem-class.md#onshow). Wywołaj tę funkcję, jeśli aplikacja obsługuje innego zlecenie dla aktywacji w miejscu (takie jak Odtwórz).

##  <a name="coleserverdoc"></a>  COleServerDoc::COleServerDoc

Konstruuje `COleServerDoc` obiektu bez połączenia z systemem OLE biblioteki dll.

```
COleServerDoc();
```

### <a name="remarks"></a>Uwagi

Należy wywołać [COleLinkingDoc::Register](../../mfc/reference/colelinkingdoc-class.md#register) otworzyć komunikacji przy użyciu OLE. Jeśli używasz [element COleTemplateServer](../../mfc/reference/coletemplateserver-class.md) w aplikacji `COleLinkingDoc::Register` jest wywoływana w programie `COleLinkingDoc`przez implementację `OnNewDocument`, `OnOpenDocument`, i `OnSaveDocument`.

##  <a name="createinplaceframe"></a>  COleServerDoc::CreateInPlaceFrame

Struktura wywołuje tę funkcję, aby utworzyć ramkę okna do edycji w miejscu.

```
virtual COleIPFrameWnd* CreateInPlaceFrame(CWnd* pParentWnd);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Wskaźnik do okna nadrzędnego aplikacji kontenera.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do okno ramowe w miejscu, lub wartość NULL, jeśli nie powiedzie.

### <a name="remarks"></a>Uwagi

Domyślna implementacja używa informacji o określonych w szablonie dokumentu, aby utworzyć ramkę. Widok używany jest pierwszym widokiem, które są tworzone dla dokumentu. Ten widok jest tymczasowo odłączone od pierwotnej ramce i dołączony do nowo utworzonego ramki.

Jest to zaawansowany możliwym do zastąpienia.

##  <a name="deactivateandundo"></a>  COleServerDoc::DeactivateAndUndo

Wywołaj tę funkcję, jeśli Twoja aplikacja obsługuje cofnąć, a użytkownik wybierze cofania po aktywowaniu elementu ale przed jego edycji.

```
BOOL DeactivateAndUndo();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera w przypadku powodzenia; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji powoduje, że jeśli aplikacja kontenera są zapisywane przy użyciu biblioteki klas Microsoft Foundation, [COleClientItem::OnDeactivateAndUndo](../../mfc/reference/coleclientitem-class.md#ondeactivateandundo) do wywołania, które dezaktywuje interfejs użytkownika serwera.

##  <a name="destroyinplaceframe"></a>  COleServerDoc::DestroyInPlaceFrame

Struktura wywołuje tę funkcję, aby zniszczyć okno ramowe w miejscu i okna dokumentu aplikacji przywrócić serwer do stanu przed aktywacji w miejscu.

```
virtual void DestroyInPlaceFrame(COleIPFrameWnd* pFrameWnd);
```

### <a name="parameters"></a>Parametry

*pFrameWnd*<br/>
Wskaźnik do okno ramowe w miejscu mają zostać zniszczone.

### <a name="remarks"></a>Uwagi

Jest to zaawansowany możliwym do zastąpienia.

##  <a name="discardundostate"></a>  COleServerDoc::DiscardUndoState

Jeśli użytkownik wykona operację edycji, którego nie można cofnąć, należy wywołać tę funkcję, aby wymusić stosowanie kontenera, aby odrzucić jego informacje o stanie cofania.

```
BOOL DiscardUndoState();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera w przypadku powodzenia; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja jest udostępniana na serwery, które obsługuje operacji cofania można zwolnić zasoby, które w przeciwnym razie mogłyby być wykorzystane przez informacji o stanie cofania, którego nie można użyć.

##  <a name="getclientsite"></a>  COleServerDoc::GetClientSite

Pobiera wskaźnik do bazowego `IOleClientSite` interfejsu.

```
LPOLECLIENTSITE GetClientSite() const;
```

### <a name="return-value"></a>Wartość zwracana

Pobiera wskaźnik do bazowego [IOleClientSite](/windows/desktop/api/oleidl/nn-oleidl-ioleclientsite) interfejsu.

##  <a name="getdocobjectserver"></a>  COleServerDoc::GetDocObjectServer

Przesłonić tę funkcję, aby utworzyć nowy `CDocObjectServer` element i zwraca wskaźnik do niego.

```
virtual CDocObjectServer* GetDocObjectServer(LPOLEDOCUMENTSITE pDocSite);
```

### <a name="parameters"></a>Parametry

*pDocSite*<br/>
Wskaźnik do `IOleDocumentSite` interfejsu, który będzie łączyć z tego dokumentu do serwera.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CDocObjectServer`; Wartość NULL, jeśli operacja nie powiodła się.

### <a name="remarks"></a>Uwagi

Po aktywowaniu serwera obiektów DocObject zwracany wskaźnik ZEROWY pokazuje, że klient może obsługiwać DocObjects. Domyślna implementacja zwraca wartość NULL.

Typowa implementacja dla dokumentu, który obsługuje DocObjects po prostu spowoduje przydzielenie nowej `CDocObjectServer` obiektów i przywrócić go do obiektu wywołującego. Na przykład:

[!code-cpp[NVC_MFCOleServer#3](../../mfc/codesnippet/cpp/coleserverdoc-class_1.cpp)]

##  <a name="getembeddeditem"></a>  COleServerDoc::GetEmbeddedItem

Wywołaj tę funkcję, aby uzyskać wskaźnik do elementu, który reprezentuje cały dokument.

```
COleServerItem* GetEmbeddedItem();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do elementu, który reprezentuje cały dokument; Wartość NULL, jeśli operacja nie powiodła się.

### <a name="remarks"></a>Uwagi

Wywołuje [COleServerDoc::OnGetEmbeddedItem](#ongetembeddeditem), funkcją wirtualną z implementacji domyślnej.

##  <a name="getitemcliprect"></a>  COleServerDoc::GetItemClipRect

Wywołaj `GetItemClipRect` funkcja elementu członkowskiego, by uzyskać współrzędne prostokątnego wycinka elementu, który jest edytowany w miejscu.

```
void GetItemClipRect(LPRECT lpClipRect) const;
```

### <a name="parameters"></a>Parametry

*lpClipRect*<br/>
Wskaźnik do `RECT` struktury lub `CRect` obiektu do odbierania współrzędne prostokątnego wycinka elementu.

### <a name="remarks"></a>Uwagi

Współrzędne są podawane w pikselach względem pola klienta okna aplikacji kontenera.

Rysowanie nie powinien wystąpić poza prostokątny. Zazwyczaj rysunek jest automatycznie ograniczany. Ta funkcja służy do określenia, czy użytkownik ma być przewijane poza widocznej części dokumentu. Jeśli tak, przewiń dokument o kontenerze zgodnie z potrzebami przy użyciu wywołania [ScrollContainerBy](#scrollcontainerby).

##  <a name="getitemposition"></a>  COleServerDoc::GetItemPosition

Wywołaj `GetItemPosition` funkcja elementu członkowskiego, by uzyskać współrzędne elementu edytowany w miejscu.

```
void GetItemPosition(LPRECT lpPosRect) const;
```

### <a name="parameters"></a>Parametry

*lpPosRect*<br/>
Wskaźnik do `RECT` struktury lub `CRect` obiektu do odbierania współrzędne elementu.

### <a name="remarks"></a>Uwagi

Współrzędne są podawane w pikselach względem pola klienta okna aplikacji kontenera.

Położenie elementu można porównać z bieżącego Prostokątny wycinek w celu ustalenia zakresu, do którego element jest widoczny (lub nie są widoczne) na ekranie.

##  <a name="getzoomfactor"></a>  COleServerDoc::GetZoomFactor

`GetZoomFactor` Funkcja elementu członkowskiego określa "współczynnika powiększenia" elementu, który został aktywowany do edycji w miejscu.

```
BOOL GetZoomFactor(
    LPSIZE lpSizeNum = NULL,
    LPSIZE lpSizeDenom = NULL,
    LPCRECT lpPosRect = NULL) const;
```

### <a name="parameters"></a>Parametry

*lpSizeNum*<br/>
Wskaźnik do obiektu klasy `CSize` który będzie przechowywać Licznik współczynnika powiększenia. Może mieć wartości NULL.

*lpSizeDenom*<br/>
Wskaźnik do obiektu klasy `CSize` który będzie przechowywać mianownik współczynnika powiększenia. Może mieć wartości NULL.

*lpPosRect*<br/>
Wskaźnik do obiektu klasy `CRect` , który opisuje elementu w nowym położeniu. Jeśli ten argument ma wartość NULL, funkcja używa bieżącej pozycji elementu.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli element aktywacji w miejscu edycji i jego współczynnika powiększenia jest inne niż 100% (1:1); w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Współczynnika powiększenia, w pikselach, jest część rozmiar elementu w jego bieżącym zakresie. Jeśli aplikacja kontenera nie ustawił elementu zakresu, jego naturalne rozszerzenie (zgodnie z ustaleniami [COleServerItem::OnGetExtent](../../mfc/reference/coleserveritem-class.md#ongetextent)) jest używany.

Funkcja ustawia jego pierwsze dwa argumenty, licznik i mianownik elementu "współczynnika powiększenia." Jeśli element nie jest edytowany w miejscu, funkcja ustawia domyślną wartość 100% (lub 1:1) te argumenty i zwraca wartość zero. Aby uzyskać więcej informacji, patrz Pomoc 40 Uwaga [rozmiaru w miejscu MFC/OLE i powiększenie](../../mfc/tn040-mfc-ole-in-place-resizing-and-zooming.md).

##  <a name="isdocobject"></a>  COleServerDoc::IsDocObject

Określa, czy dokument jest obiekt DocObject.

```
BOOL IsDocObject() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli dokument jest DocObject; w przeciwnym razie wartość FALSE.

##  <a name="isembedded"></a>  COleServerDoc::IsEmbedded

Wywołaj `IsEmbedded` funkcja elementu członkowskiego, aby ustalić, czy dokument reprezentuje obiekt osadzony w kontenerze.

```
BOOL IsEmbedded() const;
```

### <a name="return-value"></a>Wartość zwracana

Jeśli wartość różną od zera `COleServerDoc` obiekt jest dokument, który reprezentuje obiekt osadzony w kontenerze; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

W przypadku dokumentu z pliku nie jest zagnieżdżony, chociaż może być zmieniane przez aplikację kontenera jako łącza. Dokument, który jest osadzony w dokumencie kontenera jest uważany za można osadzić.

##  <a name="isinplaceactive"></a>  COleServerDoc::IsInPlaceActive

Wywołaj `IsInPlaceActive` funkcja elementu członkowskiego, aby ustalić, czy element jest w stanie aktywnym w miejscu.

```
BOOL IsInPlaceActive() const;
```

### <a name="return-value"></a>Wartość zwracana

Jeśli wartość różną od zera `COleServerDoc` obiekt jest aktywny w miejscu; w przeciwnym razie 0.

##  <a name="notifychanged"></a>  COleServerDoc::NotifyChanged

Wywołaj tę funkcję, aby powiadomić wszystkich połączonych elementów podłączone do dokumentu, który został zmieniony dokument.

```
void NotifyChanged();
```

### <a name="remarks"></a>Uwagi

Zazwyczaj możesz wywołać tę funkcję, po użytkownik zmieni niektórych atrybutów global np. wymiarów dokumentu na serwerze. Jeśli element OLE został połączony w dokumencie przy użyciu linku automatyczne, element zostanie zaktualizowany zgodnie ze zmianami. W aplikacjach kontenera napisane przy użyciu biblioteki klas Microsoft Foundation [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) funkcji składowej typu `COleClientItem` jest wywoływana.

> [!NOTE]
>  Ta funkcja jest włączone dla zachowania zgodności z OLE 1. Nowe aplikacje powinny używać [UpdateAllItems](#updateallitems).

##  <a name="notifyclosed"></a>  COleServerDoc::NotifyClosed

Wywołaj tę funkcję, aby powiadomić kontenerów, czy dokument został zamknięty.

```
void NotifyClosed();
```

### <a name="remarks"></a>Uwagi

Gdy użytkownik wybierze polecenie zamknięcia z menu Plik `NotifyClosed` jest wywoływana przez `COleServerDoc`przez implementację [OnCloseDocument](../../mfc/reference/cdocument-class.md#onclosedocument) funkcja elementu członkowskiego. W aplikacjach kontenera napisane przy użyciu biblioteki klas Microsoft Foundation [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) funkcji składowej typu `COleClientItem` jest wywoływana.

##  <a name="notifyrename"></a>  COleServerDoc::NotifyRename

Wywołaj tę funkcję, po użytkownik zmienia nazwę dokumentu na serwerze.

```
void NotifyRename(LPCTSTR lpszNewName);
```

### <a name="parameters"></a>Parametry

*lpszNewName*<br/>
Wskaźnik na ciąg określający nazwę nowego serwera dokumentu. Zazwyczaj jest w pełni kwalifikowaną ścieżkę.

### <a name="remarks"></a>Uwagi

Gdy użytkownik wybierze polecenie Zapisz jako, w menu Plik `NotifyRename` jest wywoływana przez `COleServerDoc`przez implementację [OnSaveDocument](../../mfc/reference/cdocument-class.md#onsavedocument) funkcja elementu członkowskiego. Ta funkcja powiadomi system OLE bibliotek DLL, które z kolei Powiadom kontenerów. W aplikacjach kontenera napisane przy użyciu biblioteki klas Microsoft Foundation [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) funkcji składowej typu `COleClientItem` jest wywoływana.

##  <a name="notifysaved"></a>  COleServerDoc::NotifySaved

Wywołaj tę funkcję, po użytkownik zapisze dokument serwera.

```
void NotifySaved();
```

### <a name="remarks"></a>Uwagi

Gdy użytkownik wybierze polecenie Zapisz z menu Plik `NotifySaved` jest wywoływana przez `COleServerDoc`przez implementację [OnSaveDocument](../../mfc/reference/cdocument-class.md#onsavedocument). Ta funkcja powiadomi system OLE bibliotek DLL, które z kolei Powiadom kontenerów. W aplikacjach kontenera napisane przy użyciu biblioteki klas Microsoft Foundation [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) funkcji składowej typu `COleClientItem` jest wywoływana.

##  <a name="onclose"></a>  COleServerDoc::OnClose

Wywoływane przez platformę, gdy kontener żąda zamknięte dokumentu na serwerze.

```
virtual void OnClose(OLECLOSE dwCloseOption);
```

### <a name="parameters"></a>Parametry

*dwCloseOption*<br/>
Wartość z wyliczenia OLECLOSE. Ten parametr może mieć jedną z następujących wartości:

- OLECLOSE_SAVEIFDIRTY plik jest zapisany, jeśli został zmodyfikowany.

- OLECLOSE_NOSAVE plik jest zamknięty bez zapisywany.

- OLECLOSE_PROMPTSAVE, jeśli plik został zmodyfikowany, użytkownik jest monitowany o zapisanie go.

### <a name="remarks"></a>Uwagi

Domyślna implementacja wywołuje `CDocument::OnCloseDocument`.

Aby uzyskać więcej informacji i dodatkowe wartości, zobacz [OLECLOSE](/windows/desktop/api/oleidl/ne-oleidl-tagoleclose) w zestawie Windows SDK.

##  <a name="ondeactivate"></a>  COleServerDoc::OnDeactivate

Wywoływane przez platformę, gdy użytkownik dezaktywuje element osadzony lub połączony, który jest obecnie aktywny w miejscu.

```
virtual void OnDeactivate();
```

### <a name="remarks"></a>Uwagi

Ta funkcja spowoduje przywrócenie interfejsu użytkownika aplikacji kontenera do stanu pierwotnego i niszczy wszystkie menu i inne formanty, które zostały utworzone dla aktywacji w miejscu.

Informacje o stanie cofania powinny zostać opublikowane bezwarunkowo w tym momencie.

Aby uzyskać więcej informacji, zobacz artykuł [aktywacji](../../mfc/activation-cpp.md)...

##  <a name="ondeactivateui"></a>  COleServerDoc::OnDeactivateUI

Wywołuje się, gdy użytkownik dezaktywuje element, który został aktywowany w miejscu.

```
virtual void OnDeactivateUI(BOOL bUndoable);
```

### <a name="parameters"></a>Parametry

*bUndoable*<br/>
Określa, czy edycji zmiany można cofnąć.

### <a name="remarks"></a>Uwagi

Ta funkcja spowoduje przywrócenie interfejsu użytkownika aplikacji kontenera do stanu pierwotnego, ukrywanie dowolnego menu i inne formanty, które zostały utworzone dla aktywacji w miejscu.

Struktura zawsze ustawia *bUndoable* na wartość FALSE. Jeśli serwer obsługuje cofania jest operacją, która może być cofnięte, wywołania implementacji klasy podstawowej za pomocą *bUndoable* ustawiona na wartość TRUE.

##  <a name="ondocwindowactivate"></a>  COleServerDoc::OnDocWindowActivate

Struktura wywołuje tę funkcję, aby aktywować lub dezaktywować okno dokumentu do edycji w miejscu.

```
virtual void OnDocWindowActivate(BOOL bActivate);
```

### <a name="parameters"></a>Parametry

*bActivate*<br/>
Określa, czy okno dokumentu ma zostać aktywowane lub dezaktywowane.

### <a name="remarks"></a>Uwagi

Domyślna implementacja usuwa lub dodaje elementy interfejsu użytkownika na poziomie ramki zgodnie z potrzebami. Należy przesłonić tę funkcję, jeśli chcesz wykonać dodatkowe akcje w przypadku, gdy dokument zawierający przedmiot jest aktywowane lub dezaktywowane.

Aby uzyskać więcej informacji, zobacz artykuł [aktywacji](../../mfc/activation-cpp.md)...

##  <a name="onexecolecmd"></a>  COleServerDoc::OnExecOleCmd

Struktura wywołuje tę funkcję, aby wykonywanie określonego polecenia lub wyświetlić Pomoc dla polecenia.

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
Wskaźnik na identyfikator GUID, który identyfikuje zestaw poleceń. Może mieć wartość NULL, aby wskazać polecenie domyślnej grupy.

*nCmdID*<br/>
Polecenie do wykonania. Musi należeć do grupy identyfikowane przez *pguidCmdGroup*.

*nCmdExecOut*<br/>
Sposób obiekt powinien wykonać polecenie, z których co najmniej jeden z następujących wartości z wyliczenia OLECMDEXECOPT:

OLECMDEXECOPT_DODEFAULT

OLECMDEXECOPT_PROMPTUSER

OLECMDEXECOPT_DONTPROMPTUSER

OLECMDEXECOPT_SHOWHELP

*pvarargIn*<br/>
Wskaźnik do VARIANTARG, zawierającą argumenty wejściowe dla polecenia. Może mieć wartości NULL.

*pvarargOut*<br/>
Wskaźnik do VARIANTARG otrzymywać dane wyjściowe zwracają wartości w poleceniu. Może mieć wartości NULL.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia; w przeciwnym razie, jeden z następujących kody błędów:

|Wartość|Opis|
|-----------|-----------------|
|E_UNEXPECTED|Wystąpił nieoczekiwany błąd|
|E_FAIL|Wystąpił błąd|
|E_NOTIMPL|Wskazuje MFC sam powinien próbować translacji i wysyłania polecenia|
|OLECMDERR_E_UNKNOWNGROUP|*pguidCmdGroup* jest różna od NULL, ale nie określa grupę rozpoznawanym poleceniem|
|OLECMDERR_E_NOTSUPPORTED|*nCmdID* nie rozpoznano jako prawidłowego polecenia w grupie *pguidCmdGroup*|
|OLECMDERR_DISABLED|Polecenie identyfikowane przez *nCmdID* jest wyłączona i nie można wykonać|
|OLECMDERR_NOHELP|Obiekt wywołujący pytanie, aby uzyskać pomoc na polecenie identyfikowane przez *nCmdID* , ale nie jest dostępna Pomoc|
|OLECMDERR_CANCELED|Użytkownik anulował wykonanie|

### <a name="remarks"></a>Uwagi

`COleCmdUI` można włączyć, aktualizowanie i ustawić inne właściwości polecenia interfejsu użytkownika DocObject. Po polecenia są inicjowane, można wykonać je za pomocą `OnExecOleCmd`.

Struktura wywołuje funkcję, przed podjęciem próby translacji i wysyłać polecenia dokumentu OLE. Nie musisz przesłonić tę funkcję, aby obsłużyć standardowe polecenia dokumentu OLE, ale należy podać przesłonięcie tej funkcji, jeśli chcesz obsługiwać własne niestandardowe polecenia lub poleceń, które akceptują parametry lub zwracania wyników.

Większość poleceń nie przyjmują argumentów lub zwracanych wartości. W przypadku większości poleceń elementu wywołującego można przekazać wartości null *pvarargIn* i *pvarargOut*. Dla polecenia, które oczekują wartości wejściowych, obiekt wywołujący można zadeklarować i zainicjować zmienną VARIANTARG i przekazać wskaźnik do zmiennej w *pvarargIn*. Polecenia, które wymagają pojedynczej wartości argument można przechowywane bezpośrednio w VARIANTARG i przekazany do funkcji. Wiele argumentów musi zostać spakowana w ramach VARIANTARG przy użyciu jednego z obsługiwanych typów (takich jak `IDispatch` i SAFEARRAY).

Podobnie, jeśli polecenie zwróci obiekt wywołujący oczekuje się, aby zadeklarować VARIANTARG argumentów, zainicjuj ją na VT_EMPTY i przekazania jej adres w *pvarargOut*. Jeśli polecenie zwraca pojedynczą wartość, obiekt może przechowywać wartości bezpośrednio w *pvarargOut*. Wiele wartości danych wyjściowych musi zostać spakowana w jakiś sposób, które są odpowiednie dla VARIANTARG.

Implementacji klasy podstawowej w tej funkcji spowoduje zaprezentuje struktury OLE_COMMAND_MAP skojarzone z elementem docelowym polecenia i spróbuj wysłać polecenie odpowiedni program obsługi. Implementacja klasy bazowej działa tylko w przypadku poleceń, które nie akceptuje argumentów lub nie zwracają wartości. Jeśli potrzebujesz do obsługi poleceń, które akceptuje argumentów lub nie zwracają wartości, należy przesłonić tę funkcję i pracować z *pvarargIn* i *pvarargOut* parametry samodzielnie.

##  <a name="onframewindowactivate"></a>  COleServerDoc::OnFrameWindowActivate

Struktura wywołuje tę funkcję, gdy okno ramowe aplikacji kontenera jest aktywowane lub dezaktywowane.

```
virtual void OnFrameWindowActivate(BOOL bActivate);
```

### <a name="parameters"></a>Parametry

*bActivate*<br/>
Określa, czy okno ramowe ma zostać aktywowane lub dezaktywowane.

### <a name="remarks"></a>Uwagi

Domyślna implementacja anuluje wszystkie tryby pomocy, okno ramowe może być w. Należy przesłonić tę funkcję, jeśli chcesz wykonać specjalnego przetwarzania, gdy okno ramowe jest aktywowane lub dezaktywowane.

Aby uzyskać więcej informacji, zobacz artykuł [aktywacji](../../mfc/activation-cpp.md)...

##  <a name="ongetembeddeditem"></a>  COleServerDoc::OnGetEmbeddedItem

Wywoływane przez platformę, gdy aplikacja kontener wywołuje aplikacji serwera, aby utworzyć lub edytować element osadzony.

```
virtual COleServerItem* OnGetEmbeddedItem() = 0;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do elementu, który reprezentuje cały dokument; Wartość NULL, jeśli operacja nie powiodła się.

### <a name="remarks"></a>Uwagi

Brak implementacji domyślnej. Należy przesłonić tę funkcję, aby zwrócić element, który reprezentuje cały dokument. Zwrócona wartość powinna być obiekt `COleServerItem`-klasy pochodnej.

##  <a name="onreactivateandundo"></a>  COleServerDoc::OnReactivateAndUndo

Struktura wywołuje tę funkcję, gdy użytkownik zdecyduje cofnąć zmiany wprowadzone do elementu, który został aktywowany w miejscu, zmienić i następnie zdezaktywowane.

```
virtual BOOL OnReactivateAndUndo();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Domyślna implementacja z wyjątkiem zwraca wartość FALSE, aby wskazać błąd, nic nie robi.

Należy przesłonić tę funkcję, jeśli aplikacja obsługuje cofania. Zazwyczaj można będzie wykonać operacji cofania, a następnie aktywuj element przez wywołanie metody `ActivateInPlace`. Jeśli aplikacja kontenera są zapisywane przy użyciu biblioteki klas Microsoft Foundation, wywołanie `COleClientItem::ReactivateAndUndo` powoduje, że ta funkcja do wywołania.

##  <a name="onresizeborder"></a>  COleServerDoc::OnResizeBorder

Struktura wywołuje tę funkcję, gdy okno ramowe aplikacji kontenera zmienia rozmiar.

```
virtual void OnResizeBorder(
    LPCRECT lpRectBorder,
    LPOLEINPLACEUIWINDOW lpUIWindow,
    BOOL bFrame);
```

### <a name="parameters"></a>Parametry

*lpRectBorder*<br/>
Wskaźnik do `RECT` struktury lub `CRect` obiekt, który określa współrzędne obramowania.

*lpUIWindow*<br/>
Wskaźnik do obiektu klasy `IOleInPlaceUIWindow` , który jest właścicielem bieżącej sesji edycji w miejscu.

*bFrame*<br/>
Wartość TRUE, jeśli *lpUIWindow* wskazuje okno ramek najwyższego poziomu aplikacji kontenera lub wartość FALSE, jeśli *lpUIWindow* wskazuje okna ramki dokumentu na poziomie aplikacji kontenera.

### <a name="remarks"></a>Uwagi

Ta funkcja zmienia rozmiar i dostosowuje pasków narzędzi i inne elementy interfejsu użytkownika, zgodnie z nowego rozmiaru okna.

Aby uzyskać więcej informacji, zobacz [IOleInPlaceUIWindow](/windows/desktop/api/oleidl/nn-oleidl-ioleinplaceuiwindow) w zestawie Windows SDK.

Jest to zaawansowany możliwym do zastąpienia.

##  <a name="onsethostnames"></a>  COleServerDoc::OnSetHostNames

Wywoływane przez platformę, gdy kontener Ustawia lub zmienia nazwy hostów dla tego dokumentu.

```
virtual void OnSetHostNames(
    LPCTSTR lpszHost,
    LPCTSTR lpszHostObj);
```

### <a name="parameters"></a>Parametry

*lpszHost*<br/>
Wskaźnik do ciągu, który określa nazwę aplikacji kontenera.

*lpszHostObj*<br/>
Wskaźnik do ciągu, który określa nazwę kontenera dla dokumentu.

### <a name="remarks"></a>Uwagi

Domyślna implementacja zmiany nazwy dokumentu, dla wszystkich widoków odwołujące się do tego dokumentu.

Należy przesłonić tę funkcję, jeśli aplikacja ustawia tytułów za pośrednictwem innego mechanizmu.

##  <a name="onsetitemrects"></a>  COleServerDoc::OnSetItemRects

Struktura wywołuje tę funkcję, aby umieścić je w oknie ramki edycji w miejscu okno ramowe aplikacji kontenera.

```
virtual void OnSetItemRects(
    LPCRECT lpPosRect,
    LPCRECT lpClipRect);
```

### <a name="parameters"></a>Parametry

*lpPosRect*<br/>
Wskaźnik do `RECT` struktury lub `CRect` obiekt, który określa pozycję okno ramowe w miejscu względem obszaru klienckiego aplikacji kontenera.

*lpClipRect*<br/>
Wskaźnik do `RECT` struktury lub `CRect` obiekt, który określa Prostokątny wycinek okno ramowe w miejscu względem obszaru klienckiego aplikacji kontenera.

### <a name="remarks"></a>Uwagi

Tę funkcję, aby zaktualizować współczynnika powiększenia widoku, należy zastąpić, jeśli to konieczne.

Ta funkcja jest zazwyczaj wywoływana w odpowiedzi na `RequestPositionChange` wywołać, mimo że można ją wywołać w dowolnym momencie przez kontener do żądania zmiany pozycji elementu w miejscu.

##  <a name="onshowcontrolbars"></a>  COleServerDoc::OnShowControlBars

Struktura wywołuje tę funkcję, aby pokazać lub ukryć paski sterowania aplikacji serwera skojarzony z oknem ramki identyfikowane przez *pFrameWnd*.

```
virtual void OnShowControlBars(
    CFrameWnd* pFrameWnd,
    BOOL bShow);
```

### <a name="parameters"></a>Parametry

*pFrameWnd*<br/>
Wskaźnik do ramki okna, w których paski sterowania powinien ukryte lub pokazane.

*bShow*<br/>
Określa, czy paski sterowania są pokazane lub ukryte.

### <a name="remarks"></a>Uwagi

Domyślna implementacja wylicza wszystkie paski sterowania należące do tej ramki okna i ukrywa lub pokazuje je.

##  <a name="onshowdocument"></a>  COleServerDoc::OnShowDocument

Struktura wywołuje `OnShowDocument` działać w przypadku, gdy dokument serwera musi być ukryte lub pokazane.

```
virtual void OnShowDocument(BOOL bShow);
```

### <a name="parameters"></a>Parametry

*bShow*<br/>
Określa, czy interfejs użytkownika do dokumentu jest widoczny, czy ukryty.

### <a name="remarks"></a>Uwagi

Jeśli *bShow* ma wartość PRAWDA, domyślna implementacja aktywuje aplikacji serwera, jeśli to konieczne i powoduje, że aplikacja kontenera, przewiń jej okna tak, aby element jest widoczny. Jeśli *bShow* ma wartość FAŁSZ, domyślna implementacja dezaktywuje element za pomocą wywołania `OnDeactivate`, a następnie niszczy lub powoduje ukrycie wszystkich okien ramowych utworzone dla dokumentu, z wyjątkiem pierwszej. Jeśli nadal nie widoczne dokumentów, domyślna implementacja ukrywa aplikację serwera.

##  <a name="onupdatedocument"></a>  COleServerDoc::OnUpdateDocument

Wywoływane przez platformę, podczas zapisywania dokumentu, który jest element osadzony w dokumencie złożonym.

```
virtual BOOL OnUpdateDocument();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli dokument został pomyślnie zaktualizowany; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Domyślna implementacja wywołuje [COleServerDoc::NotifySaved](#notifysaved) i [COleServerDoc::SaveEmbedding](#saveembedding) element członkowski funkcji i oznaczy wtedy dokument jako czystych. Należy przesłonić tę funkcję, jeśli chcesz wykonać specjalnego przetwarzania podczas aktualizowania elementu osadzonego.

##  <a name="requestpositionchange"></a>  COleServerDoc::RequestPositionChange

Wywołaj tę funkcję elementu członkowskiego, aby zmienić położenie elementu Wdróż aplikację kontenera.

```
void RequestPositionChange(LPCRECT lpPosRect);
```

### <a name="parameters"></a>Parametry

*lpPosRect*<br/>
Wskaźnik do `RECT` struktury lub `CRect` obiektu zawierającego nowe położenie elementu.

### <a name="remarks"></a>Uwagi

Ta funkcja jest zazwyczaj wywoływana (w połączeniu z `UpdateAllItems`) zmiany danych w aktywny element w miejscu. Po tym wywołaniu kontener może być lub może nie działać zmiany przez wywołanie metody `OnSetItemRects`. Wynikowy pozycja może być inna niż wersja żądana.

##  <a name="saveembedding"></a>  COleServerDoc::SaveEmbedding

Wywołaj tę funkcję, aby poinformować aplikacji kontenera, aby zapisać osadzonego obiektu.

```
void SaveEmbedding();
```

### <a name="remarks"></a>Uwagi

Ta funkcja jest wywoływana automatycznie z `OnUpdateDocument`. Pamiętaj, że ta funkcja powoduje, że element do zaktualizowania na dysku, więc zwykle jest wywoływana tylko w wyniku działania określonego użytkownika.

##  <a name="scrollcontainerby"></a>  COleServerDoc::ScrollContainerBy

Wywołaj `ScrollContainerBy` funkcja elementu członkowskiego, aby przewijać dokumentu kontenera o kwotę, w pikselach, wskazywanym przez `sizeScroll`.

```
BOOL ScrollContainerBy(CSize sizeScroll);
```

### <a name="parameters"></a>Parametry

*sizeScroll*<br/>
Wskazuje, jak daleko jest kontenerem do przewijania.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Dodatnie wartości wskazują, przewijając w dół i w prawo; wartości ujemne wskazują przewijanie w górę i w lewo.

##  <a name="updateallitems"></a>  COleServerDoc::UpdateAllItems

Wywołaj tę funkcję, aby powiadomić wszystkich połączonych elementów podłączone do dokumentu, który został zmieniony dokument.

```
void UpdateAllItems(
    COleServerItem* pSender,
    LPARAM lHint = 0L,
    CObject* pHint = NULL,
    DVASPECT nDrawAspect = DVASPECT_CONTENT);
```

### <a name="parameters"></a>Parametry

*pSender*<br/>
Wskaźnik do elementu, który zmodyfikował dokument, lub wartość NULL, jeśli wszystkie elementy, które mają zostać uaktualnione.

*lHint*<br/>
Zawiera informacje o modyfikacji.

*pHint*<br/>
Wskaźnik do przechowywania informacji o modyfikacji obiektu.

*nDrawAspect*<br/>
Określa, jak element ma być rysowany. Jest to wartość z wyliczenia DVASPECT. Ten parametr może mieć jedną z następujących wartości:

- Element DVASPECT_CONTENT jest reprezentowana w taki sposób, aby go mogą być wyświetlane jako osadzonego obiektu wewnątrz jej kontenera.

- DVASPECT_THUMBNAIL element jest renderowany w reprezentacji "miniaturę", więc, że mogą być wyświetlane w narzędziu do przeglądania.

- Element DVASPECT_ICON jest reprezentowany przez ikonę.

- Element DVASPECT_DOCPRINT jest reprezentowany tak, jakby były drukowane, za pomocą polecenia drukowania, za pomocą menu Plik.

### <a name="remarks"></a>Uwagi

Po użytkownik zmieni dokumentu na serwerze, zwykle Wywołaj tę funkcję. Jeśli element OLE został połączony w dokumencie przy użyciu linku automatyczne, element zostanie zaktualizowany zgodnie ze zmianami. W aplikacjach kontenera napisane przy użyciu biblioteki klas Microsoft Foundation [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) funkcji składowej typu `COleClientItem` jest wywoływana.

Ta funkcja wywołuje `OnUpdate` funkcja elementu członkowskiego dla każdego z elementów dokumentu, z wyjątkiem wysyłania elementu, przekazywanie *pHint*, *lHint*, i *nDrawAspect*. Użyj tych parametrów do przekazania informacji do informacje na temat zmian wprowadzonych do dokumentu. Możesz zakodować informacje przy użyciu *lHint* lub zdefiniować `CObject`-klasy w celu przechowywania informacji na temat zmian, a następnie przekazuje obiekt tej klasy przy użyciu *pHint*. Zastąpienie `OnUpdate` funkcja elementu członkowskiego w Twojej `COleServerItem`— pochodne klasy, aby zoptymalizować aktualizowania każdego elementu w zależności od tego, czy została zmieniona jego prezentacji.

## <a name="see-also"></a>Zobacz także

[Próbki MFC HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[Klasa COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleDocument](../../mfc/reference/coledocument-class.md)<br/>
[Klasa COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)<br/>
[Klasa COleTemplateServer](../../mfc/reference/coletemplateserver-class.md)
