---
title: Klasa COleServerItem | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4d3165a11aace54ce2062a6321acc7f911fbdc39
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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
|[COleServerItem::COleServerItem](#coleserveritem)|Konstruuje `COleServerItem` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleServerItem::AddOtherClipboardData](#addotherclipboarddata)|Umieszcza formatów prezentacji i konwersji w `COleDataSource` obiektu.|  
|[COleServerItem::CopyToClipboard](#copytoclipboard)|Kopiuje element do Schowka.|  
|[COleServerItem::DoDragDrop](#dodragdrop)|Wykonuje operację przeciągania i upuszczania.|  
|[COleServerItem::GetClipboardData](#getclipboarddata)|Pobiera źródło danych do użycia w transfer danych (przeciągania i upuszczania lub Schowka).|  
|[COleServerItem::GetDocument](#getdocument)|Zwraca dokument serwera, który zawiera element.|  
|[COleServerItem::GetEmbedSourceData](#getembedsourcedata)|Pobiera **CF_EMBEDSOURCE** dane dla elementu OLE.|  
|[COleServerItem::GetItemName](#getitemname)|Zwraca nazwę elementu. Używany tylko połączone elementy.|  
|[COleServerItem::GetLinkSourceData](#getlinksourcedata)|Pobiera `CF_LINKSOURCE` dane dla elementu OLE.|  
|[COleServerItem::GetObjectDescriptorData](#getobjectdescriptordata)|Pobiera **CF_OBJECTDESCRIPTOR** dane dla elementu OLE.|  
|[COleServerItem::IsConnected](#isconnected)|Wskazuje, czy element jest obecnie dołączony do kontenera usługi active.|  
|[COleServerItem::IsLinkedItem](#islinkeditem)|Wskazuje, czy element reprezentuje połączonego elementu OLE.|  
|[COleServerItem::NotifyChanged](#notifychanged)|Aktualizuje wszystkie kontenery z aktualizacji automatycznych łącza.|  
|[COleServerItem::OnDoVerb](#ondoverb)|Wywołuje się, by wykonać zlecenia.|  
|[COleServerItem::OnDraw](#ondraw)|Wywoływane, gdy kontener żąda do rysowania elementu; Implementacja wymagane.|  
|[COleServerItem::OnDrawEx](#ondrawex)|Wywołuje się do rysowania elementu specjalne.|  
|[COleServerItem::OnGetClipboardData](#ongetclipboarddata)|Wywoływane przez platformę, by pobrać dane, które byłyby skopiowane do Schowka.|  
|[COleServerItem::OnGetExtent](#ongetextent)|Wywoływane przez platformę, by pobrać rozmiar elementu OLE.|  
|[COleServerItem::OnInitFromData](#oninitfromdata)|Wywoływane przez platformę, by zainicjować element OLE przy użyciu zawartość określony obiekt transferu danych.|  
|[COleServerItem::OnQueryUpdateItems](#onqueryupdateitems)|Wywoływane w celu określenia, czy wszystkie połączone elementy wymagają aktualizacji.|  
|[COleServerItem::OnRenderData](#onrenderdata)|Pobiera dane jako część opóźnione renderowanie.|  
|[COleServerItem::OnRenderFileData](#onrenderfiledata)|Pobiera dane do `CFile` obiektu jako część opóźnione renderowanie.|  
|[COleServerItem::OnRenderGlobalData](#onrenderglobaldata)|Pobiera dane do `HGLOBAL` jako część opóźnione renderowanie.|  
|[COleServerItem::OnSetColorScheme](#onsetcolorscheme)|Wywołuje się, by ustawić elementu schematu kolorów.|  
|[COleServerItem::OnSetData](#onsetdata)|Wywołuje się, by ustawić elementu danych.|  
|[COleServerItem::OnSetExtent](#onsetextent)|Wywoływane przez platformę, by ustawić rozmiar elementu OLE.|  
|[COleServerItem::OnUpdate](#onupdate)|Wywołuje się, gdy niektórych części dokumentu element należy do zostanie zmieniona.|  
|[COleServerItem::OnUpdateItems](#onupdateitems)|Wywoływane w celu aktualizacji pamięci podręcznej prezentacji wszystkich elementów w dokumencie serwera.|  
|[COleServerItem::SetItemName](#setitemname)|Ustawia nazwę elementu. Używany tylko połączone elementy.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleServerItem::GetDataSource](#getdatasource)|Pobiera obiekt używany do przechowywania formatów konwersji.|  
|[COleServerItem::OnHide](#onhide)|Wywoływane przez platformę, by ukryć element OLE.|  
|[COleServerItem::OnOpen](#onopen)|Wywoływane przez platformę, by wyświetlić element OLE w osobnym oknie najwyższego poziomu.|  
|[COleServerItem::OnShow](#onshow)|Wywoływane, gdy kontener żąda do wyświetlenia elementu.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleServerItem::m_sizeExtent](#m_sizeextent)|Informuje serwer o tym, jaka część elementu OLE jest widoczny.|  
  
## <a name="remarks"></a>Uwagi  
 Połączony element może reprezentować niektórych lub wszystkich dokumentów serwera. Element osadzony zawsze stanowi dokument całego serwera.  
  
 `COleServerItem` Klasa definiuje kilka funkcji Członkowskich możliwym do zastąpienia, które są wywoływane przez OLE systemu dołączanych dynamicznie bibliotekach (dll), zwykle w odpowiedzi na żądania z aplikacji kontenera. Te funkcje Członkowskie Zezwalaj aplikacji kontenera do manipulowania elementem pośrednio na różne sposoby, takie jak wyświetlanie, wykonywanie jej zleceń lub pobiera dane w różnych formatach.  
  
 Aby użyć `COleServerItem`, pochodną klasy i wykonywania [OnDraw](#ondraw) i [serializacja](../../mfc/reference/cobject-class.md#serialize) funkcji elementów członkowskich. `OnDraw` Funkcja udostępnia reprezentację metaplik elementu, dzięki któremu będzie wyświetlana po aplikacji kontenera otwiera złożonego dokumentu. `Serialize` Funkcji `CObject` zawiera natywny reprezentacja elementu, co element osadzony do przeniesienia między aplikacje kontenera i serwera. [OnGetExtent](#ongetextent) zawiera fizyczne rozmiar elementu w kontenerze, włączanie kontener, aby rozmiar elementu.  
  
 Aby uzyskać więcej informacji na temat serwerów i materiały pokrewne, zobacz artykuł [serwery: Implementowanie serwera](../../mfc/servers-implementing-a-server.md) oraz "Tworzenie kontenera/serwera aplikacji" w artykule [kontenery: funkcje zaawansowane](../../mfc/containers-advanced-features.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocItem](../../mfc/reference/cdocitem-class.md)  
  
 `COleServerItem`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxole.h  
  
##  <a name="addotherclipboarddata"></a>  COleServerItem::AddOtherClipboardData  
 Wywołanie tej funkcji można umieścić formatów prezentacji i konwersji elementu OLE w określonym `COleDataSource` obiektu.  
  
```  
void AddOtherClipboardData(COleDataSource* pDataSource);
```  
  
### <a name="parameters"></a>Parametry  
 `pDataSource`  
 Wskaźnik do `COleDataSource` obiekt, w której ma zostać umieszczony danych.  
  
### <a name="remarks"></a>Uwagi  
 Zostały zaimplementowane [OnDraw](#ondraw) element członkowski funkcji format prezentacji (obraz metaplik) dla elementu. Do obsługi innych formatach konwersji, zarejestruj je przy użyciu [COleDataSource](../../mfc/reference/coledatasource-class.md) obiektu zwróconego przez [GetDataSource](#getdatasource) i zastąpić [OnRenderData](#onrenderdata) funkcji Członkowskich Podaj dane w formatach, które mają być obsługiwane.  
  
##  <a name="coleserveritem"></a>  COleServerItem::COleServerItem  
 Konstruuje `COleServerItem` obiektu i dodaje go do dokumentu serwera kolekcję elementów dokumentu.  
  
```  
COleServerItem(
    COleServerDoc* pServerDoc,  
    BOOL bAutoDelete);
```  
  
### <a name="parameters"></a>Parametry  
 `pServerDoc`  
 Wskaźnik do dokumentu, który będzie zawierać nowy element.  
  
 `bAutoDelete`  
 Flaga wskazująca, czy obiekt może zostać usunięta, gdy do niej łącza zostanie zwolniony. Ustaw tę wartość na **FALSE** Jeśli `COleServerItem` obiekt jest integralną częścią danych dokumentu, który należy usunąć. Ustaw tę wartość na **TRUE** Jeśli obiekt jest strukturą dodatkowej używany do identyfikowania zakresu w danych dokumentu, który może zostać usunięta przez platformę.  
  
##  <a name="copytoclipboard"></a>  COleServerItem::CopyToClipboard  
 Wywołanie tej funkcji można skopiować elementu OLE do Schowka.  
  
```  
void CopyToClipboard(BOOL bIncludeLink = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 `bIncludeLink`  
 Ustaw tę wartość na **TRUE** Jeśli łączenie danych powinien zostać skopiowany do Schowka. Ustaw tę wartość na **FALSE** Jeśli aplikacja serwera nie obsługuje łącza.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja używa [OnGetClipboardData](#ongetclipboarddata) funkcji członkowskiej, aby utworzyć [COleDataSource](../../mfc/reference/coledatasource-class.md) obiekt zawierający dane elementu OLE w formatach obsługiwane. Funkcja umieszcza `COleDataSource` obiektu w Schowku przy użyciu [COleDataSource::SetClipboard](../../mfc/reference/coledatasource-class.md#setclipboard) funkcji. `COleDataSource` Obiekt zawiera elementu danych natywnych i jego reprezentacja w `CF_METAFILEPICT` format, a także dane w wszystkie możesz zdecydować się na brak obsługi formatu konwersji. Zostały zaimplementowane [serializacja](../../mfc/reference/cobject-class.md#serialize) i [OnDraw](#ondraw) działa ten element członkowski.  
  
##  <a name="dodragdrop"></a>  COleServerItem::DoDragDrop  
 Wywołanie `DoDragDrop` funkcji członkowskiej do wykonania operacji przeciągania i upuszczania.  
  
```  
DROPEFFECT DoDragDrop(
    LPCRECT lpRectItem,  
    CPoint ptOffset,  
    BOOL bIncludeLink = FALSE,  
    DWORD dwEffects = DROPEFFECT_COPY | DROPEFFECT_MOVE,  
    LPCRECT lpRectStartDrag = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *lpRectItem*  
 Prostokąt elementu na ekranie w pikselach względem obszaru klienckiego.  
  
 `ptOffset`  
 Przesunięcie od `lpItemRect` gdzie został położenia kursora myszy podczas przeciągania.  
  
 `bIncludeLink`  
 Ustaw tę wartość na **TRUE** Jeśli łączenie danych powinien zostać skopiowany do Schowka. Ustaw ją na **FALSE** Jeśli aplikacja nie obsługuje łącza.  
  
 `dwEffects`  
 Określa efekty, których źródła przeciągania umożliwi w operacji przeciągania (kombinacja kopiowania, przenoszenie i łącza).  
  
 `lpRectStartDrag`  
 Wskaźnik do prostokąt, który określa, gdzie faktycznie uruchamia przeciągania. Aby uzyskać więcej informacji zobacz następujące sekcji uwag.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość z zakresu od `DROPEFFECT` wyliczenia. Jeśli jest `DROPEFFECT_MOVE`, powinna zostać usunięta oryginalnych danych.  
  
### <a name="remarks"></a>Uwagi  
 Operacja przeciągania i upuszczania nie rozpoczyna się natychmiast. Oczekuje, aż wskaźnik myszy opuści prostokąt określony przez `lpRectStartDrag` lub dopóki nie upłynie określoną liczbę milisekund. Jeśli `lpRectStartDrag` jest **NULL**, prostokąt domyślnej jest używana co przeciągania rozpoczyna się, gdy wskaźnik myszy przesuwa jeden piksel.  
  
 Czas opóźnienia jest określany przez ustawienie klucza rejestru. Można zmienić czas opóźnienia, wywołując [CWinApp::WriteProfileString](../../mfc/reference/cwinapp-class.md#writeprofilestring) lub [CWinApp::WriteProfileInt](../../mfc/reference/cwinapp-class.md#writeprofileint). Jeśli nie określisz czas opóźnienia, jest używana wartość domyślna 200 ms. Czas opóźnienia przeciągania są przechowywane w następujący sposób:  
  
-   Czas opóźnienia przeciągania systemu Windows NT jest przechowywany w HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\NT\CurrentVersion\IniFileMapping\win.ini\Windows\DragDelay.  
  
-   Czas opóźnienia przeciągania 3.x systemu Windows są przechowywane w Windows. Plik INI sekcji [Windows}.  
  
-   Czas opóźnienia przeciągania Windows 95/98 są przechowywane w pamięci podręcznej wersji systemu Windows. INI.  
  
 Dla przeciągnij więcej informacji na temat opóźnienie informacje są przechowywane w rejestrze albo lub. Plik INI, zobacz [WriteProfileString](http://msdn.microsoft.com/library/windows/desktop/ms725504) w zestawie Windows SDK.  
  
##  <a name="getclipboarddata"></a>  COleServerItem::GetClipboardData  
 Wywołanie tej funkcji, aby wypełnić określonego [COleDataSource](../../mfc/reference/coledatasource-class.md) obiektu z danymi, które byłyby skopiowane do Schowka, jeśli wywołujesz [CopyToClipboard](#copytoclipboard) (również będzie można przesłać tych samych danych, jeśli użytkownik wywołuje się [dodragdrop —](#dodragdrop)).  
  
```  
void GetClipboardData(
    COleDataSource* pDataSource,  
    BOOL bIncludeLink = FALSE,  
    LPPOINT lpOffset = NULL,  
    LPSIZE lpSize = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pDataSource`  
 Wskaźnik do `COleDataSource` obiekt, który będzie odbierać dane elementu OLE w wszystkich obsługiwanych formatów.  
  
 `bIncludeLink`  
 **Wartość TRUE,** Jeśli łączenie danych powinien zostać skopiowany do Schowka. **FALSE** Jeśli aplikacja serwera nie obsługuje łącza.  
  
 `lpOffset`  
 Przesunięcie w pikselach kursora myszy ze źródła obiektu.  
  
 `lpSize`  
 Rozmiar obiektu w pikselach.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja wymaga [GetEmbedSourceData](#getembedsourcedata) funkcji członkowskiej można uzyskać danych natywnych element OLE i wywołania [AddOtherClipboardData](#addotherclipboarddata) funkcji członkowskiej, aby uzyskać format prezentacji i wszystkie obsługiwane formaty konwersji. Jeśli `bIncludeLink` jest **TRUE**, również wywołuje funkcję [GetLinkSourceData](#getlinksourcedata) można pobrać danych łącze dla elementu.  
  
 Zastąpienie tej funkcji, jeśli chcesz umieścić formatach `COleDataSource` obiektu przed lub po tych formatów dostarczonych przez `CopyToClipboard`.  
  
##  <a name="getdatasource"></a>  COleServerItem::GetDataSource  
 Wywołanie tej funkcji, aby uzyskać [COleDataSource](../../mfc/reference/coledatasource-class.md) obiekt używany do przechowywania formatów konwersji, które obsługuje aplikacji serwera.  
  
```  
COleDataSource* GetDataSource();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `COleDataSource` obiekt używany do przechowywania formatów konwersji.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli chcesz, aby aplikacja serwera oferowanie danych w różnych formatach podczas transferu danych operacji, zarejestruj te formaty z `COleDataSource` obiektu zwróconego przez tę funkcję. Na przykład, jeśli chcesz udostępnić **CF_TEXT** reprezentacja elementu OLE do Schowka lub operacji przeciągania i upuszczania, czy zarejestrować formatu z `COleDataSource` ta funkcja zwraca obiekt, a następnie zastąpienie  **OnRenderXxxData** funkcji Członkowskich danych.  
  
##  <a name="getdocument"></a>  COleServerItem::GetDocument  
 Wywołanie tej funkcji, otrzymywać wskaźnik do dokumentu, który zawiera element.  
  
```  
COleServerDoc* GetDocument() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do dokumentu, który zawiera element; **NULL** Jeśli element nie jest częścią dokumentu.  
  
### <a name="remarks"></a>Uwagi  
 Dzięki temu dostęp do dokumentu serwera, który został przekazany jako argument `COleServerItem` konstruktora.  
  
##  <a name="getembedsourcedata"></a>  COleServerItem::GetEmbedSourceData  
 Wywołanie tej funkcji, aby uzyskać **CF_EMBEDSOURCE** dane dla elementu OLE.  
  
```  
void GetEmbedSourceData(LPSTGMEDIUM lpStgMedium);
```  
  
### <a name="parameters"></a>Parametry  
 `lpStgMedium`  
 Wskaźnik do [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) struktury, która odbierze **CF_EMBEDSOURCE** danych dla elementu OLE.  
  
### <a name="remarks"></a>Uwagi  
 Ten format obejmuje elementu danych natywnych. Zostały zaimplementowane `Serialize` funkcji członkowskiej ten nie działa prawidłowo.  
  
 Następnie można dodać wynik ze źródłem danych przy użyciu [COleDataSource::CacheData](../../mfc/reference/coledatasource-class.md#cachedata). Ta funkcja jest wywoływana automatycznie przez [COleServerItem::OnGetClipboardData](#ongetclipboarddata).  
  
 Aby uzyskać więcej informacji, zobacz [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) w zestawie Windows SDK.  
  
##  <a name="getitemname"></a>  COleServerItem::GetItemName  
 Wywołanie tej funkcji można pobrać nazwy elementu.  
  
```  
const CString& GetItemName() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Nazwa elementu.  
  
### <a name="remarks"></a>Uwagi  
 Tylko w przypadku połączone elementy są zazwyczaj wywołanie tej funkcji.  
  
##  <a name="getlinksourcedata"></a>  COleServerItem::GetLinkSourceData  
 Wywołanie tej funkcji, aby uzyskać `CF_LINKSOURCE` dane dla elementu OLE.  
  
```  
BOOL GetLinkSourceData(LPSTGMEDIUM lpStgMedium);
```  
  
### <a name="parameters"></a>Parametry  
 `lpStgMedium`  
 Wskaźnik do [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) struktury, która odbierze `CF_LINKSOURCE` danych dla elementu OLE.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Format ten zawiera identyfikator CLSID opisujące typ elementu OLE i informacje potrzebne do zlokalizowania dokumentu zawierającego element OLE.  
  
 Następnie można dodać wynik do źródła danych z [COleDataSource::CacheData](../../mfc/reference/coledatasource-class.md#cachedata). Ta funkcja jest wywoływana automatycznie przez [OnGetClipboardData](#ongetclipboarddata).  
  
 Aby uzyskać więcej informacji, zobacz [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) w zestawie Windows SDK.  
  
##  <a name="getobjectdescriptordata"></a>  COleServerItem::GetObjectDescriptorData  
 Wywołanie tej funkcji, aby uzyskać **CF_OBJECTDESCRIPTOR** dane dla elementu OLE.  
  
```  
void GetObjectDescriptorData(
    LPPOINT lpOffset,  
    LPSIZE lpSize,  
    LPSTGMEDIUM lpStgMedium);
```  
  
### <a name="parameters"></a>Parametry  
 `lpOffset`  
 Przesunięcie kursora myszy, kliknij pozycję od lewego górnego rogu elementu OLE. Może być **NULL**.  
  
 `lpSize`  
 Rozmiar elementu OLE. Może być **NULL**.  
  
 `lpStgMedium`  
 Wskaźnik do [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) struktury, która odbierze **CF_OBJECTDESCRIPTOR** danych dla elementu OLE.  
  
### <a name="remarks"></a>Uwagi  
 Informacje są kopiowane do **STGMEDIUM** wskazywanej przez `lpStgMedium`. Ten format zawiera informacje potrzebne do okna dialogowego Wklej specjalne.  
  
 Aby uzyskać więcej informacji, zobacz [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) w zestawie Windows SDK.  
  
##  <a name="isconnected"></a>  COleServerItem::IsConnected  
 Wywołanie tej funkcji, jeśli element OLE jest podłączony.  
  
```  
BOOL IsConnected() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli element jest połączony; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Element OLE jest traktowany jako podłączone, jeśli co najmniej jeden kontenery odwołują się do elementu. Element jest połączony, jeśli jego odwołania jest większa niż 0 lub jest element osadzony.  
  
##  <a name="islinkeditem"></a>  COleServerItem::IsLinkedItem  
 Wywołanie tej funkcji, aby sprawdzić, czy element OLE jest połączony element.  
  
```  
BOOL IsLinkedItem() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli element jest połączony element; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Element jest połączony, jeśli element jest prawidłowy i nie są zwracane w liście dokumentu elementy osadzone. Połączony element może być lub może nie być połączony z kontenerem.  
  
 Jest często, aby użyć tej samej klasy dla elementów połączonych i osadzonych. `IsLinkedItem` Umożliwia zapewnienie połączone elementy będą działały inaczej niż elementy osadzone, mimo że wiele razy kod jest wspólnej.  
  
##  <a name="m_sizeextent"></a>  COleServerItem::m_sizeExtent  
 Ten element członkowski informuje serwer, jaka część obiektu jest widoczny w dokumencie kontenera.  
  
```  
CSize m_sizeExtent;  
```  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja [OnSetExtent](#onsetextent) ustawia tego elementu członkowskiego.  
  
##  <a name="notifychanged"></a>  COleServerItem::NotifyChanged  
 Wywołanie tej funkcji po połączony element został zmieniony.  
  
```  
void NotifyChanged(DVASPECT nDrawAspect = DVASPECT_CONTENT);
```  
  
### <a name="parameters"></a>Parametry  
 `nDrawAspect`  
 Wartość z zakresu od `DVASPECT` wyliczenia, która wskazuje, które aspekt elementu OLE została zmieniona. Ten parametr może mieć jedną z następujących wartości:  
  
- `DVASPECT_CONTENT` Element jest reprezentowana w taki sposób, że mogą być wyświetlane jako osadzonego wewnątrz jej kontenera.  
  
- `DVASPECT_THUMBNAIL` Element jest renderowany w reprezentacji "miniatur", aby mogły być wyświetlone w narzędziu do przeglądania.  
  
- `DVASPECT_ICON` Element jest reprezentowany przez ikonę.  
  
- `DVASPECT_DOCPRINT` Element jest wyświetlana tak, jakby były drukowane, za pomocą polecenia Drukuj z menu Plik.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli element kontenera jest połączony z dokumentu przy użyciu automatycznego link, aby odzwierciedlić zmiany zaktualizowaniem elementu. W kontenerze aplikacje napisane przy użyciu Microsoft Foundation Class Library [COleClientItem::OnChange](../../mfc/reference/coleclientitem-class.md#onchange) jest wywoływana w odpowiedzi.  
  
##  <a name="ondoverb"></a>  COleServerItem::OnDoVerb  
 Wywoływane przez platformę, by wykonać określone zlecenie.  
  
```  
virtual void OnDoVerb(LONG iVerb);
```  
  
### <a name="parameters"></a>Parametry  
 `iVerb`  
 Określa zlecenie do wykonania. Może być jeden z następujących czynności:  
  
|Wartość|Znaczenie|Symbol|  
|-----------|-------------|------------|  
|0|Primary — Zlecenie|`OLEIVERB_PRIMARY`|  
|1|Zlecenie dodatkowej|(Brak)|  
|- 1|Wyświetlanego elementu do edycji|`OLEIVERB_SHOW`|  
|- 2|Edytuj element w oddzielnym oknie|`OLEIVERB_OPEN`|  
|- 3|Ukrywanie elementów|`OLEIVERB_HIDE`|  
  
 Wartość-1 jest zwykle alias dla innego zlecenia. Jeśli otwarty edytowanie nie jest obsługiwane, -2 ma ten sam efekt co -1. Aby uzyskać dodatkowe wartości, zobacz [IOleObject::DoVerb](http://msdn.microsoft.com/library/windows/desktop/ms694508) w zestawie Windows SDK.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli aplikacja kontenera zostało zapisane z Microsoft Foundation Class Library, ta funkcja jest wywoływana podczas [COleClientItem::Activate](../../mfc/reference/coleclientitem-class.md#activate) funkcji członkowskiej odpowiadającego `COleClientItem` nosi nazwę obiektu. Domyślna implementacja wywołuje [metodzie OnShow](#onshow) funkcji członkowskiej, jeśli podstawowy zlecenie lub `OLEIVERB_SHOW` jest określony, [zdarzenia](#onopen) Jeśli pomocniczego verb lub `OLEIVERB_OPEN` jest określona i [OnHide](#onhide) Jeśli `OLEIVERB_HIDE` jest określona. Domyślna implementacja wywołuje `OnShow` Jeśli `iVerb` nie jest jednym z zleceń wymienionych powyżej.  
  
 Jeśli Twoje primary — zlecenie nie występuje element, należy przesłonić tę funkcję. Na przykład jeśli element jest nagrywanie dźwięku i jego primary — zlecenie jest Play, czy jest do wyświetlenia aplikacji serwera, aby odtworzyć element.  
  
 Aby uzyskać więcej informacji, zobacz [IOleObject::DoVerb](http://msdn.microsoft.com/library/windows/desktop/ms694508) w zestawie Windows SDK.  
  
##  <a name="ondraw"></a>  COleServerItem::OnDraw  
 Wywoływane przez platformę, by renderować element OLE w metaplik.  
  
```  
virtual BOOL OnDraw(
    CDC* pDC,  
    CSize& rSize) = 0;  
```  
  
### <a name="parameters"></a>Parametry  
 `pDC`  
 Wskaźnik do [CDC](../../mfc/reference/cdc-class.md) obiektu, na którym ma zostać narysowany element. Kontekst wyświetlania jest automatycznie połączony kontekst wyświetlania atrybutów więc można wywołać funkcji atrybutu, mimo że spowoduje to spowodowałoby metaplik specyficzne dla urządzenia.  
  
 `rSize`  
 Rozmiar w **HIMETRIC** jednostki, w którym ma zostać narysowany metaplik.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli element został pomyślnie rysowane; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Reprezentacja elementu OLE metaplik jest używana do wyświetlania elementu w kontenerze aplikacji. Jeśli aplikacja kontenera zostało zapisane z Microsoft Foundation Class Library, metaplik jest używany przez [rysowania](../../mfc/reference/coleclientitem-class.md#draw) funkcji członkowskiej odpowiadającego [COleClientItem](../../mfc/reference/coleclientitem-class.md) obiektu. Brak implementacji domyślnej. Konieczne jest przesłonięcie tej funkcji do rysowania elementu do kontekstu urządzenia określone.  
  
##  <a name="ondrawex"></a>  COleServerItem::OnDrawEx  
 Wywoływane przez platformę dla wszystkich rysunku.  
  
```  
virtual BOOL OnDrawEx(
    CDC* pDC,  
    DVASPECT nDrawAspect,  
    CSize& rSize);
```  
  
### <a name="parameters"></a>Parametry  
 `pDC`  
 Wskaźnik do [CDC](../../mfc/reference/cdc-class.md) obiektu, na którym ma zostać narysowany element. Kontroler domeny jest automatycznie połączony z atrybutu kontrolera domeny, można wywołać funkcji atrybutu mimo że spowoduje to spowodowałoby metaplik specyficzne dla urządzenia.  
  
 `nDrawAspect`  
 Wartość z zakresu od `DVASPECT` wyliczenia. Ten parametr może mieć jedną z następujących wartości:  
  
- `DVASPECT_CONTENT` Element jest reprezentowana w taki sposób, że mogą być wyświetlane jako osadzonego wewnątrz jej kontenera.  
  
- `DVASPECT_THUMBNAIL` Element jest renderowany w reprezentacji "miniatur", aby mogły być wyświetlone w narzędziu do przeglądania.  
  
- `DVASPECT_ICON` Element jest reprezentowany przez ikonę.  
  
- `DVASPECT_DOCPRINT` Element jest wyświetlana tak, jakby były drukowane, za pomocą polecenia Drukuj z menu Plik.  
  
 `rSize`  
 Rozmiar elementu w **HIMETRIC** jednostki.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli element został pomyślnie rysowane; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja wywołuje `OnDraw` podczas `DVASPECT` jest równa `DVASPECT_CONTENT`; w przeciwnym razie nie powiedzie się.  
  
 Zastąpienie tej funkcji prezentacji danych dla elementów innych niż `DVASPECT_CONTENT`, takich jak `DVASPECT_ICON` lub `DVASPECT_THUMBNAIL`.  
  
##  <a name="ongetclipboarddata"></a>  COleServerItem::OnGetClipboardData  
 Wywoływane przez platformę, by pobrać `COleDataSource` obiekt zawierający dane, które będą umieszczone w Schowku przez wywołanie do [CopyToClipboard](#copytoclipboard) funkcję elementu członkowskiego.  
  
```  
virtual COleDataSource* OnGetClipboardData(
    BOOL bIncludeLink,  
    LPPOINT lpOffset,  
    LPSIZE lpSize);
```  
  
### <a name="parameters"></a>Parametry  
 `bIncludeLink`  
 Ustaw tę wartość na **TRUE** Jeśli łączenie danych powinien zostać skopiowany do Schowka. Ustaw tę wartość na **FALSE** Jeśli aplikacja serwera nie obsługuje łącza.  
  
 `lpOffset`  
 Przesunięcie kursora myszy ze źródła obiektu w pikselach.  
  
 `lpSize`  
 Rozmiar obiektu w pikselach.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do [COleDataSource](../../mfc/reference/coledatasource-class.md) obiektu zawierającego dane do Schowka.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja ta funkcja wymaga [GetClipboardData](#getclipboarddata).  
  
##  <a name="ongetextent"></a>  COleServerItem::OnGetExtent  
 Wywoływane przez platformę, by pobrać rozmiar w **HIMETRIC** jednostki elementu OLE.  
  
```  
virtual BOOL OnGetExtent(
    DVASPECT nDrawAspect,  
    CSize& rSize);
```  
  
### <a name="parameters"></a>Parametry  
 `nDrawAspect`  
 Określa aspekt element OLE granic, których mają zostać pobrane. Ten parametr może mieć jedną z następujących wartości:  
  
- `DVASPECT_CONTENT` Element jest reprezentowana w taki sposób, że mogą być wyświetlane jako osadzonego wewnątrz jej kontenera.  
  
- `DVASPECT_THUMBNAIL` Element jest renderowany w reprezentacji "miniatur", aby mogły być wyświetlone w narzędziu do przeglądania.  
  
- `DVASPECT_ICON` Element jest reprezentowany przez ikonę.  
  
- `DVASPECT_DOCPRINT` Element jest wyświetlana tak, jakby były drukowane, za pomocą polecenia Drukuj z menu Plik.  
  
 `rSize`  
 Odwołanie do `CSize` obiekt, który zostanie wyświetlony rozmiar elementu OLE.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli aplikacja kontenera zostało zapisane z Microsoft Foundation Class Library, ta funkcja jest wywoływana podczas [GetExtent](../../mfc/reference/coleclientitem-class.md#getextent) funkcji członkowskiej odpowiadającego `COleClientItem` nosi nazwę obiektu. Domyślna implementacja nie działa. Musisz zaimplementować ją samodzielnie. Należy przesłonić tę funkcję, jeśli chcesz wykonać specjalnego przetwarzania, podczas przetwarzania żądania rozmiar elementu OLE.  
  
##  <a name="onhide"></a>  COleServerItem::OnHide  
 Wywoływane przez platformę, by ukryć element OLE.  
  
```  
virtual void OnHide();
```  
  
### <a name="remarks"></a>Uwagi  
 Wywołuje domyślną **COleServerDoc::OnShowDocument (FALSE)**. Funkcja powiadamia również kontenera został ukryty element OLE. Należy przesłonić tę funkcję, jeśli chcesz wykonać specjalnego przetwarzania, jeśli ukrycie elementu OLE.  
  
##  <a name="oninitfromdata"></a>  COleServerItem::OnInitFromData  
 Wywoływane przez platformę, by zainicjować element OLE przy użyciu zawartość `pDataObject`.  
  
```  
virtual BOOL OnInitFromData(
    COleDataObject* pDataObject,  
    BOOL bCreation);
```  
  
### <a name="parameters"></a>Parametry  
 `pDataObject`  
 Wskaźnik do obiektu danych OLE zawierający dane w różnych formatach zainicjować element OLE.  
  
 `bCreation`  
 **Wartość TRUE,** Jeśli funkcja jest wywoływana zainicjować element OLE nowo tworzone przez aplikacji kontenera. **FALSE** Jeśli funkcja jest wywoływana, aby zastąpić zawartość już istniejący element OLE.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `bCreation` jest **TRUE**, ta funkcja jest wywoływana, gdy kontener implementuje wstawić nowego obiektu na podstawie bieżącego zaznaczenia. Wybranych danych jest używany podczas tworzenia nowego elementu OLE. Na przykład, gdy zaznaczenie zakresu komórek w arkusza kalkulacyjnego, a następnie utworzyć wykres przy użyciu Wstaw nowy obiekt na podstawie wartości w wybranym zakresie. Domyślna implementacja nie działa. Przesłonić tę funkcję, aby wybrać dozwolonego formatu z oferowanych przez `pDataObject` i zainicjować element OLE na podstawie danych podany. Jest to zaawansowane możliwym do zastąpienia.  
  
 Aby uzyskać więcej informacji, zobacz [IOleObject::InitFromData](http://msdn.microsoft.com/library/windows/desktop/ms688510) w zestawie Windows SDK.  
  
##  <a name="onopen"></a>  COleServerItem::OnOpen  
 Wywoływane przez platformę, by wyświetlić element OLE w oddzielnym wystąpieniu aplikacji serwera, a nie w miejscu.  
  
```  
virtual void OnOpen();
```  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja aktywuje pierwsze okno ramowe wyświetlania dokumentu, który zawiera element OLE; Jeśli aplikacja jest mini serwer, domyślna implementacja Pokazuje okno główne. Funkcja powiadamia również kontenera otwarciu elementu OLE.  
  
 Należy przesłonić tę funkcję, jeśli chcesz wykonać specjalnego przetwarzania, podczas otwierania elementu OLE. Jest to szczególnie powszechne z połączonych elementów, które chcesz ustawić zaznaczenie łącza, gdy jest otwarty.  
  
 Aby uzyskać więcej informacji, zobacz [IOleClientSite::OnShowWindow](http://msdn.microsoft.com/library/windows/desktop/ms688658) w zestawie Windows SDK.  
  
##  <a name="onqueryupdateitems"></a>  COleServerItem::OnQueryUpdateItems  
 Wywoływane przez platformę, by określić, czy którykolwiek z elementów powiązanych w bieżącym dokumencie serwera są nieaktualne.  
  
```  
virtual BOOL OnQueryUpdateItems();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli dokument ma elementy wymagające aktualizacji; 0, jeśli wszystkie elementy są aktualne.  
  
### <a name="remarks"></a>Uwagi  
 Element jest nieaktualny, jeśli jego dokumentu źródłowego został zmieniony, ale połączony element nie został jeszcze zaktualizowany w celu odzwierciedlenia zmian w dokumencie.  
  
##  <a name="onrenderdata"></a>  COleServerItem::OnRenderData  
 Wywoływane przez platformę, by pobrać dane w określonym formacie.  
  
```  
virtual BOOL OnRenderData(
    LPFORMATETC lpFormatEtc,  
    LPSTGMEDIUM lpStgMedium);
```  
  
### <a name="parameters"></a>Parametry  
 `lpFormatEtc`  
 Wskazuje [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktury, określając format, w którym jest wymagane informacje.  
  
 `lpStgMedium`  
 Wskazuje [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) struktury, w którym ma zostać zwrócone dane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Określony format jest jednym wcześniej umieszczone w `COleDataSource` przy użyciu [DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata) lub [DelayRenderFileData](../../mfc/reference/coledatasource-class.md#delayrenderfiledata) funkcji członkowskiej do renderowania opóźnione. Domyślna implementacja ta funkcja wymaga [OnRenderFileData](#onrenderfiledata) lub [OnRenderGlobalData](#onrenderglobaldata), jeśli podany nośnik jest pliku lub pamięci. Jeśli żadna z tych formatów podano Domyślna implementacja zwraca wartość 0 i nie działają.  
  
 Jeśli `lpStgMedium` ->  *tymed* jest **TYMED_NULL**, **STGMEDIUM** powinna przydzielona i wypełnione określony przez *lpFormatEtc -> tymed*. Jeśli nie **TYMED_NULL**, **STGMEDIUM** powinno być wypełnione w miejscu z danymi.  
  
 Jest to zaawansowane możliwym do zastąpienia. Należy przesłonić tę funkcję, aby zapewnić dane w formacie żądanego i średnia liczba godzin. W zależności od danych warto override jednego z innych wersji tej funkcji. Jeśli dane są małe i stały rozmiar, Zastąp `OnRenderGlobalData`. Jeśli znajduje się w pliku danych lub o rozmiarze zmiennej, Zastąp `OnRenderFileData`.  
  
 Aby uzyskać więcej informacji, zobacz [Metoda IDataObject::GetData](http://msdn.microsoft.com/library/windows/desktop/ms678431), [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812), [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177), i [TYMED](http://msdn.microsoft.com/library/windows/desktop/ms691227) w zestawie Windows SDK.  
  
##  <a name="onrenderfiledata"></a>  COleServerItem::OnRenderFileData  
 Wywoływane przez platformę, by pobrać dane w określonym formacie, gdy nośnik to plik.  
  
```  
virtual BOOL OnRenderFileData(
    LPFORMATETC lpFormatEtc,  
    CFile* pFile);
```  
  
### <a name="parameters"></a>Parametry  
 `lpFormatEtc`  
 Wskazuje [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktury, określając format, w którym jest wymagane informacje.  
  
 `pFile`  
 Wskazuje `CFile` obiektu, w którym ma być renderowany danych.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Określony format jest jednym wcześniej umieszczone w `COleDataSource` przy użyciu [DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata) funkcji członkowskiej do renderowania opóźnione. Domyślna implementacja tej funkcji po prostu zwraca **FALSE**.  
  
 Jest to zaawansowane możliwym do zastąpienia. Należy przesłonić tę funkcję, aby zapewnić dane w formacie żądanego i średnia liczba godzin. W zależności od danych warto override jednego z innych wersji tej funkcji. Jeśli chcesz obsługiwać wiele nośników magazynowania, należy zastąpić [OnRenderData](#onrenderdata). Jeśli znajduje się w pliku danych lub o rozmiarze zmiennej, Zastąp [OnRenderFileData](#onrenderfiledata).  
  
 Aby uzyskać więcej informacji, zobacz [Metoda IDataObject::GetData](http://msdn.microsoft.com/library/windows/desktop/ms678431) i [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) w zestawie Windows SDK.  
  
##  <a name="onrenderglobaldata"></a>  COleServerItem::OnRenderGlobalData  
 Wywoływane przez platformę, by pobrać dane w określonym formacie po określonym nośnik pamięci globalnej.  
  
```  
virtual BOOL OnRenderGlobalData(
    LPFORMATETC lpFormatEtc,  
    HGLOBAL* phGlobal);
```  
  
### <a name="parameters"></a>Parametry  
 `lpFormatEtc`  
 Wskazuje [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktury, określając format, w którym jest wymagane informacje.  
  
 `phGlobal`  
 Wskazuje dojścia do globalnej pamięci, w którym ma zostać zwrócone dane. Jeśli brak pamięci została przydzielona, ten parametr może być **NULL**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Określony format jest jednym wcześniej umieszczone w `COleDataSource` przy użyciu [DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata) funkcji członkowskiej do renderowania opóźnione. Domyślna implementacja tej funkcji po prostu zwraca **FALSE**.  
  
 Jeśli `phGlobal` jest **NULL**, następnie nowy `HGLOBAL` powinny być przydzielone i zwracany w `phGlobal`. W przeciwnym razie `HGLOBAL` określonego przez `phGlobal` powinno być wypełnione z danymi. Ilość danych umieszczone w `HGLOBAL` nie może przekraczać bieżący rozmiar bloku pamięci. Ponadto nie można przydzielić bloku, aby większy rozmiar.  
  
 Jest to zaawansowane możliwym do zastąpienia. Należy przesłonić tę funkcję, aby zapewnić dane w formacie żądanego i średnia liczba godzin. W zależności od danych warto override jednego z innych wersji tej funkcji. Jeśli chcesz obsługiwać wiele nośników magazynowania, należy zastąpić [OnRenderData](#onrenderdata). Jeśli znajduje się w pliku danych lub o rozmiarze zmiennej, Zastąp [OnRenderFileData](#onrenderfiledata).  
  
 Aby uzyskać więcej informacji, zobacz [Metoda IDataObject::GetData](http://msdn.microsoft.com/library/windows/desktop/ms678431) i [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) w zestawie Windows SDK.  
  
##  <a name="onsetcolorscheme"></a>  COleServerItem::OnSetColorScheme  
 Wywoływane przez platformę, by określić paletę kolorów, które będą używane podczas edycji elementu OLE.  
  
```  
virtual BOOL OnSetColorScheme(const LOGPALETTE* lpLogPalette);
```  
  
### <a name="parameters"></a>Parametry  
 `lpLogPalette`  
 Wskaźnik do systemu Windows [LOGPALETTE](http://msdn.microsoft.com/library/windows/desktop/dd145040) struktury.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli jest używany z palety kolorów; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli aplikacja kontenera została napisana przy użyciu Microsoft Foundation Class Library, ta funkcja jest wywoływana podczas [IOleObject::SetColorScheme](http://msdn.microsoft.com/library/windows/desktop/ms683971) funkcja odpowiadającego `COleClientItem` nosi nazwę obiektu. Domyślna implementacja zwraca **FALSE**. Należy przesłonić tę funkcję, jeśli chcesz użyć zalecanych palety. Aplikacja serwera nie trzeba używać sugerowane palety.  
  
 Aby uzyskać więcej informacji, zobacz [IOleObject::SetColorScheme](http://msdn.microsoft.com/library/windows/desktop/ms683971) w zestawie Windows SDK.  
  
##  <a name="onsetdata"></a>  COleServerItem::OnSetData  
 Wywoływane przez platformę, aby zamienić dane elementu OLE z określonymi danymi.  
  
```  
virtual BOOL OnSetData(
    LPFORMATETC lpFormatEtc,  
    LPSTGMEDIUM lpStgMedium,  
    BOOL bRelease);
```  
  
### <a name="parameters"></a>Parametry  
 `lpFormatEtc`  
 Wskaźnik do [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) Struktura określająca format danych.  
  
 `lpStgMedium`  
 Wskaźnik do [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) struktury, w którym znajdują się dane.  
  
 `bRelease`  
 Wskazuje, kto jest właścicielem nośnik po zakończeniu wywołania funkcji. Obiekt wywołujący decyduje, kto jest odpowiedzialny za zwolnienie zasobów przydzielonych imieniu nośnika magazynowania. Obiekt wywołujący robi to przez ustawienie `bRelease`. Jeśli `bRelease` jest różna od zera, element serwera przejmuje, zwalnianie nośnik, po zakończeniu używania go. Gdy `bRelease` ma wartość 0, wywołujący zachowuje własność i elementu serwera można użyć nośnik tylko na czas trwania wywołania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Element serwera dopiero właściciela danych został pomyślnie uzyskano go. Oznacza to, że nie trwa własność Jeśli zwraca 0. Jeśli źródło danych przejmuje, zwalnia nośnik wywołując [ReleaseStgMedium](http://msdn.microsoft.com/library/windows/desktop/ms693491) funkcji.  
  
 Domyślna implementacja nie działa. Należy przesłonić tę funkcję, aby zamienić dane elementu OLE z określonymi danymi. Jest to zaawansowane możliwym do zastąpienia.  
  
 Aby uzyskać więcej informacji, zobacz [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812), [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177), i [ReleaseStgMedium](http://msdn.microsoft.com/library/windows/desktop/ms693491) w zestawie Windows SDK.  
  
##  <a name="onsetextent"></a>  COleServerItem::OnSetExtent  
 Wywoływane przez platformę, by przekazać elementowi OLE, ile miejsca jest dostępnych w dokumencie kontenera.  
  
```  
virtual BOOL OnSetExtent(
    DVASPECT nDrawAspect,  
    const CSize& size);
```  
  
### <a name="parameters"></a>Parametry  
 `nDrawAspect`  
 Określa aspekt element OLE, których zakresem jest określany. Ten parametr może mieć jedną z następujących wartości:  
  
- `DVASPECT_CONTENT` Element jest reprezentowana w taki sposób, że mogą być wyświetlane jako osadzonego wewnątrz jej kontenera.  
  
- `DVASPECT_THUMBNAIL` Element jest renderowany w reprezentacji "miniatur", aby mogły być wyświetlone w narzędziu do przeglądania.  
  
- `DVASPECT_ICON` Element jest reprezentowany przez ikonę.  
  
- `DVASPECT_DOCPRINT` Element jest wyświetlana tak, jakby były drukowane, za pomocą polecenia Drukuj z menu Plik.  
  
 `size`  
 A [CSize](../../atl-mfc-shared/reference/csize-class.md) struktury, określając nowy rozmiar elementu OLE.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli aplikacja kontenera zostało zapisane z Microsoft Foundation Class Library, ta funkcja jest wywoływana podczas [SetExtent](../../mfc/reference/coleclientitem-class.md#setextent) funkcji członkowskiej odpowiadającego `COleClientItem` nosi nazwę obiektu. Domyślne zestawy implementacji [m_sizeExtent](#m_sizeextent) elementu członkowskiego z określonym rozmiarem Jeśli `nDrawAspect` jest `DVASPECT_CONTENT`; w przeciwnym razie zwraca wartość 0. Należy przesłonić tę funkcję, aby wykonać specjalnego przetwarzania, jeśli należy zmienić rozmiar elementu.  
  
##  <a name="onshow"></a>  COleServerItem::OnShow  
 Wywoływane przez platformę, by poinstruować aplikacji serwera, aby wyświetlić element OLE w miejscu.  
  
```  
virtual void OnShow();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest wywoływana zazwyczaj, gdy użytkownik aplikacji kontenera tworzy element lub wykonuje zlecenia, takie jak edytowanie, który wymaga elementu, który ma być wyświetlany. Domyślna implementacja próbuje wykonać aktywację w miejscu. Jeśli to się nie powiedzie, wywołania funkcji `OnOpen` funkcji członkowskiej, aby wyświetlić element OLE w osobnym oknie.  
  
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
 `pSender`  
 Wskaźnik do elementu, który zmodyfikował dokument. Może być **NULL**.  
  
 `lHint`  
 Zawiera informacje dotyczące zmiany.  
  
 `pHint`  
 Wskaźnik do przechowywania informacji na temat modyfikacji obiektu.  
  
 `nDrawAspect`  
 Wartość z zakresu od `DVASPECT` wyliczenia. Ten parametr może mieć jeden z następujących wartości:  
  
- `DVASPECT_CONTENT` Element jest reprezentowana w taki sposób, że mogą być wyświetlane jako osadzonego wewnątrz jej kontenera.  
  
- `DVASPECT_THUMBNAIL` Element jest renderowany w reprezentacji "miniatur", aby mogły być wyświetlone w narzędziu do przeglądania.  
  
- `DVASPECT_ICON` Element jest reprezentowany przez ikonę.  
  
- `DVASPECT_DOCPRINT` Element jest wyświetlana tak, jakby były drukowane, za pomocą polecenia Drukuj z menu Plik.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja wywołuje [NotifyChanged](#notifychanged), niezależnie od wskazówki lub nadawcy.  
  
##  <a name="onupdateitems"></a>  COleServerItem::OnUpdateItems  
 Wywoływane przez platformę, by uaktualnić wszystkie elementy w dokumencie serwera.  
  
```  
virtual void OnUpdateItems();
```  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja wywołuje [UpdateLink](../../mfc/reference/coleclientitem-class.md#updatelink) dla wszystkich `COleClientItem` obiektów w dokumencie.  
  
##  <a name="setitemname"></a>  COleServerItem::SetItemName  
 Wywołanie tej funkcji podczas tworzenia połączonego elementu można ustawić jej nazwy.  
  
```  
void SetItemName(LPCTSTR lpszItemName);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszItemName`  
 Wskaźnik na nową nazwę elementu.  
  
### <a name="remarks"></a>Uwagi  
 Nazwa musi być unikatowa w obrębie dokumentu. Aplikacja serwera wywołanego do edycji połączonego elementu aplikacja używa tej nazwy można znaleźć elementu. Nie trzeba przeprowadzać wywołanie tej funkcji dla elementów osadzonych.  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC HIERSVR](../../visual-cpp-samples.md)   
 [Klasa CDocItem](../../mfc/reference/cdocitem-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa COleClientItem](../../mfc/reference/coleclientitem-class.md)   
 [Klasa COleServerDoc](../../mfc/reference/coleserverdoc-class.md)   
 [Klasa COleTemplateServer](../../mfc/reference/coletemplateserver-class.md)
