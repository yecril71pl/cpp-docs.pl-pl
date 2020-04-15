---
title: Klasa COleInsertDialog
ms.date: 11/04/2016
f1_keywords:
- COleInsertDialog
- AFXODLGS/COleInsertDialog
- AFXODLGS/COleInsertDialog::COleInsertDialog
- AFXODLGS/COleInsertDialog::CreateItem
- AFXODLGS/COleInsertDialog::DoModal
- AFXODLGS/COleInsertDialog::GetClassID
- AFXODLGS/COleInsertDialog::GetDrawAspect
- AFXODLGS/COleInsertDialog::GetIconicMetafile
- AFXODLGS/COleInsertDialog::GetPathName
- AFXODLGS/COleInsertDialog::GetSelectionType
- AFXODLGS/COleInsertDialog::m_io
helpviewer_keywords:
- COleInsertDialog [MFC], COleInsertDialog
- COleInsertDialog [MFC], CreateItem
- COleInsertDialog [MFC], DoModal
- COleInsertDialog [MFC], GetClassID
- COleInsertDialog [MFC], GetDrawAspect
- COleInsertDialog [MFC], GetIconicMetafile
- COleInsertDialog [MFC], GetPathName
- COleInsertDialog [MFC], GetSelectionType
- COleInsertDialog [MFC], m_io
ms.assetid: a9ec610b-abde-431e-bd01-c40159a66dbb
ms.openlocfilehash: b5de4ff5daa80e1d8727444a4cfd275597e18c08
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374971"
---
# <a name="coleinsertdialog-class"></a>Klasa COleInsertDialog

Używane w oknie dialogowym Wstawianie obiektu OLE.

## <a name="syntax"></a>Składnia

