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
ms.openlocfilehash: c99344c71d3f9789905516d661749b3668b57d50
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50546314"
---
# <a name="coleinsertdialog-class"></a>Klasa COleInsertDialog

Stosowane dla okna dialogowego OLE wprowadź obiekt.

## <a name="syntax"></a>Składnia

```
class COleInsertDialog : public COleDialog
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleInsertDialog::COleInsertDialog](#coleinsertdialog)|Konstruuje `COleInsertDialog` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleInsertDialog::CreateItem](#createitem)|Tworzy elementu wybranego w oknie dialogowym.|
|[COleInsertDialog::DoModal](#domodal)|Wyświetla okno dialogowe Wstawianie obiektu OLE.|
|[COleInsertDialog::GetClassID](#getclassid)|Pobiera identyfikator CLSID skojarzone z wybranym elementem.|
|[COleInsertDialog::GetDrawAspect](#getdrawaspect)|Informuje, czy do rysowania elementu jako ikona.|
|[COleInsertDialog::GetIconicMetafile](#geticonicmetafile)|Pobiera uchwyt do metaplik skojarzony z formularzem ikony tego elementu.|
|[COleInsertDialog::GetPathName](#getpathname)|Pobiera pełną ścieżkę do pliku, który został wybrany w oknie dialogowym.|
|[COleInsertDialog::GetSelectionType](#getselectiontype)|Pobiera typ wybrany obiekt.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[COleInsertDialog::m_io](#m_io)|Struktura typu OLEUIINSERTOBJECT kontrolujące zachowanie okna dialogowego.|

## <a name="remarks"></a>Uwagi

Utwórz obiekt klasy `COleInsertDialog` umożliwia wywołanie tego okna dialogowego. Po `COleInsertDialog` obiekt został skonstruowany, możesz użyć [m_io](#m_io) strukturę, aby zainicjować wartości lub stany formantów w oknie dialogowym. `m_io` Struktury jest typu OLEUIINSERTOBJECT. Aby uzyskać więcej informacji o korzystaniu z tej klasy okien dialogowych, zobacz [DoModal](#domodal) funkcja elementu członkowskiego.

> [!NOTE]
>  Kod kontenera generowane przez Kreatora aplikacji korzysta z tej klasy.

Aby uzyskać więcej informacji, zobacz [OLEUIINSERTOBJECT](/windows/desktop/api/oledlg/ns-oledlg-tagoleuiinsertobjecta) struktury w zestawie Windows SDK.

Aby uzyskać więcej informacji dotyczących okien dialogowych OLE specyficzne, zobacz artykuł [okna dialogowe w OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleInsertDialog`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxodlgs.h

##  <a name="coleinsertdialog"></a>  COleInsertDialog::COleInsertDialog

Ta funkcja tworzy tylko `COleInsertDialog` obiektu.

