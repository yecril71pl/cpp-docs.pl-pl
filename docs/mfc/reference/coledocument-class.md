---
title: Klasa COleDocument
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
ms.openlocfilehash: 51169de521997890190aab52e4afd02ed383af3b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375036"
---
# <a name="coledocument-class"></a>Klasa COleDocument

Klasa podstawowa dla dokumentów OLE, które obsługują edycję wizualną.

## <a name="syntax"></a>Składnia

```
class COleDocument : public CDocument
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleDocument::COleDocument](#coledocument)|Konstruuje `COleDocument` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleDocument::AddItem](#additem)|Dodaje element do listy elementów obsługiwanych przez dokument.|
|[COleDocument::ApplyPrintDevice](#applyprintdevice)|Ustawia urządzenie docelowe drukowania dla wszystkich elementów klienta w dokumencie.|
|[COleDocument::EnableCompoundFile](#enablecompoundfile)|Powoduje, że dokumenty mają być przechowywane przy użyciu formatu pliku OLE Structured Storage.|
|[COleDocument::GetInPlaceActiveItem](#getinplaceactiveitem)|Zwraca element OLE, który jest aktualnie aktywny w miejscu.|
|[COleDocument::GetNextClientItem](#getnextclientitem)|Pobiera następny element klienta do iteracji.|
|[COleDocument::GetNextItem](#getnextitem)|Pobiera następny element dokumentu do iteracji.|
|[COleDocument::GetNextServerItem](#getnextserveritem)|Pobiera następny element serwera do iteracji.|
|[COleDocument::GetPrimarySelectedItem](#getprimaryselecteditem)|Zwraca podstawowy zaznaczony element OLE w dokumencie.|
|[COleDocument::GetStartPosition](#getstartposition)|Pobiera początkową pozycję, aby rozpocząć iterację.|
|[COleDocument::HasBlankItems](#hasblankitems)|Sprawdza puste elementy w dokumencie.|
|[COleDocument::OnShowViews](#onshowviews)|Wywoływane, gdy dokument staje się widoczny lub niewidoczny.|
|[COleDocument::Usuńjitem](#removeitem)|Usuwa element z listy elementów obsługiwanych przez dokument.|
|[COleDocument::UpdateModifiedFlag](#updatemodifiedflag)|Oznacza dokument jako zmodyfikowany, jeśli którykolwiek z zawartych elementów OLE został zmodyfikowany.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[COleDocument::OnEditChangeIcon](#oneditchangeicon)|Obsługuje zdarzenia w poleceniu menu Zmień ikonę.|
|[COleDocument::OnEditConvert](#oneditconvert)|Obsługuje konwersję osadzonego lub połączonego obiektu z jednego typu do drugiego.|
|[COleDocument::OnEditLinks](#oneditlinks)|Obsługuje zdarzenia w poleceniu Łącza w menu Edycja.|
|[COleDocument::OnFileSendMail](#onfilesendmail)|Wysyła wiadomość e-mail z dołączonym dokumentem.|
|[COleDocument::OnUpdateEditChangeIcon](#onupdateeditchangeicon)|Wywoływane przez strukturę, aby zaktualizować interfejs polecenia dla opcji menu Edytuj/Zmień ikonę.|
|[COleDocument::OnUpdateEditLinksMenu](#onupdateeditlinksmenu)|Wywoływane przez strukturę, aby zaktualizować interfejs polecenia dla opcji menu Edycja/Łącza.|
|[COleDocument::OnUpdateObjectVerbMenu](#onupdateobjectverbmenu)|Wywoływane przez strukturę, aby zaktualizować interfejs polecenia dla opcji menu Edit/ *ObjectName* i podmenu czasownika dostępne z Edit / *ObjectName*.|
|[COleDocument::OnUpdatePasteLinkMenu](#onupdatepastelinkmenu)|Wywoływane przez strukturę, aby zaktualizować interfejs polecenia dla opcji menu Wklej specjalne.|
|[COleDocument::OnUpdatePasteMenu](#onupdatepastemenu)|Wywoływane przez strukturę, aby zaktualizować interfejs użytkownika polecenia dla opcji menu Wklej.|

## <a name="remarks"></a>Uwagi

`COleDocument`pochodzi z `CDocument`programu , który umożliwia aplikacjom OLE korzystanie z architektury dokumentu/widoku dostarczonej przez bibliotekę klas Microsoft Foundation.

`COleDocument`traktuje dokument jako kolekcję [obiektów CDocItem](../../mfc/reference/cdocitem-class.md) do obsługi elementów OLE. Aplikacje kontenerów i serwerów wymagają takiej architektury, ponieważ ich dokumenty muszą być w stanie zawierać elementy OLE. [COleServerItem](../../mfc/reference/coleserveritem-class.md) i [COleClientItem](../../mfc/reference/coleclientitem-class.md) klasy, zarówno `CDocItem`pochodne z , zarządzać interakcje między aplikacjami i elementów OLE.

Jeśli piszesz prostą aplikację kontenera, wyprowadz klasę dokumentu z pliku `COleDocument`. Jeśli piszesz aplikację kontenera, która obsługuje łączenie z elementami osadzonymi zawartymi w dokumentach, należy wyprowadzić klasę dokumentu z [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md). W przypadku pisania aplikacji serwera lub kontenera/serwera kombinacji należy wyprowadzić klasę dokumentu z [programu COleServerDoc](../../mfc/reference/coleserverdoc-class.md). `COleLinkingDoc`i `COleServerDoc` pochodzą z `COleDocument`, więc te klasy dziedziczą wszystkie usługi dostępne w `COleDocument` i `CDocument`.

Aby `COleDocument`użyć , wywodź z niej klasę i dodaj funkcje do zarządzania danymi nie OLE aplikacji, a także elementami osadzonymi lub połączonymi. Jeśli zdefiniujesz `CDocItem`klasy pochodne do przechowywania danych natywnych aplikacji, `COleDocument` można użyć domyślnej implementacji zdefiniowanej przez do przechowywania danych OLE i innych niż OLE. Można również zaprojektować własne struktury danych do przechowywania danych innych niż OLE oddzielnie od elementów OLE. Aby uzyskać więcej informacji, zobacz artykuł [Kontenery: Pliki złożone](../../mfc/containers-compound-files.md)..

`CDocument`obsługuje wysyłanie dokumentu pocztą, jeśli obsługa poczty (MAPI) jest obecna. `COleDocument`zaktualizował [onFileSendMail](#onfilesendmail) do poprawnego obchodzenia się z dokumentami złożonymi. Aby uzyskać więcej informacji, zobacz artykuły [MAPI](../../mfc/mapi.md) i [MAPI support w MFC](../../mfc/mapi-support-in-mfc.md)..

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cdocument](../../mfc/reference/cdocument-class.md)

`COleDocument`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxole.h

## <a name="coledocumentadditem"></a><a name="additem"></a>COleDocument::AddItem

Wywołanie tej funkcji, aby dodać element do dokumentu.

```
virtual void AddItem(CDocItem* pItem);
```

### <a name="parameters"></a>Parametry

*pItem (własówce)*<br/>
Wskaźnik do dodawanych elementów dokumentu.

### <a name="remarks"></a>Uwagi

Nie trzeba wywoływać tę funkcję jawnie, gdy `COleClientItem` `COleServerItem` jest wywoływana przez lub konstruktora, który akceptuje wskaźnik do dokumentu.

## <a name="coledocumentapplyprintdevice"></a><a name="applyprintdevice"></a>COleDocument::ApplyPrintDevice

Wywołanie tej funkcji, aby zmienić urządzenie docelowe drukowania dla wszystkich wbudowanych elementów [COleClientItem](../../mfc/reference/coleclientitem-class.md) w dokumencie kontenera aplikacji.

```
BOOL ApplyPrintDevice(const DVTARGETDEVICE* ptd);
BOOL ApplyPrintDevice(const PRINTDLG* ppd);
```

### <a name="parameters"></a>Parametry

*Ptd*<br/>
Wskaźnik do `DVTARGETDEVICE` struktury danych, która zawiera informacje o nowym urządzeniu docelowym wydruku. Może mieć wartość NULL.

*Ppd*<br/>
Wskaźnik do `PRINTDLG` struktury danych, która zawiera informacje o nowym urządzeniu docelowym wydruku. Może mieć wartość NULL.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja aktualizuje urządzenie docelowe drukowania dla wszystkich elementów, ale nie odświeża pamięci podręcznej prezentacji dla tych elementów. Aby zaktualizować pamięć podręczną prezentacji dla elementu, zadzwoń [do COleClientItem::UpdateLink](../../mfc/reference/coleclientitem-class.md#updatelink).

Argumenty tej funkcji zawierają informacje używane przez ole do identyfikowania urządzenia docelowego. Struktura [PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-printdlga) zawiera informacje używane przez system Windows do inicjowania wspólnego okna dialogowego Drukowanie. Po zamknięciu okna dialogowego system Windows zwraca informacje o wyborach użytkownika w tej strukturze. Element `m_pd` członkowski [obiektu CPrintDialog](../../mfc/reference/cprintdialog-class.md) jest strukturą. `PRINTDLG`

Aby uzyskać więcej informacji, zobacz strukturę [PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-printdlga) w windows SDK.

Aby uzyskać więcej informacji, zobacz [strukturę DVTARGETDEVICE](/windows/win32/api/objidl/ns-objidl-dvtargetdevice) w sdk systemu Windows.

## <a name="coledocumentcoledocument"></a><a name="coledocument"></a>COleDocument::COleDocument

Konstruuje `COleDocument` obiekt.

```
COleDocument();
```

## <a name="coledocumentenablecompoundfile"></a><a name="enablecompoundfile"></a>COleDocument::EnableCompoundFile

Wywołanie tej funkcji, jeśli chcesz przechowywać dokument przy użyciu formatu pliku złożonego.

```
void EnableCompoundFile(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*bWłaszą*<br/>
Określa, czy obsługa plików złożonych jest włączona czy wyłączona.

### <a name="remarks"></a>Uwagi

Jest to również nazywane magazynem strukturalnym. Zazwyczaj wywołanie tej funkcji z konstruktora `COleDocument`klasy pochodnej. Aby uzyskać więcej informacji na temat dokumentów złożonych, zobacz artykuł [Kontenery: Pliki złożone](../../mfc/containers-compound-files.md)..

Jeśli ta funkcja elementu członkowskiego nie zostanie wywołana, dokumenty będą przechowywane w formacie pliku niestrukturalnym ("płaskim").

Po włączeniu lub wyłączeniu obsługi plików złożonych dla dokumentu ustawienie nie powinno być zmieniane w okresie istnienia dokumentu.

## <a name="coledocumentgetinplaceactiveitem"></a><a name="getinplaceactiveitem"></a>COleDocument::GetInPlaceActiveItem

Wywołanie tej funkcji, aby uzyskać element OLE, który jest aktualnie aktywowany w miejscu w oknie ramki zawierający widok identyfikowany przez *pWnd*.

```
virtual COleClientItem* GetInPlaceActiveItem(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*Pwnd*<br/>
Wskaźnik do okna, w które jest wyświetlany dokument kontenera.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do pojedynczego, aktywnego elementu OLE w miejscu; NULL, jeśli nie ma obecnie żadnego elementu OLE w stanie "aktywny w miejscu".

## <a name="coledocumentgetnextclientitem"></a><a name="getnextclientitem"></a>COleDocument::GetNextClientItem

Wywołanie tej funkcji wielokrotnie, aby uzyskać dostęp do każdego z elementów klienta w dokumencie.

```
COleClientItem* GetNextClientItem(POSITION& pos) const;
```

### <a name="parameters"></a>Parametry

*Poz*<br/>
Odwołanie do wartości POSITION ustawionej przez `GetNextClientItem`poprzednie wywołanie do ; wartość początkowa jest `GetStartPosition` zwracana przez funkcję elementu członkowskiego.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do następnego elementu klienta w dokumencie lub NULL, jeśli nie ma więcej elementów klienta.

### <a name="remarks"></a>Uwagi

Po każdym wywołaniu wartość *poz* jest ustawiona dla następnego elementu w dokumencie, który może lub nie może być elementem klienta.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#1](../../mfc/codesnippet/cpp/coledocument-class_1.cpp)]

## <a name="coledocumentgetnextitem"></a><a name="getnextitem"></a>COleDocument::GetNextItem

Wywołanie tej funkcji wielokrotnie, aby uzyskać dostęp do każdego z elementów w dokumencie.

```
virtual CDocItem* GetNextItem(POSITION& pos) const;
```

### <a name="parameters"></a>Parametry

*Poz*<br/>
Odwołanie do wartości POSITION ustawionej przez `GetNextItem`poprzednie wywołanie do ; wartość początkowa jest `GetStartPosition` zwracana przez funkcję elementu członkowskiego.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do elementu dokumentu w określonym położeniu.

### <a name="remarks"></a>Uwagi

Po każdym wywołaniu wartość *poz* jest ustawiona na wartość POSITION następnego elementu w dokumencie. Jeśli pobrany element jest ostatnim elementem w dokumencie, nową wartością *pos* jest NULL.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#2](../../mfc/codesnippet/cpp/coledocument-class_2.cpp)]

## <a name="coledocumentgetnextserveritem"></a><a name="getnextserveritem"></a>COleDocument::GetNextServerItem

Wywołanie tej funkcji wielokrotnie, aby uzyskać dostęp do każdego z elementów serwera w dokumencie.

```
COleServerItem* GetNextServerItem(POSITION& pos) const;
```

### <a name="parameters"></a>Parametry

*Poz*<br/>
Odwołanie do wartości POSITION ustawionej przez `GetNextServerItem`poprzednie wywołanie do ; wartość początkowa jest `GetStartPosition` zwracana przez funkcję elementu członkowskiego.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do następnego elementu serwera w dokumencie lub NULL, jeśli nie ma więcej elementów serwera.

### <a name="remarks"></a>Uwagi

Po każdym wywołaniu wartość *poz* jest ustawiona dla następnego elementu w dokumencie, który może lub nie może być elementem serwera.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleServer#2](../../mfc/codesnippet/cpp/coledocument-class_3.cpp)]

## <a name="coledocumentgetprimaryselecteditem"></a><a name="getprimaryselecteditem"></a>COleDocument::GetPrimarySelectedItem

Wywoływane przez strukturę, aby pobrać aktualnie wybrany element OLE w określonym widoku.

```
virtual COleClientItem* GetPrimarySelectedItem(CView* pView);
```

### <a name="parameters"></a>Parametry

*pWidok*<br/>
Wskaźnik do aktywnego obiektu widoku wyświetlającego dokument.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do pojedynczego, wybranego elementu OLE; NULL, jeśli nie wybrano żadnych elementów OLE lub jeśli wybrano więcej niż jeden.

### <a name="remarks"></a>Uwagi

Domyślna implementacja przeszukuje listę zawartych elementów OLE dla pojedynczego zaznaczonego elementu i zwraca do niego wskaźnik. Jeśli nie wybrano żadnego elementu lub jeśli zaznaczono więcej niż jeden element, funkcja zwraca wartość NULL. Należy zastąpić funkcję `CView::IsSelected` elementu członkowskiego w klasie widoku, aby ta funkcja działała. Zastąd w tej funkcji, jeśli masz własną metodę przechowywania zawartych elementów OLE.

## <a name="coledocumentgetstartposition"></a><a name="getstartposition"></a>COleDocument::GetStartPosition

Wywołanie tej funkcji, aby uzyskać położenie pierwszego elementu w dokumencie.

```
virtual POSITION GetStartPosition() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość POSITION, która może służyć do rozpoczynania iteracji za pośrednictwem elementów dokumentu; NULL, jeśli dokument nie zawiera żadnych elementów.

### <a name="remarks"></a>Uwagi

Przekaż wartość zwróconą `GetNextClientItem`do `GetNextServerItem` `GetNextItem`, lub .

## <a name="coledocumenthasblankitems"></a><a name="hasblankitems"></a>COleDocument::HasBlankItems

Wywołanie tej funkcji, aby ustalić, czy dokument zawiera puste elementy.

```
BOOL HasBlankItems() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli dokument zawiera puste elementy; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Pusty element to taki, którego prostokąt jest pusty.

## <a name="coledocumentoneditchangeicon"></a><a name="oneditchangeicon"></a>COleDocument::OnEditChangeIcon

Wyświetla okno dialogowe Ikona zmiany OLE i zmienia ikonę reprezentującą aktualnie zaznaczony element OLE na ikonę, która użytkownik zaznacza w oknie dialogowym.

```
afx_msg void OnEditChangeIcon();
```

### <a name="remarks"></a>Uwagi

`OnEditChangeIcon`tworzy i `COleChangeIconDialog` uruchamia okno dialogowe Zmień ikonę.

## <a name="coledocumentoneditconvert"></a><a name="oneditconvert"></a>COleDocument::OnEditConvert

Wyświetla okno dialogowe Konwertowanie OLE oraz konwertuje lub aktywuje aktualnie wybrany element OLE zgodnie z wyborami użytkownika w oknie dialogowym.

```
afx_msg void OnEditConvert();
```

### <a name="remarks"></a>Uwagi

`OnEditConvert`tworzy i `COleConvertDialog` uruchamia okno dialogowe Konwertuj.

Przykładem konwersji jest przekonwertowanie dokumentu programu Microsoft Word na dokument programu WordPad.

## <a name="coledocumentoneditlinks"></a><a name="oneditlinks"></a>COleDocument::OnEditLinks

Wyświetla okno dialogowe Edycja/Łącza OLE.

```
afx_msg void OnEditLinks();
```

### <a name="remarks"></a>Uwagi

`OnEditLinks`tworzy i `COleLinksDialog` uruchamia okno dialogowe Łącza, które umożliwia użytkownikowi zmianę połączonych obiektów.

## <a name="coledocumentonfilesendmail"></a><a name="onfilesendmail"></a>COleDocument::OnFileSendMail

Wysyła wiadomość za pośrednictwem hosta poczty rezydenta (jeśli istnieje) z dokumentem jako załącznikiem.

```
afx_msg void OnFileSendMail();
```

### <a name="remarks"></a>Uwagi

`OnFileSendMail`wywołania `OnSaveDocument` serializacji (zapisywania) dokumentów bez tytułu i zmodyfikowanych do pliku tymczasowego, który jest następnie wysyłany pocztą elektroniczną. Jeśli dokument nie został zmodyfikowany, plik tymczasowy nie jest potrzebny; oryginał zostanie wysłany. `OnFileSendMail`ładuje MAPI32. DLL, jeśli nie został jeszcze załadowany.

W przeciwieństwie `OnFileSendMail` do `CDocument`implementacji for , funkcja ta obsługuje pliki złożone poprawnie.

Aby uzyskać więcej informacji, zobacz [tematy MAPI](../../mfc/mapi.md) i obsługa mapi w artykułach [MFC..](../../mfc/mapi-support-in-mfc.md)

## <a name="coledocumentonshowviews"></a><a name="onshowviews"></a>COleDocument::OnShowViews

Struktura wywołuje tę funkcję po zmianie stanu widoczności dokumentu.

```
virtual void OnShowViews(BOOL bVisible);
```

### <a name="parameters"></a>Parametry

*b Widoczne*<br/>
Wskazuje, czy dokument stał się widoczny czy niewidoczny.

### <a name="remarks"></a>Uwagi

Domyślna wersja tej funkcji nic nie robi. Zastąd go, jeśli aplikacja musi wykonać wszelkie specjalne przetwarzanie, gdy zmieni się widoczność dokumentu.

## <a name="coledocumentonupdateeditchangeicon"></a><a name="onupdateeditchangeicon"></a>COleDocument::OnUpdateEditChangeIcon

Wywoływane przez strukturę, aby zaktualizować polecenie Zmień ikonę w menu Edycja.

```
afx_msg void OnUpdateEditChangeIcon(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parametry

*pCmdUI*<br/>
Wskaźnik do `CCmdUI` struktury reprezentującej menu, które wygenerowało polecenie aktualizacji. Program obsługi aktualizacji `Enable` wywołuje funkcję `CCmdUI` elementu członkowskiego struktury za pośrednictwem *pCmdUI,* aby zaktualizować interfejs użytkownika.

### <a name="remarks"></a>Uwagi

`OnUpdateEditChangeIcon`aktualizuje interfejs użytkownika polecenia w zależności od tego, czy w dokumencie istnieje prawidłowa ikona. Zastąd w tej funkcji należy zmienić zachowanie.

## <a name="coledocumentonupdateeditlinksmenu"></a><a name="onupdateeditlinksmenu"></a>COleDocument::OnUpdateEditLinksMenu

Wywoływane przez strukturę, aby zaktualizować łącza polecenia w menu Edycja.

```
afx_msg void OnUpdateEditLinksMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parametry

*pCmdUI*<br/>
Wskaźnik do `CCmdUI` struktury reprezentującej menu, które wygenerowało polecenie aktualizacji. Program obsługi aktualizacji `Enable` wywołuje funkcję `CCmdUI` elementu członkowskiego struktury za pośrednictwem *pCmdUI,* aby zaktualizować interfejs użytkownika.

### <a name="remarks"></a>Uwagi

Począwszy od pierwszego elementu OLE `OnUpdateEditLinksMenu` w dokumencie, uzyskuje dostęp do każdego elementu, sprawdza, czy element jest łączem, a jeśli jest to łącze, włącza polecenie Łącza. Zastąd w tej funkcji należy zmienić zachowanie.

## <a name="coledocumentonupdateobjectverbmenu"></a><a name="onupdateobjectverbmenu"></a>COleDocument::OnUpdateObjectVerbMenu

Wywoływane przez strukturę, aby zaktualizować *objectname* polecenia w menu Edycja i podmenu Czasownik dostępne z *ObjectName* polecenia, gdzie *ObjectName* jest nazwą obiektu OLE osadzone w dokumencie.

```
afx_msg void OnUpdateObjectVerbMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parametry

*pCmdUI*<br/>
Wskaźnik do `CCmdUI` struktury reprezentującej menu, które wygenerowało polecenie aktualizacji. Program obsługi aktualizacji `Enable` wywołuje funkcję `CCmdUI` elementu członkowskiego struktury za pośrednictwem *pCmdUI,* aby zaktualizować interfejs użytkownika.

### <a name="remarks"></a>Uwagi

`OnUpdateObjectVerbMenu`aktualizuje interfejs użytkownika polecenia *ObjectName* w zależności od tego, czy w dokumencie istnieje prawidłowy obiekt. Jeśli obiekt istnieje, w menu Edycja jest włączone polecenie *ObjectName.* Po wybraniu tego polecenia menu wyświetlany jest podmenu Czasownik. Podmenu czasownika zawiera wszystkie polecenia zlecenia dostępne dla obiektu, takie jak Edycja, Właściwości i tak dalej. Zastąd w tej funkcji należy zmienić zachowanie.

## <a name="coledocumentonupdatepastelinkmenu"></a><a name="onupdatepastelinkmenu"></a>COleDocument::OnUpdatePasteLinkMenu

Wywoływane przez strukturę, aby ustalić, czy połączony element OLE może być wklejony ze Schowka.

```
afx_msg void OnUpdatePasteLinkMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parametry

*pCmdUI*<br/>
Wskaźnik do `CCmdUI` struktury reprezentującej menu, które wygenerowało polecenie aktualizacji. Program obsługi aktualizacji `Enable` wywołuje funkcję `CCmdUI` elementu członkowskiego struktury za pośrednictwem *pCmdUI,* aby zaktualizować interfejs użytkownika.

### <a name="remarks"></a>Uwagi

Polecenie Menu Wklej specjalne jest włączone lub wyłączone w zależności od tego, czy element można wkleić do dokumentu, czy nie.

## <a name="coledocumentonupdatepastemenu"></a><a name="onupdatepastemenu"></a>COleDocument::OnUpdatePasteMenu

Wywoływane przez strukturę, aby ustalić, czy osadzony element OLE może być wklejony ze Schowka.

```
afx_msg void OnUpdatePasteMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parametry

*pCmdUI*<br/>
Wskaźnik do `CCmdUI` struktury reprezentującej menu, które wygenerowało polecenie aktualizacji. Program obsługi aktualizacji `Enable` wywołuje funkcję `CCmdUI` elementu członkowskiego struktury za pośrednictwem *pCmdUI,* aby zaktualizować interfejs użytkownika.

### <a name="remarks"></a>Uwagi

Polecenie i przycisk menu Wklej są włączone lub wyłączone w zależności od tego, czy element można wkleić do dokumentu, czy nie.

## <a name="coledocumentremoveitem"></a><a name="removeitem"></a>COleDocument::Usuńjitem

Wywołanie tej funkcji, aby usunąć element z dokumentu.

```
virtual void RemoveItem(CDocItem* pItem);
```

### <a name="parameters"></a>Parametry

*pItem (własówce)*<br/>
Wskaźnik do elementu dokumentu do usunięcia.

### <a name="remarks"></a>Uwagi

Zazwyczaj nie trzeba wywoływać tej funkcji jawnie; jest on nazywany przez destruktorów dla `COleClientItem` i `COleServerItem`.

## <a name="coledocumentupdatemodifiedflag"></a><a name="updatemodifiedflag"></a>COleDocument::UpdateModifiedFlag

Wywołanie tej funkcji, aby oznaczyć dokument jako zmodyfikowany, jeśli którykolwiek z zawartych elementów OLE zostały zmodyfikowane.

```
virtual void UpdateModifiedFlag();
```

### <a name="remarks"></a>Uwagi

Dzięki temu ramach monitować użytkownika, aby zapisać dokument przed zamknięciem, nawet jeśli dane macierzyste w dokumencie nie został zmodyfikowany.

## <a name="see-also"></a>Zobacz też

[Pojemnik na próbki MFC](../../overview/visual-cpp-samples.md)<br/>
[Próbka MFCBIND](../../overview/visual-cpp-samples.md)<br/>
[Klasa CDocument](../../mfc/reference/cdocument-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
