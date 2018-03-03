---
title: Klasa COleServerDoc | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 81b3b8d4c3f25e1c443d5fbcaeddb7b587216d69
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="coleserverdoc-class"></a>Klasa COleServerDoc
Klasa podstawowa dla dokumenty serwera OLE.  
  
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
|[COleServerDoc::ActivateDocObject](#activatedocobject)|Aktywuje skojarzonego dokumentu DocObject.|  
|[COleServerDoc::ActivateInPlace](#activateinplace)|Aktywuje dokument do edycji w miejscu.|  
|[COleServerDoc::DeactivateAndUndo](#deactivateandundo)|Dezaktywuje interfejs użytkownika serwera.|  
|[COleServerDoc::DiscardUndoState](#discardundostate)|Odrzuca wszystkie informacje o stanie cofania.|  
|[COleServerDoc::GetClientSite](#getclientsite)|Pobiera wskaźnik do odpowiadającego `IOleClientSite` interfejsu.|  
|[COleServerDoc::GetEmbeddedItem](#getembeddeditem)|Zwraca wskaźnik do elementu reprezentująca cały dokument.|  
|[COleServerDoc::GetItemClipRect](#getitemcliprect)|Zwraca bieżący Prostokątny wycinek dla edycji w miejscu.|  
|[COleServerDoc::GetItemPosition](#getitemposition)|Zwraca bieżący prostokąt pozycji, względem obszaru klienta aplikacji kontenera, do edycji w miejscu.|  
|[COleServerDoc::GetZoomFactor](#getzoomfactor)|Zwraca współczynnika powiększenia w pikselach.|  
|[COleServerDoc::IsDocObject](#isdocobject)|Określa, czy dokument jest DocObject.|  
|[COleServerDoc::IsEmbedded](#isembedded)|Wskazuje, czy dokument jest osadzony w dokumencie kontenera lub uruchamianie autonomicznego.|  
|[COleServerDoc::IsInPlaceActive](#isinplaceactive)|Zwraca `TRUE` Jeśli element jest obecnie aktywny w miejscu.|  
|[COleServerDoc::NotifyChanged](#notifychanged)|Powiadamia kontenerów, że użytkownik zmienił dokumentu.|  
|[COleServerDoc::NotifyClosed](#notifyclosed)|Powiadamia kontenerów, że użytkownik zamknął dokumentu.|  
|[COleServerDoc::NotifyRename](#notifyrename)|Powiadamia kontenerów, że użytkownik zmienił dokumentu.|  
|[COleServerDoc::NotifySaved](#notifysaved)|Powiadamia kontenerów, że użytkownik został zapisany dokument.|  
|[COleServerDoc::OnDeactivate](#ondeactivate)|Wywoływane przez platformę, gdy użytkownik dezaktywuje element, który został aktywowany w miejscu.|  
|[COleServerDoc::OnDeactivateUI](#ondeactivateui)|Wywoływane przez platformę, by zniszczyć kontrolek i inne elementy interfejsu użytkownika utworzone dla aktywacji w miejscu.|  
|[COleServerDoc::OnDocWindowActivate](#ondocwindowactivate)|Wywoływane przez platformę, gdy okno ramowe kontenera dokumentu jest aktywowane lub dezaktywowane.|  
|[COleServerDoc::OnResizeBorder](#onresizeborder)|Wywoływane przez platformę, gdy zmieniany jest rozmiar okno ramowe aplikacji kontenera lub okna dokumentu.|  
|[COleServerDoc::OnShowControlBars](#onshowcontrolbars)|Wywoływane przez platformę, by pokazać lub ukryć paski sterowania do edycji w miejscu.|  
|[COleServerDoc::OnUpdateDocument](#onupdatedocument)|Wywoływane przez platformę po zapisaniu dokumentu serwera, który jest element osadzony aktualizowanie kontenera kopii elementu.|  
|[COleServerDoc::RequestPositionChange](#requestpositionchange)|Zmienia położenie ramkę do edycji w miejscu.|  
|[COleServerDoc::SaveEmbedding](#saveembedding)|Określa, że aplikacja kontenera można zapisać dokumentu.|  
|[COleServerDoc::ScrollContainerBy](#scrollcontainerby)|Przewija kontenerem.|  
|[COleServerDoc::UpdateAllItems](#updateallitems)|Powiadamia kontenerów, że użytkownik zmienił dokumentu.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleServerDoc::CreateInPlaceFrame](#createinplaceframe)|Wywoływane przez platformę, by utworzyć ramkę okna do edycji w miejscu.|  
|[COleServerDoc::DestroyInPlaceFrame](#destroyinplaceframe)|Wywoływane przez platformę, by zniszczyć okno ramowe do edycji w miejscu.|  
|[COleServerDoc::GetDocObjectServer](#getdocobjectserver)|Przesłonić tę funkcję, aby utworzyć nową `CDocObjectServer` obiektu i wskazywać kontener DocObject tego dokumentu.|  
|[COleServerDoc::OnClose](#onclose)|Wywoływane przez platformę, gdy kontener żąda zamknąć dokument.|  
|[COleServerDoc::OnExecOleCmd](#onexecolecmd)|Wykonuje określone polecenie lub wyświetla Pomoc dla polecenia.|  
|[COleServerDoc::OnFrameWindowActivate](#onframewindowactivate)|Wywoływane przez platformę, gdy okno ramowe kontenera jest aktywowane lub dezaktywowane.|  
|[COleServerDoc::OnGetEmbeddedItem](#ongetembeddeditem)|Wywołuje się, by pobrać `COleServerItem` który reprezentuje cały dokument; używany do pobierania element osadzony. Implementacja wymagane.|  
|[COleServerDoc::OnReactivateAndUndo](#onreactivateandundo)|Wywoływane przez platformę, by cofnąć zmiany wprowadzone podczas edycji w miejscu.|  
|[COleServerDoc::OnSetHostNames](#onsethostnames)|Wywoływane przez platformę, gdy kontener Ustawia tytuł okna dla obiekt osadzony.|  
|[COleServerDoc::OnSetItemRects](#onsetitemrects)|Wywoływane przez platformę, by Umieść okno ramowe w miejscu do edycji w oknie aplikacji kontenera.|  
|[COleServerDoc::OnShowDocument](#onshowdocument)|Wywoływane przez platformę, by pokazać lub ukryć dokumentu.|  
  
## <a name="remarks"></a>Uwagi  
 Dokument serwera może zawierać [COleServerItem](../../mfc/reference/coleserveritem-class.md) obiektów, które reprezentują interfejsu serwera elementy osadzone i połączone. Gdy aplikacja serwera jest uruchamiana przez kontener, aby edytować element osadzony, element jest ładowany jako własny dokument serwera; `COleServerDoc` obiekt zawiera co najmniej jeden `COleServerItem` obiekt składający się z całego dokumentu. Gdy aplikacja serwera jest uruchomiona przez kontener do edycji połączonego elementu, istniejącego dokumentu są ładowane z dysku; część treści dokumentu jest wyróżniony, aby wskazać połączonego elementu.  
  
 `COleServerDoc`obiekty mogą zawierać również elementów [COleClientItem](../../mfc/reference/coleclientitem-class.md) klasy. Umożliwia tworzenie aplikacji kontenera serwera. Platformę udostępnia funkcje do przechowywania prawidłowo `COleClientItem` elementów podczas obsługi `COleServerItem` obiektów.  
  
 Jeśli aplikacja serwera nie obsługuje łącza, dokument serwera zawsze będzie zawierać tylko jeden element serwera, który reprezentuje cały obiekt osadzony jako dokument. Jeśli aplikacja serwera obsługuje łącza, musi utworzyć element serwera zawsze, gdy zaznaczenie jest kopiowany do Schowka.  
  
 Aby użyć `COleServerDoc`, pochodną klasy i wykonywania [OnGetEmbeddedItem](#ongetembeddeditem) funkcji członkowskiej, dzięki czemu serwer do obsługi elementy osadzone. Klasa wyprowadzona z `COleServerItem` implementuje elementy w dokumentach i zwracać obiekty klas z `OnGetEmbeddedItem`.  
  
 Do obsługi połączone elementy `COleServerDoc` zapewnia [OnGetLinkedItem](../../mfc/reference/colelinkingdoc-class.md#ongetlinkeditem) funkcję elementu członkowskiego. Można użyć w implementacji domyślnej lub ją zastąpić, jeśli mają własne sposób zarządzania elementów dokumentu.  
  
 Potrzebna jest jedna `COleServerDoc`-pochodnej klasy dla każdego typu serwera dokumentu obsługuje Twojej aplikacji. Na przykład, jeśli aplikacja serwera obsługuje arkuszy i wykresów, potrzebne są dwa `COleServerDoc`-klas pochodnych.  
  
 Aby uzyskać więcej informacji na serwerach, zobacz artykuł [serwery: Implementowanie serwera](../../mfc/servers-implementing-a-server.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocument](../../mfc/reference/cdocument-class.md)  
  
 [COleDocument](../../mfc/reference/coledocument-class.md)  
  
 [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)  
  
 `COleServerDoc`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxole.h  
  
##  <a name="activatedocobject"></a>COleServerDoc::ActivateDocObject  
 Aktywuje skojarzonego dokumentu DocObject.  
  
```  
void ActivateDocObject();
```  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie `COleServerDoc` nie obsługuje dokumentów aktywnych (zwaną także DocObjects). Aby włączyć tę obsługę, zobacz [GetDocObjectServer](#getdocobjectserver) i klasa [CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md).  
  
##  <a name="activateinplace"></a>COleServerDoc::ActivateInPlace  
 Aktywuje elementu dla edycji w miejscu.  
  
```  
BOOL ActivateInPlace();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie wartość 0, który wskazuje, że element jest całkowicie otwarte.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja wykonuje wszystkie operacje niezbędne do aktywacji w miejscu. Go tworzy okno ramowe w miejscu, aktywuje go i rozmiary go do elementu konfiguruje udostępnionego menu i inne formanty, można przewinąć element w widoku i ustawia fokus okno ramowe w miejscu.  
  
 Ta funkcja jest wywoływana przez domyślną implementację elementu [COleServerItem::OnShow](../../mfc/reference/coleserveritem-class.md#onshow). Wywołanie tej funkcji, jeśli aplikacja obsługuje innego zlecenie dla aktywacji w miejscu (na przykład Play).  
  
##  <a name="coleserverdoc"></a>COleServerDoc::COleServerDoc  
 Konstruuje `COleServerDoc` obiektu bez połączenia z systemem OLE biblioteki dll.  
  
```  
COleServerDoc();
```  
  
### <a name="remarks"></a>Uwagi  
 Należy wywołać [COleLinkingDoc::Register](../../mfc/reference/colelinkingdoc-class.md#register) otworzyć komunikacji z OLE. Jeśli używasz [COleTemplateServer](../../mfc/reference/coletemplateserver-class.md) w aplikacji, `COleLinkingDoc::Register` jest wywoływana przez `COleLinkingDoc`w implementacji `OnNewDocument`, `OnOpenDocument`, i `OnSaveDocument`.  
  
##  <a name="createinplaceframe"></a>COleServerDoc::CreateInPlaceFrame  
 Struktura wywołuje tę funkcję, aby utworzyć ramkę okna do edycji w miejscu.  
  
```  
virtual COleIPFrameWnd* CreateInPlaceFrame(CWnd* pParentWnd);
```  
  
### <a name="parameters"></a>Parametry  
 `pParentWnd`  
 Wskaźnik do aplikacji kontenera nadrzędnego okna.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do okno ramowe w miejscu lub **NULL** w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja używa informacji z szablonu do utworzenia ramki. Widok używany jest pierwszym widokiem utworzone dla dokumentu. Ten widok jest tymczasowo odłączone od oryginalnego ramki i dołączyć do nowo utworzony ramki.  
  
 Jest to zaawansowane możliwym do zastąpienia.  
  
##  <a name="deactivateandundo"></a>COleServerDoc::DeactivateAndUndo  
 Wywołanie tej funkcji, jeśli cofnąć obsługuje Twojej aplikacji i użytkownik wybierze cofania po aktywowaniu elementu, ale przed jego edycji.  
  
```  
BOOL DeactivateAndUndo();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji powoduje, że jeśli aplikacja kontenera jest zapisywany przy użyciu Microsoft Foundation Class Library, [COleClientItem::OnDeactivateAndUndo](../../mfc/reference/coleclientitem-class.md#ondeactivateandundo) do wywołania, które dezaktywuje interfejs użytkownika serwera.  
  
##  <a name="destroyinplaceframe"></a>COleServerDoc::DestroyInPlaceFrame  
 Struktura wywołuje tę funkcję, aby zniszczyć okno ramowe w miejscu i przywrócić okna dokumentów aplikacji serwera do stanu przed Aktywacja w miejscu.  
  
```  
virtual void DestroyInPlaceFrame(COleIPFrameWnd* pFrameWnd);
```  
  
### <a name="parameters"></a>Parametry  
 `pFrameWnd`  
 Wskaźnik do okno ramowe w miejscu do zniszczenia.  
  
### <a name="remarks"></a>Uwagi  
 Jest to zaawansowane możliwym do zastąpienia.  
  
##  <a name="discardundostate"></a>COleServerDoc::DiscardUndoState  
 Jeśli użytkownik wykona operację edycji, którego nie można cofnąć, wywołanie tej funkcji, aby wymusić aplikacji kontenera, aby odrzucić informacje stanu cofania.  
  
```  
BOOL DiscardUndoState();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja ta zapewnia tak, aby zwolnić zasoby, które w przeciwnym razie może być zużyte przez informacji o stanie cofania, której nie można użyć serwerów, które obsługuje operacji cofania.  
  
##  <a name="getclientsite"></a>COleServerDoc::GetClientSite  
 Pobiera wskaźnik do odpowiadającego `IOleClientSite` interfejsu.  
  
```  
LPOLECLIENTSITE GetClientSite() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Pobiera wskaźnik do odpowiadającego [IOleClientSite](http://msdn.microsoft.com/library/windows/desktop/ms693706) interfejsu.  
  
##  <a name="getdocobjectserver"></a>COleServerDoc::GetDocObjectServer  
 Przesłonić tę funkcję, aby utworzyć nową `CDocObjectServer` element i zwraca wskaźnik do niego.  
  
```  
virtual CDocObjectServer* GetDocObjectServer(LPOLEDOCUMENTSITE pDocSite);
```  
  
### <a name="parameters"></a>Parametry  
 `pDocSite`  
 Wskaźnik do `IOleDocumentSite` interfejs, który będzie nawiązują połączenia z serwerem tego dokumentu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `CDocObjectServer`; **NULL** Jeśli działanie nie powiodło się.  
  
### <a name="remarks"></a>Uwagi  
 Po aktywowaniu serwera DocObject, powrotu niż **NULL** wskaźnik pokazuje, że klient może obsługiwać DocObjects. Domyślna implementacja zwraca **NULL**.  
  
 Typowa implementacja dla dokumentu, który obsługuje DocObjects przyzna po prostu nową `CDocObjectServer` obiektów i przywrócić go do obiektu wywołującego. Na przykład:  
  
 [!code-cpp[NVC_MFCOleServer#3](../../mfc/codesnippet/cpp/coleserverdoc-class_1.cpp)]  
  
##  <a name="getembeddeditem"></a>COleServerDoc::GetEmbeddedItem  
 Wywołanie tej funkcji, otrzymywać wskaźnik do elementu reprezentująca cały dokument.  
  
```  
COleServerItem* GetEmbeddedItem();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do elementu reprezentująca cały dokument; **NULL** Jeśli działanie nie powiodło się.  
  
### <a name="remarks"></a>Uwagi  
 Wywołuje [COleServerDoc::OnGetEmbeddedItem](#ongetembeddeditem), funkcją wirtualną z żadnej implementacji domyślnej.  
  
##  <a name="getitemcliprect"></a>COleServerDoc::GetItemClipRect  
 Wywołanie `GetItemClipRect` funkcji członkowskiej, by uzyskać prostokątny wycinek współrzędne elementu, który jest edytowany w miejscu.  
  
```  
void GetItemClipRect(LPRECT lpClipRect) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `lpClipRect`  
 Wskaźnik do `RECT` struktury lub `CRect` obiektu do odbierania współrzędne Prostokątny wycinek elementu.  
  
### <a name="remarks"></a>Uwagi  
 Współrzędne są podawane w pikselach względem obszaru klienckiego okna aplikacji kontenera.  
  
 Rysowanie nie powinien wystąpić poza prostokątem wycinka. Zazwyczaj rysunku jest automatycznie ograniczany. Ta funkcja służy do określenia, czy użytkownik ma przewijane poza widoczną część dokumentu. Jeśli tak, przewiń dokument o kontenera, w razie potrzeby za pomocą wywołania [ScrollContainerBy](#scrollcontainerby).  
  
##  <a name="getitemposition"></a>COleServerDoc::GetItemPosition  
 Wywołanie `GetItemPosition` funkcji członkowskiej, by uzyskać współrzędne elementu edytowany w miejscu.  
  
```  
void GetItemPosition(LPRECT lpPosRect) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `lpPosRect`  
 Wskaźnik do `RECT` struktury lub `CRect` obiektu do odbierania współrzędne elementu.  
  
### <a name="remarks"></a>Uwagi  
 Współrzędne są podawane w pikselach względem obszaru klienckiego okna aplikacji kontenera.  
  
 Położenie elementu można porównać z bieżącego Prostokątny wycinek w celu ustalenia zakresu, do którego element jest widoczny (lub nie jest widoczny) na ekranie.  
  
##  <a name="getzoomfactor"></a>COleServerDoc::GetZoomFactor  
 `GetZoomFactor` Funkcji członkowskiej określa "współczynnika powiększenia" elementu, który został aktywowany do edycji w miejscu.  
  
```  
BOOL GetZoomFactor(
    LPSIZE lpSizeNum = NULL,  
    LPSIZE lpSizeDenom = NULL,  
    LPCRECT lpPosRect = NULL) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *lpSizeNum*  
 Wskaźnik do obiektu klasy `CSize` który wstrzymuje Licznik współczynnika powiększenia. Może być **NULL**.  
  
 *lpSizeDenom*  
 Wskaźnik do obiektu klasy `CSize` który wstrzymuje denominator współczynnika powiększenia. Może być **NULL**.  
  
 `lpPosRect`  
 Wskaźnik do obiektu klasy `CRect` opisujący elementu w nowe położenie. Jeśli ten argument jest **NULL**, funkcja używa elementu w bieżącym położeniu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli element został aktywowany dla w miejscu edycji i jego współczynnika powiększenia jest inne niż 100% (1:1); w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Współczynnika powiększenia w pikselach, jest część rozmiar elementu w jego bieżącym zakresie. Jeśli aplikacja kontenera nie ma ustawionej elementu w zakresie, jej zakres fizycznych (zgodnie z ustaleniami [COleServerItem::OnGetExtent](../../mfc/reference/coleserveritem-class.md#ongetextent)) jest używany.  
  
 Funkcja ustawia pierwsze dwa argumenty licznik i mianownik elementu "współczynnika powiększenia." Jeśli element nie jest edytowany w miejscu, funkcja ustawia tych argumentów do domyślnej wartości 100% (lub 1:1) i zwraca wartość zero. Aby uzyskać więcej informacji, zobacz 40 Uwaga techniczna [zmiany rozmiaru w miejscu MFC/OLE i powiększenie](../../mfc/tn040-mfc-ole-in-place-resizing-and-zooming.md).  
  
##  <a name="isdocobject"></a>COleServerDoc::IsDocObject  
 Określa, czy dokument jest DocObject.  
  
```  
BOOL IsDocObject() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 **Wartość TRUE,** Jeśli dokument jest DocObject; w przeciwnym razie **FALSE**.  
  
##  <a name="isembedded"></a>COleServerDoc::IsEmbedded  
 Wywołanie `IsEmbedded` funkcji członkowskiej, aby określić, czy dokument reprezentuje obiektu osadzonego w kontenerze.  
  
```  
BOOL IsEmbedded() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli podano niezerowe `COleServerDoc` obiekt jest dokument, który reprezentuje obiekt osadzony w kontenerze; w przeciwnym razie wartość 0.  
  
### <a name="remarks"></a>Uwagi  
 W przypadku dokumentu z pliku nie jest zagnieżdżony, chociaż może manipulować przez aplikację jako łącze do kontenera. Dokument, który jest osadzony w dokumencie kontenera jest uznawany za do osadzenia.  
  
##  <a name="isinplaceactive"></a>COleServerDoc::IsInPlaceActive  
 Wywołanie `IsInPlaceActive` funkcji członkowskiej, aby określić, czy element jest aktywny w miejscu.  
  
```  
BOOL IsInPlaceActive() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli podano niezerowe `COleServerDoc` obiekt jest aktywny w miejscu; w przeciwnym razie wartość 0.  
  
##  <a name="notifychanged"></a>COleServerDoc::NotifyChanged  
 Wywołanie tej funkcji, aby powiadomić wszystkich połączonych elementów podłączone do dokumentu, że dokument został zmieniony.  
  
```  
void NotifyChanged();
```  
  
### <a name="remarks"></a>Uwagi  
 Zazwyczaj tej funkcji należy wywołać po użytkownik zmieni niektórych globalny atrybut, taki jak wymiary dokumentu na serwerze. Jeśli element OLE jest połączony z dokumentu przy użyciu automatycznego link, aby odzwierciedlić zmiany zaktualizowaniem elementu. W aplikacjach kontenera napisane na platformie Microsoft Foundation Class Library [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) funkcji członkowskiej klasy `COleClientItem` jest wywoływana.  
  
> [!NOTE]
>  Ta funkcja jest uwzględniona w celu zapewnienia zgodności z OLE 1. Nowe aplikacje powinny używać [UpdateAllItems](#updateallitems).  
  
##  <a name="notifyclosed"></a>COleServerDoc::NotifyClosed  
 Wywołanie tej funkcji, aby powiadomić kontenerów, że dokument został zamknięty.  
  
```  
void NotifyClosed();
```  
  
### <a name="remarks"></a>Uwagi  
 Gdy użytkownik wybierze polecenie Zamknij z menu Plik `NotifyClosed` jest wywoływana przez `COleServerDoc`w implementacji [OnCloseDocument](../../mfc/reference/cdocument-class.md#onclosedocument) funkcję elementu członkowskiego. W aplikacjach kontenera napisane na platformie Microsoft Foundation Class Library [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) funkcji członkowskiej klasy `COleClientItem` jest wywoływana.  
  
##  <a name="notifyrename"></a>COleServerDoc::NotifyRename  
 Wywołanie tej funkcji po użytkownik zmienia nazwę dokumentu na serwerze.  
  
```  
void NotifyRename(LPCTSTR lpszNewName);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszNewName`  
 Wskaźnik do ciąg określający nazwę nowego dokumentu na serwerze; Zazwyczaj jest w pełni kwalifikowana.  
  
### <a name="remarks"></a>Uwagi  
 Gdy użytkownik wybierze polecenie Zapisz jako z menu Plik `NotifyRename` jest wywoływana przez `COleServerDoc`w implementacji [OnSaveDocument](../../mfc/reference/cdocument-class.md#onsavedocument) funkcji członkowskiej. Ta funkcja informuje system bibliotek DLL, które z kolei powiadamiać kontenery OLE. W aplikacjach kontenera napisane na platformie Microsoft Foundation Class Library [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) funkcji członkowskiej klasy `COleClientItem` jest wywoływana.  
  
##  <a name="notifysaved"></a>COleServerDoc::NotifySaved  
 Wywołanie tej funkcji po użytkownik zapisuje dokument serwera.  
  
```  
void NotifySaved();
```  
  
### <a name="remarks"></a>Uwagi  
 Gdy użytkownik wybierze polecenie Zapisz z menu Plik `NotifySaved` jest wywoływana przez `COleServerDoc`w implementacji [OnSaveDocument](../../mfc/reference/cdocument-class.md#onsavedocument). Ta funkcja informuje system bibliotek DLL, które z kolei powiadamiać kontenery OLE. W aplikacjach kontenera napisane na platformie Microsoft Foundation Class Library [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) funkcji członkowskiej klasy `COleClientItem` jest wywoływana.  
  
##  <a name="onclose"></a>COleServerDoc::OnClose  
 Wywoływane przez platformę, gdy kontener żąda zamknąć dokument serwera.  
  
```  
virtual void OnClose(OLECLOSE dwCloseOption);
```  
  
### <a name="parameters"></a>Parametry  
 `dwCloseOption`  
 Wartość z wyliczenia `OLECLOSE`. Ten parametr może mieć jedną z następujących wartości:  
  
- `OLECLOSE_SAVEIFDIRTY`Plik jest zapisywany, jeśli został on zmodyfikowany.  
  
- `OLECLOSE_NOSAVE`Ten plik będzie zamknięty bez zapisywania.  
  
- `OLECLOSE_PROMPTSAVE`Jeśli plik został zmodyfikowany, użytkownik jest monitowany o zapisanie go.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja wywołuje `CDocument::OnCloseDocument`.  
  
 Aby uzyskać więcej informacji i dodatkowe wartości, zobacz [OLECLOSE](http://msdn.microsoft.com/library/windows/desktop/ms680623) w zestawie Windows SDK.  
  
##  <a name="ondeactivate"></a>COleServerDoc::OnDeactivate  
 Wywoływane przez platformę, gdy użytkownik dezaktywuje element osadzony lub połączony, który jest obecnie aktywny w miejscu.  
  
```  
virtual void OnDeactivate();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja przywraca interfejsu użytkownika aplikacji kontenera do stanu pierwotnego i niszczy dowolnego menu i inne formanty, które zostały utworzone dla aktywacji w miejscu.  
  
 Informacje o stanie cofania powinny zostać zwolnione bezwarunkowo w tym momencie.  
  
 Aby uzyskać więcej informacji, zobacz artykuł [aktywacji](../../mfc/activation-cpp.md)...  
  
##  <a name="ondeactivateui"></a>COleServerDoc::OnDeactivateUI  
 Wywoływane, gdy użytkownik dezaktywuje element, który został aktywowany w miejscu.  
  
```  
virtual void OnDeactivateUI(BOOL bUndoable);
```  
  
### <a name="parameters"></a>Parametry  
 `bUndoable`  
 Określa, czy edycję można cofnąć.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja przywraca interfejsu użytkownika aplikacji kontenera do stanu pierwotnego ukrywanie dowolnego menu i inne formanty, które zostały utworzone dla aktywacji w miejscu.  
  
 Zawsze ustawia platformę `bUndoable` do **FALSE**. Jeśli serwer obsługuje cofania i można cofnąć operację, wywołanie implementacji klasy podstawowej z `bUndoable` ustawioną **TRUE**.  
  
##  <a name="ondocwindowactivate"></a>COleServerDoc::OnDocWindowActivate  
 Struktura wywołuje tę funkcję, aby aktywować lub dezaktywować okno dokumentu do edycji w miejscu.  
  
```  
virtual void OnDocWindowActivate(BOOL bActivate);
```  
  
### <a name="parameters"></a>Parametry  
 `bActivate`  
 Określa, czy okno dokumentu jest aktywowany lub dezaktywowany.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja usuwa lub dodaje elementy interfejsu użytkownika na poziomie ramki zależnie od potrzeb. Należy przesłonić tę funkcję, jeśli chcesz wykonać dodatkowe akcje w przypadku, gdy dokument zawierający tego elementu jest aktywowane lub dezaktywowane.  
  
 Aby uzyskać więcej informacji, zobacz artykuł [aktywacji](../../mfc/activation-cpp.md)...  
  
##  <a name="onexecolecmd"></a>COleServerDoc::OnExecOleCmd  
 Struktura wywołuje tę funkcję na wykonanie określonego polecenia lub wyświetlić Pomoc dla polecenia.  
  
```  
virtual HRESULT OnExecOleCmd(
    const GUID* pguidCmdGroup,  
    DWORD nCmdID,  
    DWORD nCmdExecOpt,  
    VARIANTARG* pvarargIn,  
    VARIANTARG* pvarargOut);
```  
  
### <a name="parameters"></a>Parametry  
 `pguidCmdGroup`  
 Wskaźnik do identyfikatora GUID, który identyfikuje zestaw poleceń. Może być **NULL** wskazująca domyślnej grupy polecenia.  
  
 `nCmdID`  
 Polecenie do wykonania. Musi należeć do grupy identyfikowanej przez `pguidCmdGroup`.  
  
 *nCmdExecOut*  
 Sposób obiekt powinien zostać wykonany polecenie jedną lub więcej z następujących wartości z **OLECMDEXECOPT** wyliczenie:  
  
 **OLECMDEXECOPT_DODEFAULT**  
  
 **OLECMDEXECOPT_PROMPTUSER**  
  
 **OLECMDEXECOPT_DONTPROMPTUSER**  
  
 **OLECMDEXECOPT_SHOWHELP**  
  
 `pvarargIn`  
 Wskaźnik do **VARIANTARG** zawierający argumenty wejściowe dla polecenia. Może być **NULL**.  
  
 `pvarargOut`  
 Wskaźnik do **VARIANTARG** do odbierania wartości zwracanych danych wyjściowych polecenia. Może być **NULL**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` przypadku powodzenia; w przeciwnym razie wartość jednego z następujących kodów błędów:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|**E_UNEXPECTED**|Wystąpił nieoczekiwany błąd|  
|**E_FAIL**|Wystąpił błąd|  
|**E_NOTIMPL**|Wskazuje MFC sam powinien próbować tłumaczenie i wysyłania polecenia|  
|**OLECMDERR_E_UNKNOWNGROUP**|`pguidCmdGroup`ma wartość inną niż **NULL** , ale nie określa grupę rozpoznanego polecenia|  
|**OLECMDERR_E_NOTSUPPORTED**|`nCmdID`Nie rozpoznano jako prawidłowego polecenia w grupie`pguidCmdGroup`|  
|**OLECMDERR_DISABLED**|Polecenie identyfikowane przez `nCmdID` jest wyłączona i nie można wykonać|  
|**OLECMDERR_NOHELP**|Obiekt wywołujący w opiniach pomocy w polecenie identyfikowane przez `nCmdID` , ale nie jest dostępna Pomoc|  
|**OLECMDERR_CANCELED**|Użytkownik anulował wykonywania|  
  
### <a name="remarks"></a>Uwagi  
 `COleCmdUI`można włączyć, zaktualizowania i ustawić inne właściwości polecenia interfejsu użytkownika DocObject. Po polecenia są inicjowane, można wykonać je za pomocą `OnExecOleCmd`.  
  
 Struktura wywołuje funkcję przed podjęciem próby tłumaczenie i wysyłać polecenia dokumentu OLE. Nie musisz przesłonić tę funkcję do obsługi standardowych poleceń dokumentu OLE, ale do obsługi własnych niestandardowych poleceń lub poleceń, które akceptują parametrów lub zwracają wyniki, musisz podać zastąpienia tej funkcji.  
  
 Większość potrzebnych poleceń nie przyjmuje argumentów lub wartości zwracanych. Dla większości poleceń można przekazać wywołującego **NULL**s dla `pvarargIn` i `pvarargOut`. Dla polecenia, które oczekuje wartości wejściowe, wywołujący można zadeklarować i zainicjuj **VARIANTARG** zmiennej, a następnie przekaż wskaźnik do zmiennej w `pvarargIn`. Dla polecenia, które wymagają pojedynczą wartość, argument mogą być przechowywane bezpośrednio w **VARIANTARG** i przekazany do funkcji. Używanie wielu argumentów muszą być spakowane w **VARIANTARG** przy użyciu jednego z obsługiwanych typów (takich jak `IDispatch` i **SAFEARRAY** ).  
  
 Podobnie, jeśli polecenie zwróci argumenty wywołujący powinien deklarować **VARIANTARG**, aby zainicjować `VT_EMPTY`i podaj adres w `pvarargOut`. Jeśli polecenie zwraca pojedynczą wartość, obiekt może przechowywać tej wartości bezpośrednio w `pvarargOut`. Wiele wartości danych wyjściowych muszą być spakowane w jakiś sposób odpowiednie dla **VARIANTARG**.  
  
 Przeprowadzi klasy podstawowej stosowania tej funkcji **OLE_COMMAND_MAP** struktury związanych z docelowym polecenia i spróbuj wysłać polecenie odpowiedni program obsługi. Implementacja klasy podstawowej działa tylko z poleceniami, które nie akceptuje argumentów i wartości zwracane. Jeśli wymagana jest obsługa polecenia, które akceptuje argumentów ani zwracać wartości, należy przesłonić tę funkcję i pracować z `pvarargIn` i `pvarargOut` parametry samodzielnie.  
  
##  <a name="onframewindowactivate"></a>COleServerDoc::OnFrameWindowActivate  
 Struktura wywołuje tej funkcji, gdy okno ramowe aplikacji kontenera jest aktywowane lub dezaktywowane.  
  
```  
virtual void OnFrameWindowActivate(BOOL bActivate);
```  
  
### <a name="parameters"></a>Parametry  
 `bActivate`  
 Określa, czy okno ramowe ma być aktywowany lub dezaktywowany.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja anuluje wszystkie tryby pomocy okno ramowe może być w. Należy przesłonić tę funkcję, jeśli chcesz wykonać specjalnego przetwarzania, gdy okno ramowe jest aktywowane lub dezaktywowane.  
  
 Aby uzyskać więcej informacji, zobacz artykuł [aktywacji](../../mfc/activation-cpp.md)...  
  
##  <a name="ongetembeddeditem"></a>COleServerDoc::OnGetEmbeddedItem  
 Wywoływane przez platformę, gdy aplikacja kontener wywołuje aplikacji serwera, aby utworzyć lub edytować element osadzony.  
  
```  
virtual COleServerItem* OnGetEmbeddedItem() = 0;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do elementu reprezentująca cały dokument; **NULL** Jeśli działanie nie powiodło się.  
  
### <a name="remarks"></a>Uwagi  
 Brak implementacji domyślnej. Konieczne jest przesłonięcie tej funkcji, aby powrócić do elementu, który reprezentuje cały dokument. Zwrócona wartość powinna być obiektu `COleServerItem`-klasy.  
  
##  <a name="onreactivateandundo"></a>COleServerDoc::OnReactivateAndUndo  
 Struktura wywołuje tej funkcji, jeśli użytkownik zdecyduje cofnąć zmiany elementu, który został aktywowany w miejscu, zmienić i następnie dezaktywowane.  
  
```  
virtual BOOL OnReactivateAndUndo();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja nie robi nic, z wyjątkiem powrotu **FALSE** do wskazania błędu.  
  
 Należy przesłonić tę funkcję, jeśli aplikacja obsługuje cofania. Zazwyczaj można będzie wykonać operacji cofania, a następnie uaktywnić przez wywołanie elementu `ActivateInPlace`. Jeśli aplikacja kontenera został napisany z Microsoft Foundation Class Library, wywoływania `COleClientItem::ReactivateAndUndo` powoduje, że tej funkcji do wywołania.  
  
##  <a name="onresizeborder"></a>COleServerDoc::OnResizeBorder  
 Struktura wywołuje tej funkcji po okna ramowe aplikacji kontenera zmiany rozmiaru.  
  
```  
virtual void OnResizeBorder(
    LPCRECT lpRectBorder,  
    LPOLEINPLACEUIWINDOW lpUIWindow,  
    BOOL bFrame);
```  
  
### <a name="parameters"></a>Parametry  
 `lpRectBorder`  
 Wskaźnik do `RECT` struktury lub `CRect` obiekt określający współrzędne obramowania.  
  
 `lpUIWindow`  
 Wskaźnik do obiektu klasy **IOleInPlaceUIWindow** , który jest właścicielem bieżącej sesji edycji w miejscu.  
  
 *bFrame*  
 **Wartość TRUE,** Jeśli `lpUIWindow` wskazuje okna ramowego najwyższego poziomu aplikacji kontenera, lub **FALSE** Jeśli `lpUIWindow` wskazuje okien ramowych dokumentu na poziomie aplikacji kontenera.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja zmienia rozmiar i dostosowuje paski narzędzi oraz inne elementy interfejsu użytkownika, zgodnie z nowy rozmiar okna.  
  
 Aby uzyskać więcej informacji, zobacz [IOleInPlaceUIWindow](http://msdn.microsoft.com/library/windows/desktop/ms680716) w zestawie Windows SDK.  
  
 Jest to zaawansowane możliwym do zastąpienia.  
  
##  <a name="onsethostnames"></a>COleServerDoc::OnSetHostNames  
 Wywoływane przez platformę, gdy kontener Ustawia lub zmienia nazwy hostów dla tego dokumentu.  
  
```  
virtual void OnSetHostNames(
    LPCTSTR lpszHost,  
    LPCTSTR lpszHostObj);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszHost`  
 Wskaźnik do ciąg określający nazwę kontenera aplikacji.  
  
 `lpszHostObj`  
 Wskaźnik do ciąg określający nazwę kontenera dokumentu.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja zmiany nazwy dokumentu dla wszystkich widoków odwołujących się do tego dokumentu.  
  
 Należy przesłonić tę funkcję, jeśli aplikacja ustawia tytuły przez inny mechanizm.  
  
##  <a name="onsetitemrects"></a>COleServerDoc::OnSetItemRects  
 Struktura wywołuje tę funkcję, aby umieścić je w oknie ramowym edycji w miejscu okno ramowe aplikacji kontenera.  
  
```  
virtual void OnSetItemRects(
    LPCRECT lpPosRect,  
    LPCRECT lpClipRect);
```  
  
### <a name="parameters"></a>Parametry  
 `lpPosRect`  
 Wskaźnik do `RECT` struktury lub `CRect` obiekt, który określa położenie okno ramowe w miejscu względem obszaru klienckiego aplikacji kontenera.  
  
 `lpClipRect`  
 Wskaźnik do `RECT` struktury lub `CRect` obiekt, który określa Prostokątny wycinek okno ramowe w miejscu względem obszaru klienckiego aplikacji kontenera.  
  
### <a name="remarks"></a>Uwagi  
 Zastąpienie tej funkcji, aby zaktualizować współczynnika powiększenia widoku, jeśli to konieczne.  
  
 Ta funkcja jest zazwyczaj wywoływana w odpowiedzi na `RequestPositionChange` wywołać, mimo że może ona zostać wywołana w dowolnym momencie przez kontener na żądanie zmiany pozycji dla elementu w miejscu.  
  
##  <a name="onshowcontrolbars"></a>COleServerDoc::OnShowControlBars  
 Struktura wywołuje tę funkcję, aby pokazać lub ukryć paski sterowania aplikacji serwera skojarzone z okno ramowe identyfikowane przez `pFrameWnd`.  
  
```  
virtual void OnShowControlBars(
    CFrameWnd* pFrameWnd,  
    BOOL bShow);
```  
  
### <a name="parameters"></a>Parametry  
 `pFrameWnd`  
 Wskaźnik do okno ramowe, którego paski sterowania powinny być ukryte lub pokazane.  
  
 `bShow`  
 Określa, czy paski sterowania są pokazywane lub ukryte.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja wylicza wszystkie paski sterowania należących do tej ramki okna i ukrywa lub je zawiera.  
  
##  <a name="onshowdocument"></a>COleServerDoc::OnShowDocument  
 Wywołania framework `OnShowDocument` działać, jeśli dokument serwera musi być ukryte lub pokazane.  
  
```  
virtual void OnShowDocument(BOOL bShow);
```  
  
### <a name="parameters"></a>Parametry  
 `bShow`  
 Określa, czy interfejs użytkownika do dokumentu jest pokazywane lub ukryte.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `bShow` jest **TRUE**, domyślna implementacja aktywuje aplikacji serwera, jeśli to konieczne i powoduje, że aplikacja kontenera do przewijania okna tak, aby ten element jest widoczny. Jeśli `bShow` jest **FALSE**, domyślna implementacja dezaktywuje element poprzez wywołanie `OnDeactivate`, niszczy lub powoduje ukrycie wszystkich okien ramki, które zostały utworzone dla dokumentu, z wyjątkiem pierwszej. Jeśli nadal nie widoczne dokumentów, domyślna implementacja ukrywa aplikacji serwera.  
  
##  <a name="onupdatedocument"></a>COleServerDoc::OnUpdateDocument  
 Wywoływane przez platformę, gdy zapisywania dokumentu jest element osadzony wewnątrz złożonego dokumentu.  
  
```  
virtual BOOL OnUpdateDocument();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli dokument został pomyślnie zaktualizowany; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja wywołuje [COleServerDoc::NotifySaved](#notifysaved) i [COleServerDoc::SaveEmbedding](#saveembedding) funkcje Członkowskie, a następnie oznacza dokumentu jako czystych. Należy przesłonić tę funkcję, jeśli chcesz wykonać specjalne przetwarzania podczas aktualizowania osadzonych elementu.  
  
##  <a name="requestpositionchange"></a>COleServerDoc::RequestPositionChange  
 Wywołanie tej funkcji elementu członkowskiego, aby zmienić położenie elementu w aplikacji kontenera.  
  
```  
void RequestPositionChange(LPCRECT lpPosRect);
```  
  
### <a name="parameters"></a>Parametry  
 `lpPosRect`  
 Wskaźnik do `RECT` struktury lub `CRect` obiektu zawierającego elementu w nowe położenie.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest zazwyczaj wywoływana (łącznie z `UpdateAllItems`) zmiany danych w elemencie aktywny w miejscu. Po tym wywołaniu kontener może lub nie może przeprowadzić zmiany wywołując `OnSetItemRects`. Wynikowa pozycji może być inna niż wersja żądana.  
  
##  <a name="saveembedding"></a>COleServerDoc::SaveEmbedding  
 Wywołaj tę funkcję, aby sprawdzić aplikacji kontenera, aby zapisać osadzonego obiektu.  
  
```  
void SaveEmbedding();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest wywoływana automatycznie z `OnUpdateDocument`. Należy pamiętać, że ta funkcja powoduje, że element do aktualizacji na dysku, dlatego zazwyczaj jest to tylko w wyniku akcji określonego użytkownika.  
  
##  <a name="scrollcontainerby"></a>COleServerDoc::ScrollContainerBy  
 Wywołanie `ScrollContainerBy` funkcji członkowskiej przewijanie kontenerem o wartość w pikselach, wskazane przez `sizeScroll`.  
  
```  
BOOL ScrollContainerBy(CSize sizeScroll);
```  
  
### <a name="parameters"></a>Parametry  
 `sizeScroll`  
 Wskazuje, jak daleko jest kontenerem do przewijania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Wskazuje liczbę wartości dodatnich przewijania w dół i w prawo; wartości ujemne wskazują przewijania w górę i w lewo.  
  
##  <a name="updateallitems"></a>COleServerDoc::UpdateAllItems  
 Wywołanie tej funkcji, aby powiadomić wszystkich połączonych elementów podłączone do dokumentu, że dokument został zmieniony.  
  
```  
void UpdateAllItems(
    COleServerItem* pSender,  
    LPARAM lHint = 0L,  
    CObject* pHint = NULL,  
    DVASPECT nDrawAspect = DVASPECT_CONTENT);
```  
  
### <a name="parameters"></a>Parametry  
 `pSender`  
 Wskaźnik do elementu, który zmodyfikował dokument, lub **NULL** w przypadku wszystkich elementów do zaktualizowania.  
  
 `lHint`  
 Zawiera informacje dotyczące zmiany.  
  
 `pHint`  
 Wskaźnik do przechowywania informacji na temat modyfikacji obiektu.  
  
 `nDrawAspect`  
 Określa, jak element ma być rysowany. Jest to wartość z zakresu od `DVASPECT` wyliczenia. Ten parametr może mieć jedną z następujących wartości:  
  
- `DVASPECT_CONTENT`Element jest reprezentowana w taki sposób, że mogą być wyświetlane jako osadzonego wewnątrz jej kontenera.  
  
- `DVASPECT_THUMBNAIL`Element jest renderowany w reprezentacji "miniatur", aby mogły być wyświetlone w narzędziu do przeglądania.  
  
- `DVASPECT_ICON`Element jest reprezentowany przez ikonę.  
  
- `DVASPECT_DOCPRINT`Element jest wyświetlana tak, jakby były drukowane, za pomocą polecenia Drukuj z menu Plik.  
  
### <a name="remarks"></a>Uwagi  
 Po użytkownik zmieni dokument serwera zazwyczaj wywołanie tej funkcji. Jeśli element OLE jest połączony z dokumentu przy użyciu automatycznego link, aby odzwierciedlić zmiany zaktualizowaniem elementu. W aplikacjach kontenera napisane na platformie Microsoft Foundation Class Library [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) funkcji członkowskiej klasy `COleClientItem` jest wywoływana.  
  
 Ta funkcja wymaga `OnUpdate` funkcji członkowskiej dla każdego dokumentu elementy oprócz wysyłania elementu, przekazywanie `pHint`, `lHint`, i `nDrawAspect`. Użyj tych parametrów do przekazywania informacji do elementów o zmiany wprowadzone w dokumencie. Może zakodować informacje przy użyciu `lHint` lub zdefiniować `CObject`-klasy do przechowywania informacji na temat zmian i przekazać tej klasy przy użyciu obiektu `pHint`. Zastąpienie `OnUpdate` funkcji członkowskiej w Twojej `COleServerItem`-klasy w celu zoptymalizowania aktualizacja poszczególnych elementów w zależności od tego, czy zmienił jego prezentacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC HIERSVR](../../visual-cpp-samples.md)   
 [Klasa COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa COleDocument](../../mfc/reference/coledocument-class.md)   
 [Klasa COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)   
 [Klasa COleTemplateServer](../../mfc/reference/coletemplateserver-class.md)