```
COleInsertDialog (
    DWORD dwFlags = IOF_SELECTCREATENEW,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*Flagidw*<br/>
Flaga tworzenia, który zawiera dowolną liczbę następujące wartości, które można połączyć za pomocą operatora bitowego OR:

- IOF_SHOWHELP Określa, że przycisk Pomoc, będą wyświetlane, gdy wywoływana jest okno dialogowe.

- IOF_SELECTCREATENEW Określa, że Utwórz nowy przycisk radiowy zostanie wybrany początkowo, gdy okno dialogowe jest wywoływana. To jest domyślnie i nie można używać z IOF_SELECTCREATEFROMFILE.

- IOF_SELECTCREATEFROMFILE Określa, że przycisk radiowy Utwórz z pliku będzie wybrać wstępnie, gdy okno dialogowe jest wywoływana. Nie można używać z IOF_SELECTCREATENEW.

- IOF_CHECKLINK Określa, że pole wyboru łącze będzie sprawdzany początkowo, gdy okno dialogowe jest wywoływana.

- IOF_DISABLELINK Określa, czy pole wyboru Link zostanie wyłączona po wywołaniu okno dialogowe.

- IOF_CHECKDISPLAYASICON Określa, że zostanie początkowo zaznaczone pole wyboru wyświetlana jako ikona, będzie wyświetlana ikona bieżącego i przycisk Zmień ikonę zostanie włączona, gdy wywoływana jest okno dialogowe.

- IOF_VERIFYSERVERSEXIST Określa, że okno dialogowe, należy zweryfikować klas, które dodaje do pola listy, zapewniając, że serwery określone w bazie danych rejestracji istnieć przed zostanie wyświetlone okno dialogowe. Ustawienie tej flagi znacząco obniżyć wydajność.

*pParentWnd*<br/>
Wskazuje na obiekt okna nadrzędnego lub właściciela (typu `CWnd`) do którego należy obiekt okna dialogowego. Jeśli ma wartość NULL, okno nadrzędne z obiektu okna dialogowego jest ustawiony na okna głównego aplikacji.

### <a name="remarks"></a>Uwagi

Aby wyświetlić okno dialogowe, należy wywołać [DoModal](#domodal) funkcji.

##  <a name="createitem"></a>  COleInsertDialog::CreateItem

Wywołaj tę funkcję, aby utworzyć obiekt typu [COleClientItem](../../mfc/reference/coleclientitem-class.md) tylko wtedy, gdy [DoModal](#domodal) zwraca IDOK.

```
BOOL CreateItem(COleClientItem* pItem);
```

### <a name="parameters"></a>Parametry

*pItem*<br/>
Wskazuje element, który ma zostać utworzony.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli element został utworzony; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Należy przydzielić `COleClientItem` obiekt przed wywołaniem tej funkcji.

##  <a name="domodal"></a>  COleInsertDialog::DoModal

Wywołaj tę funkcję, aby wyświetlić okna dialogowego OLE wprowadź obiekt.

```
virtual INT_PTR
    DoModal();

INT_PTR
    DoModal(DWORD  dwFlags);
```

### <a name="parameters"></a>Parametry

*Flagidw*<br/>
Jeden z następujących wartości:

`COleInsertDialog::DocObjectsOnly` Wstawia tylko DocObjects.

`COleInsertDialog::ControlsOnly` Wstawia tylko formantów ActiveX.

Zero Wstawia obiekt DocObject ani formantów ActiveX. Tej wartości powoduje w tej samej implementacji jako pierwszego prototypu wymienionych powyżej.

### <a name="return-value"></a>Wartość zwracana

Stan ukończenia dla okna dialogowego. Jeden z następujących wartości:

- IDOK, jeśli pomyślnie zostało wyświetlone okno dialogowe.

- IDCANCEL, jeśli użytkownik anulował okno dialogowe.

- IDABORT, jeśli wystąpił błąd. Jeśli zwracana jest IDABORT, wywołaj [COleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) funkcja elementu członkowskiego, aby uzyskać więcej informacji o typie błędu, który wystąpił. Aby uzyskać listę możliwych błędów, zobacz [OleUIInsertObject](/windows/desktop/api/oledlg/nf-oledlg-oleuiinsertobjecta) funkcji w zestawie Windows SDK.

### <a name="remarks"></a>Uwagi

Aby inicjowanie różne formanty okna dialogowego, ustawiając członkowie [m_io](#m_io) struktury, należy to zrobić przed wywołaniem `DoModal`, ale po jest konstruowany obiektu okna dialogowego.

Jeśli `DoModal` zwraca IDOK, może wywołać inny członek funkcje, które można pobrać ustawień lub wprowadzanie informacji w oknie dialogowym przez użytkownika.

##  <a name="getclassid"></a>  COleInsertDialog::GetClassID

Wywołaj tę funkcję, aby uzyskać identyfikator CLSID skojarzone z wybranych elementów tylko w przypadku [DoModal](#domodal) zwraca IDOK i typ wyboru to `COleInsertDialog::createNewItem`.

```
REFCLSID GetClassID() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca identyfikator CLSID skojarzonych z wybranym elementem.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [klucz identyfikator CLSID](/windows/desktop/com/clsid-key-hklm) w zestawie Windows SDK.

