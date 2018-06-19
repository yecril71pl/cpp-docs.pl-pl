---
title: Klasa COleDocument | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleDocument
- AFXOLE/COleDocument
- AFXOLE/COleDocument::COleDocument
- AFXOLE/COleDocument::AddItem
- AFXOLE/COleDocument::ApplyPrintDevice
- AFXOLE/COleDocument::EnableCompoundFile
- AFXOLE/COleDocument::GetInPlaceActiveItem
- AFXOLE/COleDocument::GetNextClientItem
- AFXOLE/COleDocument::GetNextItem
- AFXOLE/COleDocument::GetNextServerItem
- AFXOLE/COleDocument::GetPrimarySelectedItem
- AFXOLE/COleDocument::GetStartPosition
- AFXOLE/COleDocument::HasBlankItems
- AFXOLE/COleDocument::OnShowViews
- AFXOLE/COleDocument::RemoveItem
- AFXOLE/COleDocument::UpdateModifiedFlag
- AFXOLE/COleDocument::OnEditChangeIcon
- AFXOLE/COleDocument::OnEditConvert
- AFXOLE/COleDocument::OnEditLinks
- AFXOLE/COleDocument::OnFileSendMail
- AFXOLE/COleDocument::OnUpdateEditChangeIcon
- AFXOLE/COleDocument::OnUpdateEditLinksMenu
- AFXOLE/COleDocument::OnUpdateObjectVerbMenu
- AFXOLE/COleDocument::OnUpdatePasteLinkMenu
- AFXOLE/COleDocument::OnUpdatePasteMenu
dev_langs:
- C++
helpviewer_keywords:
- COleDocument [MFC], COleDocument
- COleDocument [MFC], AddItem
- COleDocument [MFC], ApplyPrintDevice
- COleDocument [MFC], EnableCompoundFile
- COleDocument [MFC], GetInPlaceActiveItem
- COleDocument [MFC], GetNextClientItem
- COleDocument [MFC], GetNextItem
- COleDocument [MFC], GetNextServerItem
- COleDocument [MFC], GetPrimarySelectedItem
- COleDocument [MFC], GetStartPosition
- COleDocument [MFC], HasBlankItems
- COleDocument [MFC], OnShowViews
- COleDocument [MFC], RemoveItem
- COleDocument [MFC], UpdateModifiedFlag
- COleDocument [MFC], OnEditChangeIcon
- COleDocument [MFC], OnEditConvert
- COleDocument [MFC], OnEditLinks
- COleDocument [MFC], OnFileSendMail
- COleDocument [MFC], OnUpdateEditChangeIcon
- COleDocument [MFC], OnUpdateEditLinksMenu
- COleDocument [MFC], OnUpdateObjectVerbMenu
- COleDocument [MFC], OnUpdatePasteLinkMenu
- COleDocument [MFC], OnUpdatePasteMenu
ms.assetid: dc2ecb99-03e1-44c7-bb69-48056dd1b672
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6317d7c14f76355df908c9809df633533df3fb61
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33377125"
---
# <a name="coledocument-class"></a>Klasa COleDocument
Klasa podstawowa dla dokumentów OLE, które obsługują edycji.  
  
## <a name="syntax"></a>Składnia  
  
