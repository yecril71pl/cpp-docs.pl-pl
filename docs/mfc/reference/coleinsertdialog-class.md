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
ms.openlocfilehash: a884f946b60be0567f39477f434db8efe041e393
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503928"
---
# <a name="coleinsertdialog-class"></a>Klasa COleInsertDialog

Używane na potrzeby okna dialogowego Wstawianie obiektu OLE.

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
|[COleInsertDialog:: GetItem](#createitem)|Tworzy element wybrany w oknie dialogowym.|
|[COleInsertDialog::D oModal](#domodal)|Wyświetla okno dialogowe OLE Wstaw obiekt.|
|[COleInsertDialog:: GetClassID](#getclassid)|Pobiera identyfikator CLSID skojarzony z wybranym elementem.|
|[COleInsertDialog::GetDrawAspect](#getdrawaspect)|Wskazuje, czy element ma być rysowany jako ikona.|
|[COleInsertDialog::GetIconicMetafile](#geticonicmetafile)|Pobiera uchwyt do metapliku skojarzonego z formą Icon tego elementu.|
|[COleInsertDialog:: getPathname](#getpathname)|Pobiera pełną ścieżkę do pliku wybranego w oknie dialogowym.|
|[COleInsertDialog:: GetSelectionType](#getselectiontype)|Pobiera typ wybranego obiektu.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[COleInsertDialog::m_io](#m_io)|Struktura typu OLEUIINSERTOBJECT, która kontroluje zachowanie okna dialogowego.|

## <a name="remarks"></a>Uwagi

Utwórz obiekt klasy `COleInsertDialog` , gdy chcesz wywołać to okno dialogowe. Po skonstruowaniu obiektu można użyć struktury m_io, aby zainicjować wartości lub Stany kontrolek w oknie dialogowym. [](#m_io) `COleInsertDialog` `m_io` Struktura jest typu OLEUIINSERTOBJECT. Aby uzyskać więcej informacji o używaniu tej klasy okna dialogowego, zobacz funkcja członkowska [DoModal](#domodal) .

> [!NOTE]
>  Kod kontenera wygenerowany przez Kreatora aplikacji używa tej klasy.

Aby uzyskać więcej informacji, zapoznaj się ze strukturą [OLEUIINSERTOBJECT](/windows/win32/api/oledlg/ns-oledlg-oleuiinsertobjectw) w Windows SDK.

Aby uzyskać więcej informacji dotyczących okien dialogowych specyficznych dla OLE, zobacz [okna dialogowe artykułu w OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleInsertDialog`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxodlgs. h

##  <a name="coleinsertdialog"></a>COleInsertDialog::COleInsertDialog

Ta funkcja tworzy tylko `COleInsertDialog` obiekt.

```
COleInsertDialog (
    DWORD dwFlags = IOF_SELECTCREATENEW,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*flagiDW*<br/>
Flaga tworzenia zawierająca dowolną liczbę następujących wartości, które mają zostać połączone przy użyciu operatora bitowego lub:

- IOF_SHOWHELP Określa, że przycisk Pomoc będzie wyświetlany po wywołaniu okna dialogowego.

- IOF_SELECTCREATENEW określa, że przycisk tworzenia nowego przycisku radiowego będzie wybierany początkowo po wywołaniu okna dialogowego. Jest to wartość domyślna i nie można jej używać z IOF_SELECTCREATEFROMFILE.

- IOF_SELECTCREATEFROMFILE określa, że przycisk radiowy Utwórz z pliku będzie wybierany początkowo po wywołaniu okna dialogowego. Nie można używać z IOF_SELECTCREATENEW.

- IOF_CHECKLINK określa, że pole wyboru link zostanie zaznaczone początkowo po wywołaniu okna dialogowego.

- IOF_DISABLELINK określa, że pole wyboru link zostanie wyłączone po wywołaniu okna dialogowego.

- IOF_CHECKDISPLAYASICON Określa, że pole wyboru Wyświetl jako ikonę zostanie zaznaczone na początku, zostanie wyświetlona bieżąca ikona, a przycisk Zmień ikonę zostanie włączony po wywołaniu okna dialogowego.

- IOF_VERIFYSERVERSEXIST określa, że okno dialogowe powinno sprawdzać poprawność klas, które dodaje do pola listy przez upewnienie się, że serwery określone w bazie danych rejestracji istnieją przed wyświetleniem okna dialogowego. Ustawienie tej flagi może znacząco obniżyć wydajność.

*pParentWnd*<br/>
Wskazuje obiekt nadrzędny lub właściciel (typu `CWnd`), do którego należy obiekt okna dialogowego. Jeśli ma wartość NULL, okno nadrzędne obiektu okna dialogowego jest ustawione na główne okno aplikacji.

### <a name="remarks"></a>Uwagi

Aby wyświetlić okno dialogowe, wywołaj funkcję [DoModal](#domodal) .

##  <a name="createitem"></a>COleInsertDialog:: GetItem

Wywołaj tę funkcję, aby utworzyć obiekt typu [COleClientItem](../../mfc/reference/coleclientitem-class.md) tylko wtedy, gdy [DoModal](#domodal) zwraca IDOK.

```
BOOL CreateItem(COleClientItem* pItem);
```

### <a name="parameters"></a>Parametry

*pItem*<br/>
Wskazuje element, który ma zostać utworzony.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli element został utworzony; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aby można było wywołać `COleClientItem` tę funkcję, należy przydzielić obiekt.

##  <a name="domodal"></a>COleInsertDialog::D oModal

Wywołaj tę funkcję, aby wyświetlić okno dialogowe OLE Wstaw obiekt.

```
virtual INT_PTR
    DoModal();

INT_PTR
    DoModal(DWORD  dwFlags);
```

### <a name="parameters"></a>Parametry

*flagiDW*<br/>
Jedna z następujących wartości:

`COleInsertDialog::DocObjectsOnly`Wstawia tylko DocObjects.

`COleInsertDialog::ControlsOnly`Wstawia tylko kontrolki ActiveX.

Zero wstawia nie DocObject ani kontrolki ActiveX. Ta wartość jest taka sama jak implementacja pierwszego prototypu wymienionego powyżej.

### <a name="return-value"></a>Wartość zwracana

Stan ukończenia dla okna dialogowego. Jedna z następujących wartości:

- IDOK, jeśli okno dialogowe zostało wyświetlone pomyślnie.

- IDCANCEL, jeśli użytkownik anulował okno dialogowe.

- IDABORT, jeśli wystąpił błąd. Jeśli IDABORT jest zwracany, wywołaj funkcję członkowską [COleDialog:: GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) , aby uzyskać więcej informacji na temat typu błędu, który wystąpił. Listę możliwych błędów można znaleźć w funkcji [OLEUIINSERTOBJECT](/windows/win32/api/oledlg/nf-oledlg-oleuiinsertobjectw) w Windows SDK.

### <a name="remarks"></a>Uwagi

Jeśli chcesz zainicjować różne kontrolki okna dialogowego, ustawiając elementy członkowskie struktury [m_io](#m_io) , należy to zrobić przed wywołaniem `DoModal`, ale po skonstruowaniu obiektu okna dialogowego.

Jeśli `DoModal` zwraca IDOK, można wywołać inne funkcje członkowskie, aby pobrać ustawienia lub dane wejściowe do okna dialogowego użytkownika.

##  <a name="getclassid"></a>COleInsertDialog:: GetClassID

Wywołaj tę funkcję, aby uzyskać identyfikator CLSID skojarzony z wybranym elementem tylko wtedy, gdy [DoModal](#domodal) zwraca IDOK i typ `COleInsertDialog::createNewItem`zaznaczenia to.

```
REFCLSID GetClassID() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca identyfikator CLSID skojarzony z wybranym elementem.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [klucz CLSID](/windows/win32/com/clsid-key-hklm) w Windows SDK.

##  <a name="getdrawaspect"></a>COleInsertDialog::GetDrawAspect

Wywołaj tę funkcję, aby określić, czy użytkownik wybrał opcję wyświetlania wybranego elementu jako ikonę.

```
DVASPECT GetDrawAspect() const;
```

### <a name="return-value"></a>Wartość zwracana

Metoda wymagana do renderowania obiektu.

- DVASPECT_CONTENT zwracany, jeśli pole wyboru Wyświetl jako ikonę nie zostało zaznaczone.

- DVASPECT_ICON zwracana, jeśli zaznaczono pole wyboru Wyświetl jako ikonę.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję tylko wtedy, gdy [DoModal](#domodal) zwraca IDOK.

Aby uzyskać więcej informacji na temat aspektów rysowania, zobacz [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) struktury danych w Windows SDK.

##  <a name="geticonicmetafile"></a>COleInsertDialog::GetIconicMetafile

Wywołaj tę funkcję, aby uzyskać uchwyt do metapliku zawierającego ikonę wybranego elementu.

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>Wartość zwracana

Uchwyt do metapliku zawierającego ikonę z ikoną wybranego elementu, jeśli pole wyboru Wyświetl jako ikonę zostało zaznaczone, gdy okno dialogowe zostało odrzucone, wybierając **przycisk OK**. w przeciwnym razie wartość NULL.

##  <a name="getpathname"></a>COleInsertDialog:: getPathname

Wywołaj tę funkcję, aby uzyskać pełną ścieżkę wybranego pliku tylko wtedy, gdy [DoModal](#domodal) zwraca IDOK i typ zaznaczenia to nie `COleInsertDialog::createNewItem`.

```
CString GetPathName() const;
```

### <a name="return-value"></a>Wartość zwracana

Pełna ścieżka do pliku wybranego w oknie dialogowym. Jeśli typ zaznaczenia to `createNewItem`, funkcja ta zwraca bez `CString` znaczenia w trybie wydania lub powoduje potwierdzenie w trybie debugowania.

##  <a name="getselectiontype"></a>COleInsertDialog:: GetSelectionType

Wywołaj tę funkcję, aby uzyskać typ wyboru wybrany podczas odrzucania okna dialogowego Wstawianie obiektu, wybierając **przycisk OK**.

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>Wartość zwracana

Typ dokonanego wyboru.

### <a name="remarks"></a>Uwagi

Wartości typu zwracanego są określane przez `Selection` typ wyliczeniowy zadeklarowany `COleInsertDialog` w klasie.

```
enum Selection {
    createNewItem,
    insertFromFile,
    linkToFile
    };
```

Poniżej przedstawiono krótkie opisy następujących wartości:

- `COleInsertDialog::createNewItem`Wybrano przycisk Create New Radio.

- `COleInsertDialog::insertFromFile`Wybrano przycisk radiowy Utwórz z pliku, a pole wyboru link nie zostało zaznaczone.

- `COleInsertDialog::linkToFile`Wybrano przycisk radiowy Utwórz z pliku, a pole wyboru link zostało zaznaczone.

##  <a name="m_io"></a>COleInsertDialog::m_io

Struktura typu OLEUIINSERTOBJECT używana do sterowania zachowaniem okna dialogowego Wstawianie obiektu.

```
OLEUIINSERTOBJECT m_io;
```

### <a name="remarks"></a>Uwagi

Elementy członkowskie tej struktury można modyfikować bezpośrednio lub za pomocą funkcji składowych.

Aby uzyskać więcej informacji, zapoznaj się ze strukturą [OLEUIINSERTOBJECT](/windows/win32/api/oledlg/ns-oledlg-oleuiinsertobjectw) w Windows SDK.

## <a name="see-also"></a>Zobacz także

[Przykład OCLIENT MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa COleDialog](../../mfc/reference/coledialog-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleDialog](../../mfc/reference/coledialog-class.md)
