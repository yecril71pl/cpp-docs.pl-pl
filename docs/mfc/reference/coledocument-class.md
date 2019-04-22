---
title: COleDocument Class
ms.date: 11/04/2016
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
ms.openlocfilehash: d1922c2f2d804c2a93d30dc0708b2d3ae037414d
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58768708"
---
# <a name="coledocument-class"></a>COleDocument Class

Klasa bazowa dla OLE dokumentów, które obsługują edycję wizualną.

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
|[COleDocument::AddItem](#additem)|Dodaje element do listy elementów utrzymane w dokumencie.|
|[COleDocument::ApplyPrintDevice](#applyprintdevice)|Ustawia print-urządzenie dla wszystkich elementów klienta w dokumencie.|
|[COleDocument::EnableCompoundFile](#enablecompoundfile)|Powoduje, że dokumenty, które mają być przechowywane przy użyciu formatu pliku magazynu strukturalnego OLE.|
|[COleDocument::GetInPlaceActiveItem](#getinplaceactiveitem)|Zwraca element OLE, który jest obecnie aktywny w miejscu.|
|[COleDocument::GetNextClientItem](#getnextclientitem)|Pobiera następny element klienta do wykonania iteracji.|
|[COleDocument::GetNextItem](#getnextitem)|Pobiera następny element dokumentu do wykonania iteracji.|
|[COleDocument::GetNextServerItem](#getnextserveritem)|Pobiera następny element serwera do wykonania iteracji.|
|[COleDocument::GetPrimarySelectedItem](#getprimaryselecteditem)|Zwraca główny wybrany element OLE w dokumencie.|
|[COleDocument::GetStartPosition](#getstartposition)|Pobiera położenie początkowe w celu rozpoczęcia iteracji.|
|[COleDocument::HasBlankItems](#hasblankitems)|Sprawdza, czy puste elementy w dokumencie.|
|[COleDocument::OnShowViews](#onshowviews)|Wywoływane, gdy dokument staje się widoczny lub niewidoczny.|
|[COleDocument::RemoveItem](#removeitem)|Usuwa element z listy elementów utrzymane w dokumencie.|
|[COleDocument::UpdateModifiedFlag](#updatemodifiedflag)|Powoduje oznaczenie dokumentu jako modyfikacji, jeśli zostały zmodyfikowane zawartych elementów OLE.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[COleDocument::OnEditChangeIcon](#oneditchangeicon)|Obsługuje zdarzenia w poleceniu menu Zmień ikonę.|
|[COleDocument::OnEditConvert](#oneditconvert)|Obsługuje konwersji obiekt osadzony lub połączony z jednego typu na inny.|
|[COleDocument::OnEditLinks](#oneditlinks)|Obsługuje zdarzenia w poleceniu łącza w menu Edycja.|
|[COleDocument::OnFileSendMail](#onfilesendmail)|Wysyła wiadomość e-mail z dołączony dokument.|
|[COleDocument::OnUpdateEditChangeIcon](#onupdateeditchangeicon)|Metoda wywoływana przez platformę, by zaktualizować poleceń interfejsu użytkownika dla opcji menu Edycja/Zmień ikonę.|
|[COleDocument::OnUpdateEditLinksMenu](#onupdateeditlinksmenu)|Metoda wywoływana przez platformę, by zaktualizować poleceń interfejsu użytkownika dla opcji menu Edycja/łącza.|
|[COleDocument::OnUpdateObjectVerbMenu](#onupdateobjectverbmenu)|Wywoływane przez platformę, zaktualizować poleceń interfejsu użytkownika w celu edycji / *ObjectName* opcji menu i podmenu zlecenie dostępne z edycji / *ObjectName*.|
|[COleDocument::OnUpdatePasteLinkMenu](#onupdatepastelinkmenu)|Metoda wywoływana przez platformę, by zaktualizować poleceń interfejsu użytkownika dla Wklej specjalne opcji menu.|
|[COleDocument::OnUpdatePasteMenu](#onupdatepastemenu)|Metoda wywoływana przez platformę, by zaktualizować poleceń interfejsu użytkownika dla opcji menu wklejania.|

## <a name="remarks"></a>Uwagi

`COleDocument` jest tworzony na podstawie `CDocument`, co pozwala aplikacji OLE architektury dokument/widok, dostarczone przez bibliotekę Microsoft Foundation Class.

`COleDocument` traktuje dokumentu jako zbiór [CDocItem](../../mfc/reference/cdocitem-class.md) obiektów w celu obsługi elementów OLE. Aplikacje kontenera i serwera wymagają takich architekturę, ponieważ swoje dokumenty muszą mieć możliwość zawierać elementy OLE. [COleServerItem](../../mfc/reference/coleserveritem-class.md) i [COleClientItem](../../mfc/reference/coleclientitem-class.md) klasy, oba pochodzące z `CDocItem`, zarządzanie nimi w interakcje między aplikacjami i elementów OLE.

Jeśli piszesz aplikację prostym kontenerem pochodną klasy dokumentów z `COleDocument`. Jeśli piszesz aplikację kontenera, która obsługuje łączenie elementów osadzonych zawartych dokumentów pochodną klasy dokumentów z [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md). Jeśli piszesz serwer aplikacji lub kombinacji kontenera/serwera, pochodzi z klasy dokumentów z [COleServerDoc](../../mfc/reference/coleserverdoc-class.md). `COleLinkingDoc` i `COleServerDoc` są uzyskiwane z `COleDocument`, więc te klasy dziedziczą usługi dostępne w `COleDocument` i `CDocument`.

Aby użyć `COleDocument`dziedziczyć po nim klasę i dodają funkcje do zarządzania aplikacji innych niż OLE danych także elementy osadzony lub połączony. Jeśli zdefiniujesz `CDocItem`-pochodne klasy do przechowywania danych natywnych aplikacji, możesz użyć implementacji domyślnej, zdefiniowane przez `COleDocument` do przechowywania OLE i danych innych niż OLE. Istnieje również możliwość projektowania własnych struktur danych do przechowywania danych innych niż OLE niezależnie od elementów OLE. Aby uzyskać więcej informacji, zobacz artykuł [kontenerów: Pliki złożone](../../mfc/containers-compound-files.md)...

`CDocument` obsługuje wysyłanie dokumentu za pośrednictwem poczty, jeśli występuje obsługi poczty (MAPI). `COleDocument` Zaktualizowano [onfilesendmail —](#onfilesendmail) poprawnie obsłużyć dokumentów złożonych. Aby uzyskać więcej informacji, zobacz artykuły [MAPI](../../mfc/mapi.md) i [Obsługa MAPI w MFC](../../mfc/mapi-support-in-mfc.md)...

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

`COleDocument`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxole.h

##  <a name="additem"></a>  COleDocument::AddItem

Wywołaj tę funkcję, aby dodać element do dokumentu.

```
virtual void AddItem(CDocItem* pItem);
```

### <a name="parameters"></a>Parametry

*pItem*<br/>
Wskaźnik do dokumentu element dodawany.

### <a name="remarks"></a>Uwagi

Nie trzeba jawnie wywołać tę funkcję, gdy jest wywoływana `COleClientItem` lub `COleServerItem` Konstruktor, który akceptuje wskaźnik do dokumentu.

##  <a name="applyprintdevice"></a>  COleDocument::ApplyPrintDevice

Wywołaj tę funkcję, aby zmienić urządzenie docelowe wydruku dla wszystkich osadzonych [COleClientItem](../../mfc/reference/coleclientitem-class.md) elementów w dokumencie kontenera aplikacji.

```
BOOL ApplyPrintDevice(const DVTARGETDEVICE* ptd);
BOOL ApplyPrintDevice(const PRINTDLG* ppd);
```

### <a name="parameters"></a>Parametry

*ptd*<br/>
Wskaźnik do `DVTARGETDEVICE` struktury danych, który zawiera informacje dotyczące nowego urządzenia docelowego drukowania. Może mieć wartości NULL.

*PPD*<br/>
Wskaźnik do `PRINTDLG` struktury danych, który zawiera informacje dotyczące nowego urządzenia docelowego drukowania. Może mieć wartości NULL.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja aktualizuje print-urządzenie dla wszystkich elementów, ale nie powoduje odświeżenia pamięci podręcznej prezentacji dla tych elementów. Aby zaktualizować pamięć podręczną prezentacji dla elementu, należy wywołać [COleClientItem::UpdateLink](../../mfc/reference/coleclientitem-class.md#updatelink).

Argumenty do tej funkcji zawierają informacje, które używa OLE, aby zidentyfikować urządzenia docelowego. [PRINTDLG](/windows/desktop/api/commdlg/ns-commdlg-tagpda) struktura zawiera informacje Windows używane do zainicjowania wspólne okno dialogowe drukowania. Po zamknięciu okna dialogowego użytkownika Windows zwraca informacje o wybór użytkownika w tej strukturze. `m_pd` Członkiem [CPrintDialog](../../mfc/reference/cprintdialog-class.md) obiekt jest `PRINTDLG` struktury.

Aby uzyskać więcej informacji, zobacz [PRINTDLG](/windows/desktop/api/commdlg/ns-commdlg-tagpda) struktury w zestawie Windows SDK.

Aby uzyskać więcej informacji, zobacz [DVTARGETDEVICE](/windows/desktop/api/objidl/ns-objidl-tagdvtargetdevice) struktury w zestawie Windows SDK.

##  <a name="coledocument"></a>  COleDocument::COleDocument

Konstruuje `COleDocument` obiektu.

```
COleDocument();
```

##  <a name="enablecompoundfile"></a>  COleDocument::EnableCompoundFile

Wywołaj tę funkcję, aby zapisać dokument w formacie pliku złożone.

```
void EnableCompoundFile(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*bWłączenie*<br/>
Określa, czy obsługa złożone plików jest włączone.

### <a name="remarks"></a>Uwagi

Jest to również nazywane strukturalny magazyn. Zazwyczaj wywołać tę funkcję z konstruktora obiektu usługi `COleDocument`-klasy pochodnej. Aby uzyskać więcej informacji na temat dokumentów złożonych, zobacz artykuł [kontenerów: Pliki złożone](../../mfc/containers-compound-files.md)...

Jeśli ta funkcja elementu członkowskiego nie jest wywołana, dokumenty będą przechowywane w formacie interfejsem plik ("prosty").

Po złożony plik pomocy technicznej jest włączone lub wyłączone dla dokumentu, ustawienia nie można zmienić w okresie istnienia dokumentu.

##  <a name="getinplaceactiveitem"></a>  COleDocument::GetInPlaceActiveItem

Wywołanie elementu tę funkcję, aby pobrać OLE, który jest obecnie aktywna w miejscu w okno ramowe zawierające widok identyfikowane przez *pWnd*.

```
virtual COleClientItem* GetInPlaceActiveItem(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Wskaźnik do okna, które wyświetla dokument, do kontenera.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do jednego, w miejscu aktywnego elementu OLE; Wartość NULL, jeśli nie ma żadnego elementu OLE w stanie "w miejscu aktywny".

##  <a name="getnextclientitem"></a>  COleDocument::GetNextClientItem

Wywołaj tę funkcję, aby dostęp do każdego z elementów klienta w dokumencie.

```
COleClientItem* GetNextClientItem(POSITION& pos) const;
```

### <a name="parameters"></a>Parametry

*punktu sprzedaży*<br/>
Odwołanie do pozycji wartość zestawu przez poprzednie wywołanie `GetNextClientItem`; wartość początkowa jest zwracany przez `GetStartPosition` funkcja elementu członkowskiego.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do następnego klienta elementów w dokumencie lub wartość NULL, jeśli istnieje już żadnych elementów klienta.

### <a name="remarks"></a>Uwagi

Po każdym wywołaniu wartość *pos* jest ustawiona dla następnego elementu w dokumencie, który może być lub może nie być elementu klienta.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#1](../../mfc/codesnippet/cpp/coledocument-class_1.cpp)]

##  <a name="getnextitem"></a>  COleDocument::GetNextItem

Wywołaj tę funkcję, aby uzyskać dostęp każdy z elementów w dokumencie.

```
virtual CDocItem* GetNextItem(POSITION& pos) const;
```

### <a name="parameters"></a>Parametry

*punktu sprzedaży*<br/>
Odwołanie do pozycji wartość zestawu przez poprzednie wywołanie `GetNextItem`; wartość początkowa jest zwracany przez `GetStartPosition` funkcja elementu członkowskiego.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do elementu dokumentu w określonej pozycji.

### <a name="remarks"></a>Uwagi

Po każdym wywołaniu wartość *pos* jest ustawiona na wartość pozycji następnego elementu w dokumencie. Jeśli pobrano element jest ostatnim elementem w dokumencie, nowa wartość *pos* ma wartość NULL.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#2](../../mfc/codesnippet/cpp/coledocument-class_2.cpp)]

##  <a name="getnextserveritem"></a>  COleDocument::GetNextServerItem

Wywołaj tę funkcję, aby dostęp do wszystkich elementów serwera w dokumencie.

```
COleServerItem* GetNextServerItem(POSITION& pos) const;
```

### <a name="parameters"></a>Parametry

*punktu sprzedaży*<br/>
Odwołanie do pozycji wartość zestawu przez poprzednie wywołanie `GetNextServerItem`; wartość początkowa jest zwracany przez `GetStartPosition` funkcja elementu członkowskiego.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do następnego serwera elementów w dokumencie lub wartość NULL, jeśli istnieje już żadnych elementów serwera.

### <a name="remarks"></a>Uwagi

Po każdym wywołaniu wartość *pos* jest ustawiona dla następnego elementu w dokumencie, który może być lub może być elementem serwera.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleServer#2](../../mfc/codesnippet/cpp/coledocument-class_3.cpp)]

##  <a name="getprimaryselecteditem"></a>  COleDocument::GetPrimarySelectedItem

Metoda wywoływana przez platformę, by pobrać zaznaczony element OLE w określonym widoku.

```
virtual COleClientItem* GetPrimarySelectedItem(CView* pView);
```

### <a name="parameters"></a>Parametry

*pView*<br/>
Wskaźnik do obiektu bieżącym widokiem wyświetlania dokumentu.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do jednego, zaznaczony element OLE; Wartość NULL Jeśli nie zaznaczono żadnych elementów OLE, lub jeśli istnieje więcej niż jedna jest zaznaczone.

### <a name="remarks"></a>Uwagi

Domyślna implementacja wyszukuje listę zawartej OLE elementów dla jednego wybranego elementu i zwraca wskaźnik do niego. Jeśli nie wybrano elementu lub istnieje więcej niż jeden element wybrany, funkcja zwraca wartość NULL. Konieczne jest przesłonięcie `CView::IsSelected` funkcja elementu członkowskiego w klasie widoku dla tej funkcji do pracy. Należy przesłonić tę funkcję, jeśli ma zastosowanie własnej metody przechowywania zawartych w niej elementów OLE.

##  <a name="getstartposition"></a>  COleDocument::GetStartPosition

Wywołaj tę funkcję, aby uzyskać pozycja pierwszego elementu w dokumencie.

```
virtual POSITION GetStartPosition() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość pozycji, który może służyć do rozpoczęcia iteracji przez elementy dokumentu. Wartość NULL, jeśli dokument nie zawiera żadnych elementów.

### <a name="remarks"></a>Uwagi

Przekaż wartość zwracana do `GetNextItem`, `GetNextClientItem`, lub `GetNextServerItem`.

##  <a name="hasblankitems"></a>  COleDocument::HasBlankItems

Wywołaj tę funkcję, aby ustalić, czy dokument zawiera jakiekolwiek elementy puste.

```
BOOL HasBlankItems() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli dokument zawiera wszystkie elementy puste; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Pusty element jest jednym prostokąta, którego jest pusty.

##  <a name="oneditchangeicon"></a>  COleDocument::OnEditChangeIcon

Powoduje wyświetlenie okna dialogowego OLE Zmień ikonę i zmienia się ikona reprezentująca zaznaczony element OLE na ikonę wybranego przez użytkownika w oknie dialogowym.

```
afx_msg void OnEditChangeIcon();
```

### <a name="remarks"></a>Uwagi

`OnEditChangeIcon` Tworzy i uruchamia `COleChangeIconDialog` okno dialogowe Zmienianie ikony.

##  <a name="oneditconvert"></a>  COleDocument::OnEditConvert

Zostanie wyświetlone okno dialogowe Konwertowanie OLE i konwertuje lub aktywuje zaznaczony element OLE, zgodnie z wyborów użytkownika w oknie dialogowym.

```
afx_msg void OnEditConvert();
```

### <a name="remarks"></a>Uwagi

`OnEditConvert` Tworzy i uruchamia `COleConvertDialog` konwertowanie, okno dialogowe.

Przykładem konwersji konwertuje dokument programu Microsoft Word do dokumentu programu WordPad.

##  <a name="oneditlinks"></a>  COleDocument::OnEditLinks

Wyświetla okno dialogowe OLE/łączy edycji.

```
afx_msg void OnEditLinks();
```

### <a name="remarks"></a>Uwagi

`OnEditLinks` Tworzy i uruchamia `COleLinksDialog` okno dialogowe łącza, który umożliwia użytkownikowi zmianę powiązane obiekty.

##  <a name="onfilesendmail"></a>  COleDocument::OnFileSendMail

Wysyła komunikat za pośrednictwem hosta rezydentnego poczty (jeśli istnieją) w dokumencie jako załącznik.

```
afx_msg void OnFileSendMail();
```

### <a name="remarks"></a>Uwagi

`OnFileSendMail` wywołania `OnSaveDocument` do serializacji (Zapisz) bez tytułu i zmodyfikowane dokumenty do tymczasowego pliku, który jest następnie wysyłany za pośrednictwem poczty elektronicznej. Jeśli dokument nie został zmodyfikowany, plik tymczasowy nie jest wymagana; oryginalne są wysyłane. `OnFileSendMail` ładuje MAPI32. Biblioteki DLL, jeśli nie została jeszcze załadowana.

W odróżnieniu od wdrożenia `OnFileSendMail` dla `CDocument`, ta funkcja obsługuje pliki złożone poprawnie.

Aby uzyskać więcej informacji, zobacz [tematy MAPI](../../mfc/mapi.md) i [Obsługa MAPI w MFC](../../mfc/mapi-support-in-mfc.md) artykułów...

##  <a name="onshowviews"></a>  COleDocument::OnShowViews

Struktura wywołuje tę funkcję po widoczności dokumentu, zmiany stanu.

```
virtual void OnShowViews(BOOL bVisible);
```

### <a name="parameters"></a>Parametry

*bVisible*<br/>
Wskazuje, czy dokument stał się widoczny lub niewidoczny.

### <a name="remarks"></a>Uwagi

Domyślna wersja tej funkcji, nic nie robi. Go zastąpić, jeśli aplikacja musi wykonać wszelkie specjalnego przetwarzania, po zmianie widoczności dokumentu.

##  <a name="onupdateeditchangeicon"></a>  COleDocument::OnUpdateEditChangeIcon

Metoda wywoływana przez platformę, by zaktualizuj polecenie Zmień ikonę menu Edycja.

```
afx_msg void OnUpdateEditChangeIcon(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parametry

*pCmdUI*<br/>
Wskaźnik do `CCmdUI` strukturę, która reprezentuje menu, który wygenerował polecenia update. Wywołuje program obsługi aktualizacji `Enable` funkcji składowej typu `CCmdUI` struktury za pomocą *pCmdUI* można zaktualizować interfejsu użytkownika.

### <a name="remarks"></a>Uwagi

`OnUpdateEditChangeIcon` Aktualizuje interfejs użytkownika poleceń w zależności od tego, czy istnieje prawidłową ikoną w dokumencie. Należy przesłonić tę funkcję, aby zmienić to zachowanie.

##  <a name="onupdateeditlinksmenu"></a>  COleDocument::OnUpdateEditLinksMenu

Metoda wywoływana przez platformę, by zaktualizować polecenia łącza w menu Edycja.

```
afx_msg void OnUpdateEditLinksMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parametry

*pCmdUI*<br/>
Wskaźnik do `CCmdUI` strukturę, która reprezentuje menu, który wygenerował polecenia update. Wywołuje program obsługi aktualizacji `Enable` funkcji składowej typu `CCmdUI` struktury za pomocą *pCmdUI* można zaktualizować interfejsu użytkownika.

### <a name="remarks"></a>Uwagi

Począwszy od pierwszego elementu OLE w dokumencie, `OnUpdateEditLinksMenu` uzyskuje dostęp do każdego elementu, sprawdza, czy element jest łączem i, jeśli jest to łącze umożliwia polecenia łącza. Należy przesłonić tę funkcję, aby zmienić to zachowanie.

##  <a name="onupdateobjectverbmenu"></a>  COleDocument::OnUpdateObjectVerbMenu

Wywoływane przez platformę, aby zaktualizować *ObjectName* polecenia na menu Edycja i podmenu zlecenie dostępne z *ObjectName* polecenie, gdzie *ObjectName* nazywa się osadzony obiekt OLE w dokumencie.

```
afx_msg void OnUpdateObjectVerbMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parametry

*pCmdUI*<br/>
Wskaźnik do `CCmdUI` strukturę, która reprezentuje menu, który wygenerował polecenia update. Wywołuje program obsługi aktualizacji `Enable` funkcji składowej typu `CCmdUI` struktury za pomocą *pCmdUI* można zaktualizować interfejsu użytkownika.

### <a name="remarks"></a>Uwagi

`OnUpdateObjectVerbMenu` aktualizacje *ObjectName* polecenia interfejsu użytkownika w zależności od tego, czy istnieje prawidłowy obiekt w dokumencie. Jeśli obiekt istnieje, *ObjectName* polecenie menu Edycja jest włączone. Po wybraniu tego polecenia menu jest wyświetlana w podmenu zlecenie. Podmenu zlecenie zawiera wszystkie polecenia zlecenie dostępne dla obiektu, takie jak Edycja, właściwości i tak dalej. Należy przesłonić tę funkcję, aby zmienić to zachowanie.

##  <a name="onupdatepastelinkmenu"></a>  COleDocument::OnUpdatePasteLinkMenu

Metoda wywoływana przez platformę, aby określić, czy połączony element OLE można wkleić ze Schowka.

```
afx_msg void OnUpdatePasteLinkMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parametry

*pCmdUI*<br/>
Wskaźnik do `CCmdUI` strukturę, która reprezentuje menu, który wygenerował polecenia update. Wywołuje program obsługi aktualizacji `Enable` funkcji składowej typu `CCmdUI` struktury za pomocą *pCmdUI* można zaktualizować interfejsu użytkownika.

### <a name="remarks"></a>Uwagi

Wklej specjalne polecenia menu jest włączone lub wyłączone w zależności od tego, czy element można wkleić do dokumentu lub nie.

##  <a name="onupdatepastemenu"></a>  COleDocument::OnUpdatePasteMenu

Metoda wywoływana przez platformę, aby określić, czy wbudowanego elementu OLE można wkleić ze Schowka.

```
afx_msg void OnUpdatePasteMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parametry

*pCmdUI*<br/>
Wskaźnik do `CCmdUI` strukturę, która reprezentuje menu, który wygenerował polecenia update. Wywołuje program obsługi aktualizacji `Enable` funkcji składowej typu `CCmdUI` struktury za pomocą *pCmdUI* można zaktualizować interfejsu użytkownika.

### <a name="remarks"></a>Uwagi

Polecenie menu Paste i przycisk włączone lub wyłączone w zależności od tego, czy element można wkleić do dokumentu lub nie.

##  <a name="removeitem"></a>  COleDocument::RemoveItem

Wywołaj tę funkcję, aby usunąć element z dokumentu.

```
virtual void RemoveItem(CDocItem* pItem);
```

### <a name="parameters"></a>Parametry

*pItem*<br/>
Wskaźnik do elementu dokumentu do usunięcia.

### <a name="remarks"></a>Uwagi

Zazwyczaj nie trzeba jawnie; wywołać tę funkcję jest ona wywoływana przez destruktory `COleClientItem` i `COleServerItem`.

##  <a name="updatemodifiedflag"></a>  COleDocument::UpdateModifiedFlag

Wywołaj tę funkcję, aby oznaczyć dokumentu, jak modyfikacji, jeśli zostały zmodyfikowane zawartych elementów OLE.

```
virtual void UpdateModifiedFlag();
```

### <a name="remarks"></a>Uwagi

Dzięki temu platformę, aby monitować użytkownika o Zapisz dokument przed jego zamknięciem, nawet jeśli nie został zmodyfikowany danych natywnych w dokumencie.

## <a name="see-also"></a>Zobacz także

[Próbki MFC kontenera](../../overview/visual-cpp-samples.md)<br/>
[Próbki MFC MFCBIND](../../overview/visual-cpp-samples.md)<br/>
[Klasa CDocument](../../mfc/reference/cdocument-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
