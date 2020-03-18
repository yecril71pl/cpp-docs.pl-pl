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
ms.openlocfilehash: b92c796fdaa972966dcbfa85b1e34f267b6c629c
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79421101"
---
# <a name="coledocument-class"></a>Klasa COleDocument

Klasa bazowa dla dokumentów OLE, które obsługują edycję wizualizacji.

## <a name="syntax"></a>Składnia

```
class COleDocument : public CDocument
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[COleDocument::COleDocument](#coledocument)|Konstruuje obiekt `COleDocument`.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[COleDocument:: AddItem](#additem)|Dodaje element do listy elementów obsługiwanych przez dokument.|
|[COleDocument::ApplyPrintDevice](#applyprintdevice)|Ustawia urządzenie drukowania-docelowego dla wszystkich elementów klienta w dokumencie.|
|[COleDocument::EnableCompoundFile](#enablecompoundfile)|Powoduje, że dokumenty są przechowywane przy użyciu formatu pliku magazynu strukturalnego OLE.|
|[COleDocument::GetInPlaceActiveItem](#getinplaceactiveitem)|Zwraca element OLE, który jest obecnie aktywny.|
|[COleDocument::GetNextClientItem](#getnextclientitem)|Pobiera następny element klienta do iteracji.|
|[COleDocument::GetNextItem](#getnextitem)|Pobiera następny element dokumentu do iteracji.|
|[COleDocument::GetNextServerItem](#getnextserveritem)|Pobiera następny element serwera do iteracji.|
|[COleDocument::GetPrimarySelectedItem](#getprimaryselecteditem)|Zwraca podstawowy wybrany element OLE w dokumencie.|
|[COleDocument::GetStartPosition](#getstartposition)|Pobiera początkową pozycję, aby rozpocząć iterację.|
|[COleDocument::HasBlankItems](#hasblankitems)|Wyszukuje puste elementy w dokumencie.|
|[COleDocument::OnShowViews](#onshowviews)|Wywołuje się, gdy dokument jest widoczny lub niewidoczny.|
|[COleDocument:: RemoveItem](#removeitem)|Usuwa element z listy elementów obsługiwanych przez dokument.|
|[COleDocument::UpdateModifiedFlag](#updatemodifiedflag)|Oznacza dokument jako zmodyfikowany, jeśli którykolwiek z zawartych w nim elementów OLE został zmodyfikowany.|

### <a name="protected-methods"></a>Metody chronione

|Name (Nazwa)|Opis|
|----------|-----------------|
|[COleDocument::OnEditChangeIcon](#oneditchangeicon)|Obsługuje zdarzenia w menu Zmień ikonę.|
|[COleDocument::OnEditConvert](#oneditconvert)|Obsługuje konwersję osadzonego lub połączonego obiektu z jednego typu na drugi.|
|[COleDocument::OnEditLinks](#oneditlinks)|Obsługuje zdarzenia w poleceniu Links w menu Edycja.|
|[COleDocument::OnFileSendMail](#onfilesendmail)|Wysyła wiadomość e-mail z dołączonym dokumentem.|
|[COleDocument::OnUpdateEditChangeIcon](#onupdateeditchangeicon)|Wywoływane przez platformę, aby zaktualizować interfejs użytkownika poleceń dla opcji menu Edytuj/Zmień.|
|[COleDocument::OnUpdateEditLinksMenu](#onupdateeditlinksmenu)|Wywoływane przez platformę, aby zaktualizować interfejs użytkownika poleceń dla opcji menu Edytuj/linki.|
|[COleDocument::OnUpdateObjectVerbMenu](#onupdateobjectverbmenu)|Wywoływane przez platformę, aby zaktualizować interfejs użytkownika poleceń dla opcji menu Edytuj/ *ObjectName* i podmenu czasownik, do którego można uzyskać dostęp z edycji/ *ObjectName*.|
|[COleDocument::OnUpdatePasteLinkMenu](#onupdatepastelinkmenu)|Wywoływane przez platformę, aby zaktualizować interfejs użytkownika poleceń dla opcji menu Wklej specjalnie.|
|[COleDocument::OnUpdatePasteMenu](#onupdatepastemenu)|Wywoływane przez platformę, aby zaktualizować interfejs użytkownika poleceń dla opcji menu Wklej.|

## <a name="remarks"></a>Uwagi

`COleDocument` pochodzi od `CDocument`, co umożliwia aplikacjom OLE używanie architektury dokumentu/widoku dostarczonej przez biblioteka MFC.

`COleDocument` traktuje dokument jako kolekcję obiektów [CDocItem](../../mfc/reference/cdocitem-class.md) do obsługi elementów OLE. Aplikacje kontenerów i serwerów wymagają takiej architektury, ponieważ ich dokumenty muszą być w stanie zawierać elementy OLE. Klasy [COleServerItem](../../mfc/reference/coleserveritem-class.md) i [COleClientItem](../../mfc/reference/coleclientitem-class.md) , zarówno pochodne od `CDocItem`, zarządzają interakcjami między aplikacjami i elementami OLE.

Jeśli piszesz prostą aplikację kontenera, Utwórz klasę dokumentu z `COleDocument`. Jeśli piszesz aplikację kontenera, która obsługuje łączenie z osadzonymi elementami zawartymi w jego dokumentach, Utwórz klasę dokumentu z [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md). W przypadku pisania aplikacji serwera lub kontenera/serwera, Utwórz klasę dokumentu z [COleServerDoc](../../mfc/reference/coleserverdoc-class.md). `COleLinkingDoc` i `COleServerDoc` są wyprowadzane z `COleDocument`, więc te klasy dziedziczą wszystkie usługi dostępne w `COleDocument` i `CDocument`.

Aby użyć `COleDocument`, należy utworzyć z niej klasę i dodać funkcje do zarządzania danymi nienależącymi do OLE, a także osadzonymi lub połączonymi elementami. Jeśli zdefiniujesz klasy pochodne `CDocItem`do przechowywania danych natywnych aplikacji, możesz użyć domyślnej implementacji zdefiniowanej przez `COleDocument` do przechowywania zarówno danych OLE, jak i innych niż OLE. Możesz również projektować własne struktury danych do przechowywania danych nienależących do OLE niezależnie od elementów OLE. Aby uzyskać więcej informacji, zobacz [kontenery artykułów: pliki złożone](../../mfc/containers-compound-files.md)...

`CDocument` obsługuje wysyłanie dokumentu za pośrednictwem poczty, jeśli istnieje obsługa poczty (MAPI). `COleDocument` zaktualizował [OnFileSendMail](#onfilesendmail) w celu poprawnego obsługi dokumentów złożonych. Aby uzyskać więcej informacji, zapoznaj się z artykułami obsługa [MAPI](../../mfc/mapi.md) i [MAPI w MFC](../../mfc/mapi-support-in-mfc.md)..

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

`COleDocument`

## <a name="requirements"></a>Wymagania

**Nagłówek:** Afxole. h

##  <a name="additem"></a>COleDocument:: AddItem

Wywołaj tę funkcję, aby dodać element do dokumentu.

```
virtual void AddItem(CDocItem* pItem);
```

### <a name="parameters"></a>Parametry

*pItem*<br/>
Wskaźnik do dodawanego elementu dokumentu.

### <a name="remarks"></a>Uwagi

Nie ma potrzeby wywoływania tej funkcji jawnie, gdy jest wywoływana przez konstruktora `COleClientItem` lub `COleServerItem`, który akceptuje wskaźnik do dokumentu.

##  <a name="applyprintdevice"></a>COleDocument::ApplyPrintDevice

Wywołaj tę funkcję, aby zmienić urządzenie Print-Target dla wszystkich osadzonych elementów [COleClientItem](../../mfc/reference/coleclientitem-class.md) w dokumencie kontenera aplikacji.

```
BOOL ApplyPrintDevice(const DVTARGETDEVICE* ptd);
BOOL ApplyPrintDevice(const PRINTDLG* ppd);
```

### <a name="parameters"></a>Parametry

*ptd*<br/>
Wskaźnik do struktury danych `DVTARGETDEVICE`, która zawiera informacje o nowym urządzeniu drukowania. Może mieć wartość NULL.

*PPD*<br/>
Wskaźnik do struktury danych `PRINTDLG`, która zawiera informacje o nowym urządzeniu drukowania. Może mieć wartość NULL.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja aktualizuje urządzenie drukowania-docelowego dla wszystkich elementów, ale nie odświeża pamięci podręcznej prezentacji dla tych elementów. Aby zaktualizować pamięć podręczną prezentacji dla elementu, wywołaj [COleClientItem:: UpdateLink](../../mfc/reference/coleclientitem-class.md#updatelink).

Argumenty tej funkcji zawierają informacje używane przez technologię OLE do identyfikowania urządzenia docelowego. Struktura [PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-printdlga) zawiera informacje używane przez system Windows do zainicjowania wspólnego okna dialogowego drukowania. Gdy użytkownik zamknie okno dialogowe, system Windows zwróci informacje o wyborach użytkownika w tej strukturze. `m_pd` element członkowski obiektu [CPrintDialog](../../mfc/reference/cprintdialog-class.md) jest strukturą `PRINTDLG`.

Aby uzyskać więcej informacji, zapoznaj się ze strukturą [PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-printdlga) w Windows SDK.

Aby uzyskać więcej informacji, zapoznaj się ze strukturą [DVTARGETDEVICE](/windows/win32/api/objidl/ns-objidl-dvtargetdevice) w Windows SDK.

##  <a name="coledocument"></a>COleDocument::COleDocument

Konstruuje obiekt `COleDocument`.

```
COleDocument();
```

##  <a name="enablecompoundfile"></a>COleDocument::EnableCompoundFile

Wywołaj tę funkcję, jeśli chcesz przechowywać dokument przy użyciu formatu pliku złożonego.

```
void EnableCompoundFile(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
Określa, czy obsługa plików złożonych jest włączona czy wyłączona.

### <a name="remarks"></a>Uwagi

Jest to również nazywane magazynem strukturalnym. Zazwyczaj wywoływana jest ta funkcja z konstruktora klasy pochodnej `COleDocument`. Aby uzyskać więcej informacji o dokumentach złożonych, zobacz [kontenery artykułów: pliki złożone](../../mfc/containers-compound-files.md)...

Jeśli ta funkcja członkowska nie zostanie wywołana, dokumenty będą przechowywane w formacie pliku bez struktury ("Flat").

Po włączeniu lub wyłączeniu obsługi plików złożonych dla dokumentu nie należy zmieniać tego ustawienia w okresie istnienia dokumentu.

##  <a name="getinplaceactiveitem"></a>COleDocument::GetInPlaceActiveItem

Wywołaj tę funkcję, aby pobrać element OLE, który jest aktualnie aktywowany w miejscu w oknie ramki zawierającym widok identyfikowany przez *pWnd*.

```
virtual COleClientItem* GetInPlaceActiveItem(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Wskaźnik do okna, w którym jest wyświetlany dokument kontenera.

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do pojedynczego, w miejscu aktywnego elementu OLE; Wartość NULL, jeśli w stanie "w miejscu aktywnym" nie ma obecnie elementu OLE.

##  <a name="getnextclientitem"></a>COleDocument::GetNextClientItem

Wielokrotnie Wywołaj tę funkcję, aby uzyskać dostęp do każdego elementu klienta w dokumencie.

```
COleClientItem* GetNextClientItem(POSITION& pos) const;
```

### <a name="parameters"></a>Parametry

*Terminal*<br/>
Odwołanie do wartości pozycji ustawionej przez poprzednie wywołanie do `GetNextClientItem`; wartość początkowa jest zwracana przez `GetStartPosition` funkcję członkowską.

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do następnego elementu klienta w dokumencie lub wartość NULL, jeśli nie ma więcej elementów klienta.

### <a name="remarks"></a>Uwagi

Po każdym wywołaniu wartość *pos* jest ustawiana dla następnego elementu w dokumencie, który może być lub nie jest elementem klienta.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#1](../../mfc/codesnippet/cpp/coledocument-class_1.cpp)]

##  <a name="getnextitem"></a>COleDocument::GetNextItem

Wielokrotnie Wywołaj tę funkcję, aby uzyskać dostęp do wszystkich elementów w dokumencie.

```
virtual CDocItem* GetNextItem(POSITION& pos) const;
```

### <a name="parameters"></a>Parametry

*Terminal*<br/>
Odwołanie do wartości pozycji ustawionej przez poprzednie wywołanie do `GetNextItem`; wartość początkowa jest zwracana przez `GetStartPosition` funkcję członkowską.

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do elementu dokumentu na określonej pozycji.

### <a name="remarks"></a>Uwagi

Po każdym wywołaniu wartość *pos* jest ustawiana na wartość pozycji następnego elementu w dokumencie. Jeśli pobrany element jest ostatnim elementem w dokumencie, Nowa wartość *pos* ma wartość null.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#2](../../mfc/codesnippet/cpp/coledocument-class_2.cpp)]

##  <a name="getnextserveritem"></a>COleDocument::GetNextServerItem

Wielokrotnie Wywołaj tę funkcję, aby uzyskać dostęp do wszystkich elementów serwera w dokumencie.

```
COleServerItem* GetNextServerItem(POSITION& pos) const;
```

### <a name="parameters"></a>Parametry

*Terminal*<br/>
Odwołanie do wartości pozycji ustawionej przez poprzednie wywołanie do `GetNextServerItem`; wartość początkowa jest zwracana przez `GetStartPosition` funkcję członkowską.

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do następnego elementu serwera w dokumencie lub wartość NULL, jeśli nie ma więcej elementów serwera.

### <a name="remarks"></a>Uwagi

Po każdym wywołaniu wartość *pos* jest ustawiana dla następnego elementu w dokumencie, który może być lub może nie być elementem serwera.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleServer#2](../../mfc/codesnippet/cpp/coledocument-class_3.cpp)]

##  <a name="getprimaryselecteditem"></a>COleDocument::GetPrimarySelectedItem

Wywoływane przez platformę, by pobrać aktualnie wybrany element OLE w określonym widoku.

```
virtual COleClientItem* GetPrimarySelectedItem(CView* pView);
```

### <a name="parameters"></a>Parametry

*pView*<br/>
Wskaźnik do aktywnego obiektu widoku wyświetlającego dokument.

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do pojedynczego, wybranego elementu OLE; Wartość NULL, jeśli nie wybrano żadnych elementów OLE lub wybrano więcej niż jeden element.

### <a name="remarks"></a>Uwagi

Domyślna implementacja przeszukuje listę zawartych elementów OLE dla pojedynczego zaznaczonego elementu i zwraca do niego wskaźnik. Jeśli nie wybrano żadnego elementu lub jeśli wybrano więcej niż jeden element, funkcja zwraca wartość NULL. Aby ta funkcja działała, należy zastąpić funkcję elementu członkowskiego `CView::IsSelected` w klasie widoku. Zastąp tę funkcję, jeśli masz własną metodę przechowywania zawartych elementów OLE.

##  <a name="getstartposition"></a>COleDocument::GetStartPosition

Wywołaj tę funkcję, aby pobrać pozycję pierwszego elementu w dokumencie.

```
virtual POSITION GetStartPosition() const;
```

### <a name="return-value"></a>Wartość zwrócona

Wartość pozycji, której można użyć, aby rozpocząć iterację elementów dokumentu; Wartość NULL, jeśli dokument nie zawiera żadnych elementów.

### <a name="remarks"></a>Uwagi

Przekaż wartość zwróconą do `GetNextItem`, `GetNextClientItem`lub `GetNextServerItem`.

##  <a name="hasblankitems"></a>COleDocument::HasBlankItems

Wywołaj tę funkcję, aby określić, czy dokument zawiera puste elementy.

```
BOOL HasBlankItems() const;
```

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli dokument zawiera puste elementy; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Pusty element to jeden, którego prostokąt jest pusty.

##  <a name="oneditchangeicon"></a>COleDocument::OnEditChangeIcon

Wyświetla okno dialogowe ikona zmiany OLE i zmienia ikonę reprezentującą aktualnie zaznaczony element OLE do ikony, którą użytkownik wybiera w oknie dialogowym.

```
afx_msg void OnEditChangeIcon();
```

### <a name="remarks"></a>Uwagi

`OnEditChangeIcon` tworzy i uruchamia okno dialogowe Zmień ikonę `COleChangeIconDialog`.

##  <a name="oneditconvert"></a>COleDocument::OnEditConvert

Wyświetla okno dialogowe Konwersja OLE i konwertuje lub aktywuje aktualnie zaznaczony element OLE zgodnie z wybranymi przez użytkownika w oknie dialogowym.

```
afx_msg void OnEditConvert();
```

### <a name="remarks"></a>Uwagi

`OnEditConvert` tworzy i uruchamia okno dialogowe konwersji `COleConvertDialog`.

Przykład konwersji polega na konwertowaniu dokumentu programu Microsoft Word do dokumentu programu WordPad.

##  <a name="oneditlinks"></a>COleDocument::OnEditLinks

Wyświetla okno dialogowe Edytowanie/łącza OLE.

```
afx_msg void OnEditLinks();
```

### <a name="remarks"></a>Uwagi

`OnEditLinks` tworzy i uruchamia okno dialogowe linki `COleLinksDialog`, które umożliwia użytkownikowi zmianę połączonych obiektów.

##  <a name="onfilesendmail"></a>COleDocument::OnFileSendMail

Wysyła komunikat za pośrednictwem zamieszkałego hosta poczty (jeśli istnieje) do dokumentu jako załącznik.

```
afx_msg void OnFileSendMail();
```

### <a name="remarks"></a>Uwagi

`OnFileSendMail` wywołania `OnSaveDocument` do serializacji (Zapisz) bez tytułu i modyfikacji dokumentów do pliku tymczasowego, który następnie jest wysyłany pocztą elektroniczną. Jeśli dokument nie został zmodyfikowany, plik tymczasowy nie jest wymagany; zostanie wysłany oryginalny. `OnFileSendMail` ładuje MAPI32. DLL, jeśli nie został jeszcze załadowany.

W przeciwieństwie do implementacji `OnFileSendMail` dla `CDocument`, ta funkcja obsługuje pliki złożone prawidłowo.

Aby uzyskać więcej informacji, zobacz [Tematy dotyczące MAPI](../../mfc/mapi.md) i [Obsługa MAPI w](../../mfc/mapi-support-in-mfc.md) artykułach MFC..

##  <a name="onshowviews"></a>COleDocument::OnShowViews

Struktura wywołuje tę funkcję po zmianie stanu widoczności dokumentu.

```
virtual void OnShowViews(BOOL bVisible);
```

### <a name="parameters"></a>Parametry

*bVisible*<br/>
Wskazuje, czy dokument stał się widoczny czy niewidoczny.

### <a name="remarks"></a>Uwagi

Domyślna wersja tej funkcji nic nie robi. Zastąp go, jeśli aplikacja musi wykonać jakiekolwiek specjalne przetwarzanie, gdy zmieni się widoczność dokumentu.

##  <a name="onupdateeditchangeicon"></a>COleDocument::OnUpdateEditChangeIcon

Wywoływane przez platformę, aby zaktualizować polecenie Zmień ikonę w menu Edycja.

```
afx_msg void OnUpdateEditChangeIcon(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parametry

*pCmdUI*<br/>
Wskaźnik do struktury `CCmdUI`, która reprezentuje menu, które wygenerowało polecenie Update. Procedura obsługi aktualizacji wywołuje funkcję członkowską `Enable` struktury `CCmdUI` za pomocą *pCmdUI* , aby zaktualizować interfejs użytkownika.

### <a name="remarks"></a>Uwagi

`OnUpdateEditChangeIcon` aktualizuje interfejs użytkownika polecenia w zależności od tego, czy w dokumencie istnieje prawidłowa ikona. Zastąp tę funkcję, aby zmienić zachowanie.

##  <a name="onupdateeditlinksmenu"></a>COleDocument::OnUpdateEditLinksMenu

Wywoływane przez platformę, aby zaktualizować polecenie Links w menu Edycja.

```
afx_msg void OnUpdateEditLinksMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parametry

*pCmdUI*<br/>
Wskaźnik do struktury `CCmdUI`, która reprezentuje menu, które wygenerowało polecenie Update. Procedura obsługi aktualizacji wywołuje funkcję członkowską `Enable` struktury `CCmdUI` za pomocą *pCmdUI* , aby zaktualizować interfejs użytkownika.

### <a name="remarks"></a>Uwagi

Począwszy od pierwszego elementu OLE w dokumencie, `OnUpdateEditLinksMenu` uzyskuje dostęp do każdego elementu, testuje, czy element jest łączem, a jeśli jest łączem, włącza polecenie Links. Zastąp tę funkcję, aby zmienić zachowanie.

##  <a name="onupdateobjectverbmenu"></a>COleDocument::OnUpdateObjectVerbMenu

Wywoływane przez platformę, aby zaktualizować polecenie *ObjectName* w menu Edycja i podmenu czasownik, do którego można uzyskać dostęp z obiektu *ObjectName* , gdzie *ObjectName* jest nazwą obiektów OLE osadzonych w dokumencie.

```
afx_msg void OnUpdateObjectVerbMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parametry

*pCmdUI*<br/>
Wskaźnik do struktury `CCmdUI`, która reprezentuje menu, które wygenerowało polecenie Update. Procedura obsługi aktualizacji wywołuje funkcję członkowską `Enable` struktury `CCmdUI` za pomocą *pCmdUI* , aby zaktualizować interfejs użytkownika.

### <a name="remarks"></a>Uwagi

`OnUpdateObjectVerbMenu` aktualizuje interfejs użytkownika polecenia *ObjectName* , w zależności od tego, czy w dokumencie istnieje prawidłowy obiekt. Jeśli obiekt istnieje, polecenie *ObjectName* w menu Edycja jest włączone. Po wybraniu tego polecenia menu zostanie wyświetlone podmenu zlecenie. Podmenu zlecenie zawiera wszystkie polecenia zleceń dostępne dla obiektu, takie jak Edycja, właściwości i tak dalej. Zastąp tę funkcję, aby zmienić zachowanie.

##  <a name="onupdatepastelinkmenu"></a>COleDocument::OnUpdatePasteLinkMenu

Wywoływane przez platformę, aby określić, czy połączony element OLE można wkleić ze schowka.

```
afx_msg void OnUpdatePasteLinkMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parametry

*pCmdUI*<br/>
Wskaźnik do struktury `CCmdUI`, która reprezentuje menu, które wygenerowało polecenie Update. Procedura obsługi aktualizacji wywołuje funkcję członkowską `Enable` struktury `CCmdUI` za pomocą *pCmdUI* , aby zaktualizować interfejs użytkownika.

### <a name="remarks"></a>Uwagi

Polecenie Wklej specjalne menu jest włączone lub wyłączone w zależności od tego, czy element można wkleić do dokumentu, czy nie.

##  <a name="onupdatepastemenu"></a>COleDocument::OnUpdatePasteMenu

Wywoływane przez platformę, aby określić, czy osadzony element OLE można wkleić ze schowka.

```
afx_msg void OnUpdatePasteMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parametry

*pCmdUI*<br/>
Wskaźnik do struktury `CCmdUI`, która reprezentuje menu, które wygenerowało polecenie Update. Procedura obsługi aktualizacji wywołuje funkcję członkowską `Enable` struktury `CCmdUI` za pomocą *pCmdUI* , aby zaktualizować interfejs użytkownika.

### <a name="remarks"></a>Uwagi

Polecenie Wklej menu i przycisk jest włączone lub wyłączone w zależności od tego, czy element można wkleić do dokumentu, czy nie.

##  <a name="removeitem"></a>COleDocument:: RemoveItem

Wywołaj tę funkcję, aby usunąć element z dokumentu.

```
virtual void RemoveItem(CDocItem* pItem);
```

### <a name="parameters"></a>Parametry

*pItem*<br/>
Wskaźnik na element dokumentu, który ma zostać usunięty.

### <a name="remarks"></a>Uwagi

Zazwyczaj nie trzeba wywoływać tej funkcji jawnie; jest on wywoływany przez destruktory dla `COleClientItem` i `COleServerItem`.

##  <a name="updatemodifiedflag"></a>COleDocument::UpdateModifiedFlag

Wywołaj tę funkcję, aby oznaczyć dokument jako zmodyfikowany, jeśli którykolwiek z zawartych w nim elementów OLE został zmodyfikowany.

```
virtual void UpdateModifiedFlag();
```

### <a name="remarks"></a>Uwagi

Dzięki temu platforma może monitować użytkownika o zapisanie dokumentu przed zamknięciem, nawet jeśli dane natywne w dokumencie nie zostały zmodyfikowane.

## <a name="see-also"></a>Zobacz też

[Przykładowy kontener MFC](../../overview/visual-cpp-samples.md)<br/>
[Przykład MFCBIND MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CDocument](../../mfc/reference/cdocument-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