##  <a name="getdrawaspect"></a>  COleInsertDialog::GetDrawAspect

Wywołaj tę funkcję, aby określić, jeśli użytkownik wybrał opcję wyświetlania wybrany element jako ikona.

```
DVASPECT GetDrawAspect() const;
```

### <a name="return-value"></a>Wartość zwracana

Metoda wymagane do renderowania obiektu.

- DVASPECT_CONTENT zwracany, jeśli nie zaznaczono pola wyboru Wyświetl jako ikonę.

- DVASPECT_ICON zwracany, jeśli zaznaczono pole wyboru Wyświetl jako ikonę.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji tylko wtedy, gdy [DoModal](#domodal) zwraca IDOK.

Aby uzyskać więcej informacji na temat Rysowanie aspektu, zobacz [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) struktury danych w zestawie Windows SDK.

##  <a name="geticonicmetafile"></a>  COleInsertDialog::GetIconicMetafile

Wywołaj tę funkcję można pobrać uchwytu do metaplik, który zawiera ikony aspektów wybranego elementu.

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>Wartość zwracana

Dojście do Metaplik zawierający ikony aspektów wybranego elementu, jeśli była wyświetlana jako ikona okno wyboru zaznaczone, gdy okno dialogowe został odrzucony, wybierając **OK**; w przeciwnym razie wartość NULL.

##  <a name="getpathname"></a>  COleInsertDialog::GetPathName

Wywołaj tę funkcję, aby uzyskać pełną ścieżkę wybrany plik tylko wtedy, gdy [DoModal](#domodal) zwraca IDOK i typ wyboru nie jest `COleInsertDialog::createNewItem`.

```
CString GetPathName() const;
```

### <a name="return-value"></a>Wartość zwracana

Pełna ścieżka do pliku wybranego w oknie dialogowym. Jeśli typ wyboru `createNewItem`, funkcja zwraca wartość ta nie ma znaczenia `CString` w trybie wydania lub powoduje potwierdzenie, że w trybie debugowania.

##  <a name="getselectiontype"></a>  COleInsertDialog::GetSelectionType

Wywołaj tę funkcję można pobrać typu Wybór wybrany, gdy okno dialogowe Wstawianie obiektu został odrzucony, wybierając **OK**.

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>Wartość zwracana

Typ dokonano wyboru.

### <a name="remarks"></a>Uwagi

Wartości zwracanej są określane przez `Selection` typ wyliczeniowy zadeklarowany w `COleInsertDialog` klasy.

```
enum Selection {
    createNewItem,
    insertFromFile,
    linkToFile
    };
```

Wykonaj krótkie opisy tych wartości:

- `COleInsertDialog::createNewItem` Utwórz nowy przycisk radiowy został wybrany.

- `COleInsertDialog::insertFromFile` Został wybrany przycisk radiowy Utwórz z pliku, a nie zaznaczono pola wyboru łącze.

- `COleInsertDialog::linkToFile` Został wybrany przycisk radiowy Utwórz z pliku i zaznaczono pole wyboru łącze.

##  <a name="m_io"></a>  COleInsertDialog::m_io

Struktury typu OLEUIINSERTOBJECT używane do sterowania zachowaniem okno dialogowe Wstawianie obiektu.

```
OLEUIINSERTOBJECT m_io;
```

### <a name="remarks"></a>Uwagi

Elementy członkowskie tej struktury można zmodyfikować bezpośrednio lub za pośrednictwem funkcji elementów członkowskich.

Aby uzyskać więcej informacji, zobacz [OLEUIINSERTOBJECT](/windows/desktop/api/oledlg/ns-oledlg-tagoleuiinsertobjecta) struktury w zestawie Windows SDK.

## <a name="see-also"></a>Zobacz też

[Próbki MFC OCLIENT](../../visual-cpp-samples.md)<br/>
[Klasa COleDialog](../../mfc/reference/coledialog-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleDialog](../../mfc/reference/coledialog-class.md)