```
class COleInsertDialog : public COleDialog
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleInsertDialog::COleInsertDialog](#coleinsertdialog)|Konstruuje `COleInsertDialog` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleInsertDialog::CreateItem](#createitem)|Tworzy element zaznaczony w oknie dialogowym.|
|[COleInsertDialog::DoModal](#domodal)|Wyświetla okno dialogowe Wstawianie obiektu OLE.|
|[COleInsertDialog::GetClassID](#getclassid)|Pobiera CLSID skojarzone z wybranym elementem.|
|[COleInsertDialog::GetDrawAspect](#getdrawaspect)|Określa, czy element ma być rysowany jako ikona.|
|[COleInsertDialog::GetIconicMetafile](#geticonicmetafile)|Pobiera uchwyt do metapliku skojarzonego z ikoniczną formą tego elementu.|
|[COleInsertDialog::GetPathName](#getpathname)|Pobiera pełną ścieżkę do pliku wybranego w oknie dialogowym.|
|[COleInsertDialog::GetSelectionType](#getselectiontype)|Pobiera typ wybranego obiektu.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[COleInsertDialog::m_io](#m_io)|Struktura typu OLEUIINSERTOBJECT, która kontroluje zachowanie okna dialogowego.|

## <a name="remarks"></a>Uwagi

Utwórz obiekt `COleInsertDialog` klasy, jeśli chcesz wywołać to okno dialogowe. Po `COleInsertDialog` skonstruowaniu obiektu można użyć struktury [m_io](#m_io) do zainicjowania wartości lub stanów formantów w oknie dialogowym. Struktura `m_io` jest typu OLEUIINSERTOBJECT. Aby uzyskać więcej informacji na temat korzystania z tej klasy okna dialogowego, zobacz Funkcję elementu członkowskiego [DoModal.](#domodal)

> [!NOTE]
> Kod kontenera generowany przez Kreatora aplikacji używa tej klasy.

Aby uzyskać więcej informacji, zobacz [OLEUIINSERTOBJECT](/windows/win32/api/oledlg/ns-oledlg-oleuiinsertobjectw) struktury w windows SDK.

Aby uzyskać więcej informacji dotyczących okien dialogowych specyficznych dla ole, zobacz [okna dialogowe](../../mfc/dialog-boxes-in-ole.md)artykułu OLE .

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cdialog](../../mfc/reference/cdialog-class.md)

[CKlogialny](../../mfc/reference/ccommondialog-class.md)

[COleDialog (Polski)](../../mfc/reference/coledialog-class.md)

`COleInsertDialog`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxodlgs.h

## <a name="coleinsertdialogcoleinsertdialog"></a><a name="coleinsertdialog"></a>COleInsertDialog::COleInsertDialog

Ta funkcja konstruuje tylko `COleInsertDialog` obiekt.

```
COleInsertDialog (
    DWORD dwFlags = IOF_SELECTCREATENEW,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*Dwflags*<br/>
Flaga tworzenia zawierająca dowolną liczbę następujących wartości, które mają być łączone za pomocą operatora bitowego OR:

- IOF_SHOWHELP Określa, że przycisk Pomoc będzie wyświetlany po wywołaniu okna dialogowego.

- IOF_SELECTCREATENEW Określa, że przycisk opcji Utwórz nowy zostanie wybrany początkowo po wywołaniu okna dialogowego. Jest to wartość domyślna i nie można jej używać z IOF_SELECTCREATEFROMFILE.

- IOF_SELECTCREATEFROMFILE Określa, że przycisk opcji Utwórz z pliku zostanie wybrany początkowo po wywołaniu okna dialogowego. Nie można używać z IOF_SELECTCREATENEW.

- IOF_CHECKLINK Określa, że pole wyboru Łącze zostanie sprawdzone początkowo, gdy zostanie wywołane okno dialogowe.

- IOF_DISABLELINK Określa, że pole wyboru Łącze zostanie wyłączone, gdy zostanie wywołane okno dialogowe.

- IOF_CHECKDISPLAYASICON Określa, że pole wyboru Wyświetl jako ikona zostanie początkowo zaznaczone, zostanie wyświetlona bieżąca ikona, a przycisk Zmień ikonę zostanie włączony, gdy zostanie wywołane okno dialogowe.

- IOF_VERIFYSERVERSEXIST Określa, że okno dialogowe powinno sprawdzać poprawność klas, które dodaje do pola listy, upewniając się, że serwery określone w bazie danych rejestracji istnieją przed wyświetleniem okna dialogowego. Ustawienie tej flagi może znacznie pogorszyć wydajność.

*pParentWnd*<br/>
Wskazuje obiekt okna nadrzędnego lub `CWnd`właściciela (typu), do którego należy obiekt okna dialogowego. Jeśli jest null, okno nadrzędne obiektu okna dialogowego jest ustawiona na główne okno aplikacji.

### <a name="remarks"></a>Uwagi

Aby wyświetlić okno dialogowe, należy wywołać funkcję [DoModal.](#domodal)

## <a name="coleinsertdialogcreateitem"></a><a name="createitem"></a>COleInsertDialog::CreateItem

Wywołanie tej funkcji, aby utworzyć obiekt typu [COleClientItem](../../mfc/reference/coleclientitem-class.md) tylko [wtedy, gdy DoModal](#domodal) zwraca IDOK.

```
BOOL CreateItem(COleClientItem* pItem);
```

### <a name="parameters"></a>Parametry

*pItem (własówce)*<br/>
Wskazuje element, który ma zostać utworzony.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli element został utworzony; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Przed wywołaniem `COleClientItem` tej funkcji należy przydzielić obiekt.

## <a name="coleinsertdialogdomodal"></a><a name="domodal"></a>COleInsertDialog::DoModal

Wywołanie tej funkcji powoduje wyświetlenie okna dialogowego Wstawianie obiektu OLE.

```
virtual INT_PTR
    DoModal();

INT_PTR
    DoModal(DWORD  dwFlags);
```

### <a name="parameters"></a>Parametry

*Dwflags*<br/>
Jedna z następujących wartości:

`COleInsertDialog::DocObjectsOnly`wstawia tylko docObjects.

`COleInsertDialog::ControlsOnly`wstawia tylko formanty ActiveX.

Zero nie wstawia ani DocObject ani ActiveX kontrolki. Ta wartość powoduje taką samą implementację jak pierwszy prototyp wymienionych powyżej.

### <a name="return-value"></a>Wartość zwracana

Stan ukończenia okna dialogowego. Jedna z następujących wartości:

- IDOK, jeśli okno dialogowe zostało pomyślnie wyświetlone.

- IDCANCEL, jeśli użytkownik anulował okno dialogowe.

- IDABORT, jeśli wystąpił błąd. Jeśli idabort jest zwracany, wywołać [COleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) funkcji elementu członkowskiego, aby uzyskać więcej informacji na temat typu błędu, który wystąpił. Aby uzyskać listę możliwych błędów, zobacz [OleUIInsertObject](/windows/win32/api/oledlg/nf-oledlg-oleuiinsertobjectw) funkcji w zestawie Windows SDK.

### <a name="remarks"></a>Uwagi

Jeśli chcesz zainicjować różne formanty okna dialogowego, ustawiając elementy członkowskie [m_io](#m_io) `DoModal`struktury, należy to zrobić przed wywołaniem , ale po skonstruowaniu obiektu okna dialogowego.

Jeśli `DoModal` zwraca IDOK, można wywołać inne funkcje członkowskie, aby pobrać ustawienia lub informacje wprowadzone do okna dialogowego przez użytkownika.

## <a name="coleinsertdialoggetclassid"></a><a name="getclassid"></a>COleInsertDialog::GetClassID

Wywołanie tej funkcji, aby uzyskać CLSID skojarzone z wybranym elementem tylko `COleInsertDialog::createNewItem` [wtedy, gdy DoModal](#domodal) zwraca IDOK i typ zaznaczenia jest .

```
REFCLSID GetClassID() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca identyfikator CLSID skojarzony z zaznaczonym elementem.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [ClsID klucz](/windows/win32/com/clsid-key-hklm) w windows SDK.

## <a name="coleinsertdialoggetdrawaspect"></a><a name="getdrawaspect"></a>COleInsertDialog::GetDrawAspect

Wywołanie tej funkcji, aby ustalić, czy użytkownik zdecydował się wyświetlić wybrany element jako ikonę.

```
DVASPECT GetDrawAspect() const;
```

### <a name="return-value"></a>Wartość zwracana

Metoda potrzebna do renderowania obiektu.

- DVASPECT_CONTENT Zwrócony, jeśli pole wyboru Wyświetl jako ikonę nie zostało zaznaczone.

- DVASPECT_ICON zwrócone, jeśli zaznaczono pole wyboru Wyświetl jako ikonę.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji tylko [wtedy, gdy DoModal](#domodal) zwraca IDOK.

Aby uzyskać więcej informacji na temat aspektu rysowania, zobacz struktura danych [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) w zestaw windows SDK.

## <a name="coleinsertdialoggeticonicmetafile"></a><a name="geticonicmetafile"></a>COleInsertDialog::GetIconicMetafile

Wywołanie tej funkcji, aby uzyskać uchwyt do metapliku, który zawiera kultowy aspekt wybranego elementu.

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>Wartość zwracana

Uchwyt do metapliku zawierającego kultowy aspekt wybranego elementu, jeśli pole wyboru Wyświetl jako ikonę zostało zaznaczone, gdy okno dialogowe zostało odrzucone, wybierając **przycisk OK**; w przeciwnym razie NULL.

## <a name="coleinsertdialoggetpathname"></a><a name="getpathname"></a>COleInsertDialog::GetPathName

Wywołanie tej funkcji, aby uzyskać pełną ścieżkę wybranego pliku tylko wtedy, gdy `COleInsertDialog::createNewItem` [DoModal](#domodal) zwraca IDOK i typ zaznaczenia nie jest .

```
CString GetPathName() const;
```

### <a name="return-value"></a>Wartość zwracana

Pełna ścieżka do pliku zaznaczonego w oknie dialogowym. Jeśli typem `createNewItem`zaznaczenia jest , `CString` ta funkcja zwraca bezsensowne w trybie wydania lub powoduje potwierdzenia w trybie debugowania.

## <a name="coleinsertdialoggetselectiontype"></a><a name="getselectiontype"></a>COleInsertDialog::GetSelectionType

Wywołanie tej funkcji w celu uzyskania wybranego typu zaznaczenia po odrzuceniu okna dialogowego Wstawianie obiektu przez **wybranie przycisku OK**.

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>Wartość zwracana

Typ dokonanego wyboru.

### <a name="remarks"></a>Uwagi

Wartości typu zwracane są `Selection` określone przez typ wyliczenia zadeklarowany w `COleInsertDialog` klasie.

```
enum Selection {
    createNewItem,
    insertFromFile,
    linkToFile
    };
```

Krótkie opisy tych wartości są następujące:

- `COleInsertDialog::createNewItem`Wybrano przycisk opcji Utwórz nowy.

- `COleInsertDialog::insertFromFile`Wybrano przycisk opcji Utwórz z pliku, a pole wyboru Łącze nie zostało zaznaczone.

- `COleInsertDialog::linkToFile`Wybrano przycisk opcji Utwórz z pliku i zaznaczono pole wyboru Łącze.

## <a name="coleinsertdialogm_io"></a><a name="m_io"></a>COleInsertDialog::m_io

Struktura typu OLEUIINSERTOBJECT używana do kontrolowania zachowania okna dialogowego Wstawianie obiektu.

```
OLEUIINSERTOBJECT m_io;
```

### <a name="remarks"></a>Uwagi

Elementy członkowskie tej struktury mogą być modyfikowane bezpośrednio lub za pośrednictwem funkcji członkowskich.

Aby uzyskać więcej informacji, zobacz [OLEUIINSERTOBJECT](/windows/win32/api/oledlg/ns-oledlg-oleuiinsertobjectw) struktury w windows SDK.

## <a name="see-also"></a>Zobacz też

[Próbka MFC OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[Klasa COleDialog](../../mfc/reference/coledialog-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleDialog](../../mfc/reference/coledialog-class.md)