```  
class COleDocument : public CDocument  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleDocument::COleDocument](#coledocument)|Konstruuje `COleDocument` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleDocument::AddItem](#additem)|Dodaje element do listy elementów, obsługiwane przez dokument.|  
|[COleDocument::ApplyPrintDevice](#applyprintdevice)|Ustawia cel drukowania urządzenia dla wszystkich elementów klienta w dokumencie.|  
|[COleDocument::EnableCompoundFile](#enablecompoundfile)|Powoduje, że dokumenty mają być przechowywane w formacie pliku OLE magazynem strukturalnym.|  
|[COleDocument::GetInPlaceActiveItem](#getinplaceactiveitem)|Zwraca element OLE, który jest obecnie aktywny w miejscu.|  
|[COleDocument::GetNextClientItem](#getnextclientitem)|Pobiera następnego elementu klienta potrzeby iteracji.|  
|[COleDocument::GetNextItem](#getnextitem)|Pobiera element dokumentu dalej potrzeby iteracji.|  
|[COleDocument::GetNextServerItem](#getnextserveritem)|Pobiera iteracja następnego elementu serwera.|  
|[COleDocument::GetPrimarySelectedItem](#getprimaryselecteditem)|Zwraca głównej zaznaczony element OLE w dokumencie.|  
|[COleDocument::GetStartPosition](#getstartposition)|Pobiera położenie początkowe w celu rozpoczęcia iteracji.|  
|[COleDocument::HasBlankItems](#hasblankitems)|Sprawdza, czy puste elementy w dokumencie.|  
|[COleDocument::OnShowViews](#onshowviews)|Wywoływane, gdy dokument staje się widoczny lub niewidoczny.|  
|[COleDocument::RemoveItem](#removeitem)|Usuwa element z listy elementów, obsługiwane przez dokument.|  
|[COleDocument::UpdateModifiedFlag](#updatemodifiedflag)|Oznacza dokumentu, modyfikowanie, jeśli zawartych w niej elementów OLE zostały zmodyfikowane.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleDocument::OnEditChangeIcon](#oneditchangeicon)|Obsługuje zdarzenia w poleceniu Zmień ikonę.|  
|[COleDocument::OnEditConvert](#oneditconvert)|Obsługuje konwersji obiekt osadzony lub połączony z jednego typu na inny.|  
|[COleDocument::OnEditLinks](#oneditlinks)|Obsługuje zdarzenia w poleceniu łącza w menu Edycja.|  
|[COleDocument::OnFileSendMail](#onfilesendmail)|Wysyła wiadomość e-mail z dołączonym dokumentem.|  
|[COleDocument::OnUpdateEditChangeIcon](#onupdateeditchangeicon)|Wywoływane przez platformę, by zaktualizować polecenia interfejsu użytkownika dla opcji menu Edycja/Zmień ikonę.|  
|[COleDocument::OnUpdateEditLinksMenu](#onupdateeditlinksmenu)|Wywoływane przez platformę, by zaktualizować polecenia interfejsu użytkownika dla opcji menu Edycja/łącza.|  
|[COleDocument::OnUpdateObjectVerbMenu](#onupdateobjectverbmenu)|Wywoływane przez platformę, aby zaktualizować polecenia interfejsu użytkownika dla edycji / *ObjectName* opcji menu i podmenu zlecenie użytkowcy edycji / *ObjectName*.|  
|[COleDocument::OnUpdatePasteLinkMenu](#onupdatepastelinkmenu)|Wywoływane przez platformę, by zaktualizować polecenia interfejsu użytkownika dla Wklej specjalne opcji menu.|  
|[COleDocument::OnUpdatePasteMenu](#onupdatepastemenu)|Wywoływane przez platformę, by zaktualizować polecenia interfejsu użytkownika dla opcji menu Paste.|  
  
## <a name="remarks"></a>Uwagi  
 `COleDocument` jest pochodną **CDocument**, dzięki czemu aplikacje OLE do użycia architektury dokument/widok udostępniane przez Microsoft Foundation Class Library.  
  
 `COleDocument` traktuje dokumentu jako kolekcja [CDocItem](../../mfc/reference/cdocitem-class.md) obiekty do obsługi elementów OLE. Zarówno kontenera i aplikacji serwera wymagają takie architekturę, ponieważ swoje dokumenty muszą mieć możliwość zawiera elementy OLE. [COleServerItem](../../mfc/reference/coleserveritem-class.md) i [COleClientItem](../../mfc/reference/coleclientitem-class.md) klasy zarówno pochodną `CDocItem`, zarządzanie interakcje między aplikacjami i elementy OLE.  
  
 Podczas pisania aplikacji kontenera proste, pochodzi z klasy dokumentu `COleDocument`. Podczas pisania aplikacji kontenera, który obsługuje łączenie elementy osadzone zawarty w swoje dokumenty, pochodzi z klasy dokumentu [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md). Jeśli piszesz serwera aplikacji lub kombinacji kontener/serwer, pochodzi z klasy dokumentu [COleServerDoc](../../mfc/reference/coleserverdoc-class.md). `COleLinkingDoc` i `COleServerDoc` pochodne `COleDocument`, więc te klasy dziedziczy wszystkie usługi dostępne w `COleDocument` i **CDocument**.  
  
 Aby użyć `COleDocument`, pochodną klasy oraz dodawać funkcje do zarządzania aplikacji innych niż OLE jak i elementy osadzone i połączone. W przypadku definiowania `CDocItem`-pochodnej klasy do przechowywania danych natywnych aplikacji, można użyć w implementacji domyślnej zdefiniowane przez `COleDocument` do przechowywania OLE i danych innych niż OLE. Można również projektować własnych struktur danych do przechowywania danych innych niż OLE niezależnie od elementy OLE. Aby uzyskać więcej informacji, zobacz artykuł [kontenery: pliki złożone](../../mfc/containers-compound-files.md)...  
  
 **Cdocument —** obsługuje wysyłanie dokumentu pocztą, jeśli występuje obsługi poczty (MAPI). `COleDocument` zaktualizował [OnFileSendMail](#onfilesendmail) do obsługi dokumentów złożonych poprawnie. Aby uzyskać więcej informacji, zobacz artykuły [MAPI](../../mfc/mapi.md) i [Obsługa MAPI w MFC](../../mfc/mapi-support-in-mfc.md)...  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocument](../../mfc/reference/cdocument-class.md)  
  
 `COleDocument`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxole.h  
  
##  <a name="additem"></a>  COleDocument::AddItem  
 Wywołanie tej funkcji, aby dodać element do dokumentu.  
  
```  
virtual void AddItem(CDocItem* pItem);
```  
  
### <a name="parameters"></a>Parametry  
 `pItem`  
 Wskaźnik do dokumentu element dodawany.  
  
### <a name="remarks"></a>Uwagi  
 Nie trzeba jawnie wywołanie tej funkcji, gdy jest wywoływana przez `COleClientItem` lub `COleServerItem` konstruktora akceptującego wskaźnik do dokumentu.  
  
##  <a name="applyprintdevice"></a>  COleDocument::ApplyPrintDevice  
 Wywołanie tej funkcji, aby zmienić urządzenie docelowe wydruku dla wszystkich osadzonych [COleClientItem](../../mfc/reference/coleclientitem-class.md) elementów w dokumencie kontenera aplikacji.  
  
```  
BOOL ApplyPrintDevice(const DVTARGETDEVICE* ptd);  
BOOL ApplyPrintDevice(const PRINTDLG* ppd);
```  
  
### <a name="parameters"></a>Parametry  
 `ptd`  
 Wskaźnik do **DVTARGETDEVICE** struktury danych, który zawiera informacje dotyczące nowego urządzenia docelowego drukowania. Może być **NULL**.  
  
 `ppd`  
 Wskaźnik do **PRINTDLG** struktury danych, który zawiera informacje dotyczące nowego urządzenia docelowego drukowania. Może być **NULL**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli funkcja zakończyło się pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja aktualizuje drukowania urządzenia dla wszystkich elementów, ale nie powoduje odświeżenia pamięci podręcznej prezentacji dla tych elementów. Aby zaktualizować pamięci podręcznej prezentacji dla elementu, należy wywołać [COleClientItem::UpdateLink](../../mfc/reference/coleclientitem-class.md#updatelink).  
  
 Argumenty do tej funkcji zawierają informacje OLE używane do identyfikowania urządzenia docelowego. [PRINTDLG](http://msdn.microsoft.com/library/windows/desktop/ms646843) struktura zawiera informacje, używany w systemie Windows można zainicjować okno dialogowe Drukuj wspólnej. Po zamknięciu okna dialogowego Windows zwraca informacje na temat opcji użytkownika w tej struktury. `m_pd` Członkiem [CPrintDialog](../../mfc/reference/cprintdialog-class.md) obiekt jest **PRINTDLG** struktury.  
  
 Aby uzyskać więcej informacji, zobacz [PRINTDLG](http://msdn.microsoft.com/library/windows/desktop/ms646843) struktury w zestawie Windows SDK.  
  
 Aby uzyskać więcej informacji, zobacz [DVTARGETDEVICE](http://msdn.microsoft.com/library/windows/desktop/ms686613) struktury w zestawie Windows SDK.  
  
##  <a name="coledocument"></a>  COleDocument::COleDocument  
 Konstruuje `COleDocument` obiektu.  
  
```  
COleDocument();
```  
  
##  <a name="enablecompoundfile"></a>  COleDocument::EnableCompoundFile  
 Wywołanie tej funkcji, jeśli chcesz przechowywać dokumentu w formacie pliku złożone.  
  
```  
void EnableCompoundFile(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `bEnable`  
 Określa, czy obsługa złożone plików jest włączona.  
  
### <a name="remarks"></a>Uwagi  
 To jest również nazywany magazynem strukturalnym. Zazwyczaj wywołanie tej funkcji z konstruktora z `COleDocument`-klasy. Aby uzyskać więcej informacji na temat dokumentów złożonych, zobacz artykuł [kontenery: pliki złożone](../../mfc/containers-compound-files.md)...  
  
 Nie można wywołać funkcji członkowskiej, dokumenty będą przechowywane w formacie niemających określonej struktury pliku ("prosty").  
  
 Po Obsługa pliku złożonego jest włączone lub wyłączone dla dokumentu, ustawienia nie można zmienić okres istnienia dokumentu.  
  
##  <a name="getinplaceactiveitem"></a>  COleDocument::GetInPlaceActiveItem  
 Wywołanie tej funkcji, aby uzyskać OLE elementu, który jest aktywowany w miejscu okno ramowe zawierające widok identyfikowane przez `pWnd`.  
  
```  
virtual COleClientItem* GetInPlaceActiveItem(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 `pWnd`  
 Wskaźnik do okna, które wyświetla dokument, do kontenera.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do jednej, w miejscu aktywny element OLE; **NULL** Jeśli nie ma żadnego elementu OLE w stanie "aktywny w miejscu".  
  
##  <a name="getnextclientitem"></a>  COleDocument::GetNextClientItem  
 Wywołanie tej funkcji, aby uzyskać dostęp każdy z elementów klienta w dokumencie.  
  
```  
COleClientItem* GetNextClientItem(POSITION& pos) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Odwołanie do **pozycji** wartość zestawu przez poprzednie wywołanie `GetNextClientItem`; wartość początkowa jest zwracany przez `GetStartPosition` funkcji członkowskiej.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do następnego elementu klienta w dokumencie lub **NULL** Jeśli nie ma żadnych więcej towarów klienta.  
  
### <a name="remarks"></a>Uwagi  
 Po każdym wywołaniu wartość `pos` ustawiono dla następnego elementu w dokumencie, który może lub nie może być elementem klienta.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCOleContainer#1](../../mfc/codesnippet/cpp/coledocument-class_1.cpp)]  
  
##  <a name="getnextitem"></a>  COleDocument::GetNextItem  
 Wywołanie tej funkcji, aby uzyskać dostęp każdy z elementów w dokumencie.  
  
```  
virtual CDocItem* GetNextItem(POSITION& pos) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Odwołanie do **pozycji** wartość zestawu przez poprzednie wywołanie `GetNextItem`; wartość początkowa jest zwracany przez `GetStartPosition` funkcji członkowskiej.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do elementu dokumentu w określonej pozycji.  
  
### <a name="remarks"></a>Uwagi  
 Po każdym wywołaniu wartość `pos` ustawiono **pozycji** wartość następnego elementu w dokumencie. Jeśli element pobrane jest ostatnim elementem w dokumencie, nowa wartość `pos` jest **NULL**.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCOleContainer#2](../../mfc/codesnippet/cpp/coledocument-class_2.cpp)]  
  
##  <a name="getnextserveritem"></a>  COleDocument::GetNextServerItem  
 Wywołanie tej funkcji, aby uzyskać dostęp każdy serwer elementów w dokumencie.  
  
```  
COleServerItem* GetNextServerItem(POSITION& pos) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Odwołanie do **pozycji** wartość zestawu przez poprzednie wywołanie `GetNextServerItem`; wartość początkowa jest zwracany przez `GetStartPosition` funkcji członkowskiej.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do następnego elementu serwera w dokumencie lub **NULL** Jeśli nie ma żadnych więcej towarów serwera.  
  
### <a name="remarks"></a>Uwagi  
 Po każdym wywołaniu wartość `pos` ustawiono dla następnego elementu w dokumencie, który może lub nie może być elementem serwera.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCOleServer#2](../../mfc/codesnippet/cpp/coledocument-class_3.cpp)]  
  
##  <a name="getprimaryselecteditem"></a>  COleDocument::GetPrimarySelectedItem  
 Wywoływane przez platformę, by pobrać zaznaczony element OLE w określonym widoku.  
  
```  
virtual COleClientItem* GetPrimarySelectedItem(CView* pView);
```  
  
### <a name="parameters"></a>Parametry  
 `pView`  
 Wskaźnik do obiektu widoku aktywnego wyświetlania dokumentu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do pojedynczej, zaznaczony element OLE; **NULL** Jeśli nie wybrano żadnych elementów OLE lub jeśli więcej niż jeden zostanie wybrany.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja wyszukuje elementy dla jednego wybranego elementu listy zawartych w niej OLE i zwraca wskaźnik do niego. Jeśli nie ma elementu zaznaczone, lub jeśli istnieje więcej niż jeden element wybrany, funkcja zwraca **NULL**. Konieczne jest przesłonięcie `CView::IsSelected` funkcji członkowskiej we własnej klasy widoku dla tej funkcji do pracy. Jeśli masz własnej metody przechowywania zawartych w niej elementów OLE, należy przesłonić tę funkcję.  
  
##  <a name="getstartposition"></a>  COleDocument::GetStartPosition  
 Wywołanie tej funkcji, aby uzyskać położenie pierwszego elementu w dokumencie.  
  
```  
virtual POSITION GetStartPosition() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A **pozycji** wartość, która może służyć do rozpoczęcia iteracji elementów dokumentu. **NULL** Jeśli dokument nie zawiera żadnych elementów.  
  
### <a name="remarks"></a>Uwagi  
 Wartość zwracana do przekazania `GetNextItem`, `GetNextClientItem`, lub `GetNextServerItem`.  
  
##  <a name="hasblankitems"></a>  COleDocument::HasBlankItems  
 Wywołanie tej funkcji w celu ustalenia, czy dokument zawiera wszystkie elementy puste.  
  
```  
BOOL HasBlankItems() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli dokument zawiera wszystkie elementy puste; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Pusty element jest jedną z którego prostokąt jest pusta.  
  
##  <a name="oneditchangeicon"></a>  COleDocument::OnEditChangeIcon  
 Wyświetla okno dialogowe OLE Zmień ikonę i zmienia ikony reprezentującej aktualnie zaznaczony element OLE na ikonę wybranego przez użytkownika w oknie dialogowym.  
  
```  
afx_msg void OnEditChangeIcon();
```  
  
### <a name="remarks"></a>Uwagi  
 `OnEditChangeIcon` Tworzy i uruchamia `COleChangeIconDialog` okno dialogowe Zmienianie ikony.  
  
##  <a name="oneditconvert"></a>  COleDocument::OnEditConvert  
 Wyświetla okno dialogowe Konwertowanie OLE i konwertuje lub uaktywnia zaznaczony element OLE w zależności od opcji użytkownika w oknie dialogowym.  
  
```  
afx_msg void OnEditConvert();
```  
  
### <a name="remarks"></a>Uwagi  
 `OnEditConvert` Tworzy i uruchamia `COleConvertDialog` konwertowanie — okno dialogowe.  
  
 Przykład konwersji konwertuje dokument programu Microsoft Word do dokumentu programu WordPad.  
  
##  <a name="oneditlinks"></a>  COleDocument::OnEditLinks  
 Wyświetla okno dialogowe OLE/łączy edycji.  
  
```  
afx_msg void OnEditLinks();
```  
  
### <a name="remarks"></a>Uwagi  
 `OnEditLinks` Tworzy i uruchamia `COleLinksDialog` okno dialogowe łącza, który umożliwia użytkownikowi zmianę powiązane obiekty.  
  
##  <a name="onfilesendmail"></a>  COleDocument::OnFileSendMail  
 Wysyła komunikat za pośrednictwem hosta rezydentna poczty (jeśli istnieją) w dokumencie jako załącznik.  
  
```  
afx_msg void OnFileSendMail();
```  
  
### <a name="remarks"></a>Uwagi  
 `OnFileSendMail` wywołania `OnSaveDocument` do serializacji (bez tytułu i zmodyfikowane dokumenty do pliku tymczasowego, który jest następnie wysyłana za pośrednictwem poczty elektronicznej Zapisz). Jeśli dokument nie został zmodyfikowany, plik tymczasowy nie jest wymagane; oryginalny są wysyłane. `OnFileSendMail` ładuje MAPI32. Biblioteki DLL, jeśli nie został już załadowany.  
  
 W przeciwieństwie do wykonania `OnFileSendMail` dla **CDocument**, ta funkcja obsługuje pliki złożone poprawnie.  
  
 Aby uzyskać więcej informacji, zobacz [tematy MAPI](../../mfc/mapi.md) i [Obsługa MAPI w MFC](../../mfc/mapi-support-in-mfc.md) artykułów.  
  
##  <a name="onshowviews"></a>  COleDocument::OnShowViews  
 Struktura wywołuje tej funkcji po widoczności dokumentu zmiany stanu.  
  
```  
virtual void OnShowViews(BOOL bVisible);
```  
  
### <a name="parameters"></a>Parametry  
 `bVisible`  
 Wskazuje, czy dokument ma stają się widoczne lub niewidoczne.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna wersja ta funkcja nie działa. Zastąpienie go, jeśli aplikacja musi wykonywać żadnych specjalnego przetwarzania, po zmianie widoczności dokumentu.  
  
##  <a name="onupdateeditchangeicon"></a>  COleDocument::OnUpdateEditChangeIcon  
 Wywoływane przez platformę, by zaktualizować polecenia Zmień ikonę menu Edycja.  
  
```  
afx_msg void OnUpdateEditChangeIcon(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>Parametry  
 `pCmdUI`  
 Wskaźnik do `CCmdUI` strukturę, która reprezentuje menu generowane polecenia update. Wywołuje program obsługi aktualizacji **włączyć** funkcji członkowskiej klasy `CCmdUI` struktury za pośrednictwem `pCmdUI` można zaktualizować interfejsu użytkownika.  
  
### <a name="remarks"></a>Uwagi  
 `OnUpdateEditChangeIcon` Aktualizuje polecenia interfejsu użytkownika, w zależności od tego, czy jest prawidłową ikoną istnieje w dokumencie. Należy przesłonić tę funkcję, aby zmienić zachowanie.  
  
##  <a name="onupdateeditlinksmenu"></a>  COleDocument::OnUpdateEditLinksMenu  
 Wywoływane przez platformę, by zaktualizować polecenie łącza w menu Edycja.  
  
```  
afx_msg void OnUpdateEditLinksMenu(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>Parametry  
 `pCmdUI`  
 Wskaźnik do `CCmdUI` strukturę, która reprezentuje menu generowane polecenia update. Wywołuje program obsługi aktualizacji **włączyć** funkcji członkowskiej klasy `CCmdUI` struktury za pośrednictwem `pCmdUI` można zaktualizować interfejsu użytkownika.  
  
### <a name="remarks"></a>Uwagi  
 Począwszy od pierwszego elementu OLE w dokumencie `OnUpdateEditLinksMenu` uzyskuje dostęp do każdego elementu, sprawdza, czy element jest łączem i, jeśli jest to łącze umożliwia polecenie łącza. Należy przesłonić tę funkcję, aby zmienić zachowanie.  
  
##  <a name="onupdateobjectverbmenu"></a>  COleDocument::OnUpdateObjectVerbMenu  
 Wywoływane przez platformę, aby zaktualizować *ObjectName* polecenia w menu Edycja i podmenu zlecenie użytkowcy *ObjectName* polecenie, gdzie *ObjectName* jest nazwą Obiekt OLE osadzony w dokumencie.  
  
```  
afx_msg void OnUpdateObjectVerbMenu(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>Parametry  
 `pCmdUI`  
 Wskaźnik do `CCmdUI` strukturę, która reprezentuje menu generowane polecenia update. Wywołuje program obsługi aktualizacji **włączyć** funkcji członkowskiej klasy `CCmdUI` struktury za pośrednictwem `pCmdUI` można zaktualizować interfejsu użytkownika.  
  
### <a name="remarks"></a>Uwagi  
 `OnUpdateObjectVerbMenu` aktualizacje *ObjectName* polecenia interfejsu użytkownika, w zależności od tego, czy istnieje prawidłowy obiekt w dokumencie. Jeśli istnieje obiekt, *ObjectName* polecenie menu Edycja jest włączone. Po wybraniu tego polecenia menu podmenu zlecenie jest wyświetlany. Podmenu zlecenie zawiera wszystkie polecenia zlecenie dostępne dla obiektu, na przykład edycji, właściwości i tak dalej. Należy przesłonić tę funkcję, aby zmienić zachowanie.  
  
##  <a name="onupdatepastelinkmenu"></a>  COleDocument::OnUpdatePasteLinkMenu  
 Wywoływane przez platformę, aby określić, czy połączony element OLE można wklejonych ze Schowka.  
  
```  
afx_msg void OnUpdatePasteLinkMenu(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>Parametry  
 `pCmdUI`  
 Wskaźnik do `CCmdUI` strukturę, która reprezentuje menu generowane polecenia update. Wywołuje program obsługi aktualizacji **włączyć** funkcji członkowskiej klasy `CCmdUI` struktury za pośrednictwem `pCmdUI` można zaktualizować interfejsu użytkownika.  
  
### <a name="remarks"></a>Uwagi  
 Wklej specjalne polecenie jest włączone lub wyłączone w zależności od tego, czy element można wkleić do dokumentu lub nie.  
  
##  <a name="onupdatepastemenu"></a>  COleDocument::OnUpdatePasteMenu  
 Wywoływane przez platformę, aby określić, czy element osadzony OLE można wklejonych ze Schowka.  
  
```  
afx_msg void OnUpdatePasteMenu(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>Parametry  
 `pCmdUI`  
 Wskaźnik do `CCmdUI` strukturę, która reprezentuje menu generowane polecenia update. Wywołuje program obsługi aktualizacji **włączyć** funkcji członkowskiej klasy `CCmdUI` struktury za pośrednictwem `pCmdUI` można zaktualizować interfejsu użytkownika.  
  
### <a name="remarks"></a>Uwagi  
 Polecenia menu Paste i przycisk są włączone lub wyłączone w zależności od tego, czy element można wkleić do dokumentu lub nie.  
  
##  <a name="removeitem"></a>  COleDocument::RemoveItem  
 Wywołanie tej funkcji, aby usunąć element z dokumentu.  
  
```  
virtual void RemoveItem(CDocItem* pItem);
```  
  
### <a name="parameters"></a>Parametry  
 `pItem`  
 Wskaźnik do elementu dokumentu do usunięcia.  
  
### <a name="remarks"></a>Uwagi  
 Zwykle nie trzeba jawnie; wywołanie tej funkcji jest ona wywoływana przez destruktory dla `COleClientItem` i `COleServerItem`.  
  
##  <a name="updatemodifiedflag"></a>  COleDocument::UpdateModifiedFlag  
 Wywołanie tej funkcji, aby oznaczyć dokumentu, modyfikowanie, jeśli zostały zmodyfikowane zawartych w niej elementów OLE.  
  
```  
virtual void UpdateModifiedFlag();
```  
  
### <a name="remarks"></a>Uwagi  
 Dzięki temu framework monit, aby zapisać dokument przed jego zamknięciem, nawet jeśli nie został zmodyfikowany danych natywnych w dokumencie.  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC kontenera](../../visual-cpp-samples.md)   
 [Przykładowe MFC MFCBIND](../../visual-cpp-samples.md)   
 [Cdocument — klasa](../../mfc/reference/cdocument-class.md)   
 [Wykres hierarchii](../../mfc/hierarchy-chart.md)



