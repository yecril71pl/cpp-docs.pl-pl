---
title: Klasa COleConvertDialog
ms.date: 11/04/2016
f1_keywords:
- COleConvertDialog
- AFXODLGS/COleConvertDialog
- AFXODLGS/COleConvertDialog::COleConvertDialog
- AFXODLGS/COleConvertDialog::DoConvert
- AFXODLGS/COleConvertDialog::DoModal
- AFXODLGS/COleConvertDialog::GetClassID
- AFXODLGS/COleConvertDialog::GetDrawAspect
- AFXODLGS/COleConvertDialog::GetIconicMetafile
- AFXODLGS/COleConvertDialog::GetSelectionType
- AFXODLGS/COleConvertDialog::m_cv
helpviewer_keywords:
- COleConvertDialog [MFC], COleConvertDialog
- COleConvertDialog [MFC], DoConvert
- COleConvertDialog [MFC], DoModal
- COleConvertDialog [MFC], GetClassID
- COleConvertDialog [MFC], GetDrawAspect
- COleConvertDialog [MFC], GetIconicMetafile
- COleConvertDialog [MFC], GetSelectionType
- COleConvertDialog [MFC], m_cv
ms.assetid: a7c57714-31e8-4b78-834d-8ddd1b856a1c
ms.openlocfilehash: ba57e756457fcffca806eeba7454ddf7bcf99d34
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504296"
---
# <a name="coleconvertdialog-class"></a>Klasa COleConvertDialog

Aby uzyskać więcej informacji, zapoznaj się ze strukturą [OLEUICONVERT](/windows/win32/api/oledlg/ns-oledlg-oleuiconvertw) w Windows SDK.

## <a name="syntax"></a>Składnia

```
class COleConvertDialog : public COleDialog
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleConvertDialog::COleConvertDialog](#coleconvertdialog)|Konstruuje `COleConvertDialog` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleConvertDialog::D oConvert](#doconvert)|Wykonuje konwersję określoną w oknie dialogowym.|
|[COleConvertDialog::D oModal](#domodal)|Wyświetla okno dialogowe Zmień element OLE.|
|[COleConvertDialog:: GetClassID](#getclassid)|Pobiera identyfikator CLSID skojarzony z wybranym elementem.|
|[COleConvertDialog::GetDrawAspect](#getdrawaspect)|Określa, czy element ma być rysowany jako ikona.|
|[COleConvertDialog::GetIconicMetafile](#geticonicmetafile)|Pobiera uchwyt do metapliku skojarzonego z formą Icon tego elementu.|
|[COleConvertDialog:: GetSelectionType](#getselectiontype)|Pobiera wybrany typ zaznaczenia.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[COleConvertDialog::m_cv](#m_cv)|Struktura, która kontroluje zachowanie okna dialogowego.|

## <a name="remarks"></a>Uwagi

> [!NOTE]
>  Kod kontenera wygenerowany przez Kreatora aplikacji używa tej klasy.

Aby uzyskać więcej informacji o oknach dialogowych specyficznych dla OLE, zobacz [okna dialogowe artykułu w OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleConvertDialog`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxodlgs. h

##  <a name="coleconvertdialog"></a>COleConvertDialog::COleConvertDialog

Tworzy tylko `COleConvertDialog` obiekt.

```
explicit COleConvertDialog (
    COleClientItem* pItem,
    DWORD dwFlags = CF_SELECTCONVERTTO,
    CLSID* pClassID = NULL,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*pItem*<br/>
Wskazuje element do przekonwertowania lub aktywowania.

*flagiDW*<br/>
Flaga tworzenia, która zawiera dowolną liczbę następujących wartości połączonych przy użyciu operatora bitowego lub:

- CF_SELECTCONVERTTO Określa, że przycisk Konwertuj do przycisku radiowego będzie wybierany początkowo po wywołaniu okna dialogowego. Domyślnie włączone.

- CF_SELECTACTIVATEAS określa, że przycisk opcji Aktywuj jako jest wybierany początkowo po wywołaniu okna dialogowego.

- CF_SETCONVERTDEFAULT określa, że Klasa, której CLSID jest określony przez `clsidConvertDefault` element członkowski `m_cv` struktury, będzie używana jako domyślny wybór w polu listy klas po wybraniu przycisku Konwertuj na przycisk radiowy.

- CF_SETACTIVATEDEFAULT określa, że Klasa, której CLSID jest określony przez `clsidActivateDefault` element członkowski `m_cv` struktury, będzie używana jako domyślny wybór w polu listy klas, gdy zostanie wybrany przycisk Aktywuj jako radio.

- CF_SHOWHELPBUTTON określa, że przycisk Pomoc będzie wyświetlany po wywołaniu okna dialogowego.

*pClassID*<br/>
Wskazuje identyfikator CLSID elementu, który ma zostać przekonwertowany lub aktywowany. Jeśli wartość jest równa NULL, zostanie użyty identyfikator CLSID skojarzony z *pItem* .

*pParentWnd*<br/>
Wskazuje obiekt nadrzędny lub właściciel (typu `CWnd`), do którego należy obiekt okna dialogowego. Jeśli ma wartość NULL, okno dialogowe nadrzędne okna dialogowego jest ustawione na główne okno aplikacji.

### <a name="remarks"></a>Uwagi

Aby wyświetlić okno dialogowe, wywołaj funkcję [DoModal](#domodal) .

Aby uzyskać więcej informacji, zobacz [klucz CLSID](/windows/win32/com/clsid-key-hklm) i struktura [OLEUICONVERT](/windows/win32/api/oledlg/ns-oledlg-oleuiconvertw) .

##  <a name="doconvert"></a>COleConvertDialog::D oConvert

Wywołaj tę funkcję po pomyślnym powrocie z [DoModal](#domodal), aby skonwertować lub uaktywnić obiekt typu [COleClientItem](../../mfc/reference/coleclientitem-class.md).

```
BOOL DoConvert(COleClientItem* pItem);
```

### <a name="parameters"></a>Parametry

*pItem*<br/>
Wskazuje element do przekonwertowania lub aktywowania. Nie może mieć wartości NULL.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Element jest konwertowany lub aktywowany zgodnie z informacjami wybranymi przez użytkownika w oknie dialogowym Konwertowanie.

##  <a name="domodal"></a>COleConvertDialog::D oModal

Wywołaj tę funkcję, aby wyświetlić okno dialogowe Konwersja OLE.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Wartość zwracana

Stan ukończenia dla okna dialogowego. Jedna z następujących wartości:

- IDOK, jeśli okno dialogowe zostało wyświetlone pomyślnie.

- IDCANCEL, jeśli użytkownik anulował okno dialogowe.

- IDABORT, jeśli wystąpił błąd. Jeśli IDABORT jest zwracany, wywołaj funkcję członkowską [COleDialog:: GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) , aby uzyskać więcej informacji na temat typu błędu, który wystąpił. Listę możliwych błędów można znaleźć w funkcji [OLEUICONVERT](/windows/win32/api/oledlg/nf-oledlg-oleuiconvertw) w Windows SDK.

### <a name="remarks"></a>Uwagi

Jeśli chcesz zainicjować różne kontrolki okna dialogowego, ustawiając elementy członkowskie struktury [m_cv](#m_cv) , należy to zrobić przed wywołaniem `DoModal`, ale po skonstruowaniu obiektu okna dialogowego.

Jeśli `DoModal` zwraca IDOK, można wywołać inne funkcje członkowskie, aby pobrać ustawienia lub informacje, które zostały wprowadzone przez użytkownika w oknie dialogowym.

##  <a name="getclassid"></a>COleConvertDialog:: GetClassID

Wywołaj tę funkcję, aby uzyskać identyfikator CLSID skojarzony z elementem wybranym przez użytkownika w oknie dialogowym Konwertowanie.

```
REFCLSID GetClassID() const;
```

### <a name="return-value"></a>Wartość zwracana

Identyfikator CLSID skojarzony z elementem, który został wybrany w oknie dialogowym Konwertowanie.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję tylko po [DoModal](#domodal) zwraca IDOK.

Aby uzyskać więcej informacji, zobacz [klucz CLSID](/windows/win32/com/clsid-key-hklm) w Windows SDK.

##  <a name="getdrawaspect"></a>COleConvertDialog::GetDrawAspect

Wywołaj tę funkcję, aby określić, czy użytkownik wybrał opcję wyświetlania wybranego elementu jako ikonę.

```
DVASPECT GetDrawAspect() const;
```

### <a name="return-value"></a>Wartość zwracana

Metoda wymagana do renderowania obiektu.

- DVASPECT_CONTENT zwracany, jeśli pole wyboru Wyświetl jako ikonę nie zostało zaznaczone.

- DVASPECT_ICON zwracana, jeśli zaznaczono pole wyboru Wyświetl jako ikonę.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję tylko po [DoModal](#domodal) zwraca IDOK.

Aby uzyskać więcej informacji na temat aspektów rysowania, zapoznaj się ze strukturą danych [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) w Windows SDK.

##  <a name="geticonicmetafile"></a>COleConvertDialog::GetIconicMetafile

Wywołaj tę funkcję, aby uzyskać uchwyt do metapliku zawierającego ikonę wybranego elementu.

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>Wartość zwracana

Uchwyt do metapliku zawierającego ikonę z ikoną wybranego elementu, jeśli pole wyboru Wyświetl jako ikonę zostało zaznaczone, gdy okno dialogowe zostało odrzucone, wybierając przycisk OK. w przeciwnym razie wartość NULL.

##  <a name="getselectiontype"></a>COleConvertDialog:: GetSelectionType

Wywołaj tę funkcję, aby określić typ konwersji wybranej w oknie dialogowym konwersja.

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>Wartość zwracana

Typ dokonanego wyboru.

### <a name="remarks"></a>Uwagi

Wartości typu zwracanego są określane przez `Selection` typ wyliczeniowy zadeklarowany `COleConvertDialog` w klasie.

```
enum Selection {
    noConversion,
    convertItem,
    activateAs
    };
```

Poniżej przedstawiono krótkie opisy następujących wartości:

- `COleConvertDialog::noConversion`Zwracany, jeśli okno dialogowe zostało anulowane lub użytkownik nie zaznaczył konwersji. Jeśli `COleConvertDialog::DoModal` zostanie zwrócony IDOK, istnieje możliwość, że użytkownik wybrał inną ikonę niż ta, która wcześniej została wybrana.

- `COleConvertDialog::convertItem`Zwracana, jeśli zaznaczono przycisk Konwertuj na opcję radiową, użytkownik wybrał inny element do przekonwertowania na `DoModal` i zwróci IDOK.

- `COleConvertDialog::activateAs`Zwracanego, jeśli zaznaczono przycisk radiowy Aktywuj jako, użytkownik wybrał inny element do aktywowania `DoModal` i zwrócił IDOK.

##  <a name="m_cv"></a>COleConvertDialog::m_cv

Struktura typu OLEUICONVERT używana do sterowania zachowaniem okna dialogowego Konwersja.

```
OLEUICONVERT m_cv;
```

### <a name="remarks"></a>Uwagi

Elementy członkowskie tej struktury można modyfikować bezpośrednio lub za pomocą funkcji składowych.

Aby uzyskać więcej informacji, zapoznaj się ze strukturą [OLEUICONVERT](/windows/win32/api/oledlg/ns-oledlg-oleuiconvertw) w Windows SDK.

## <a name="see-also"></a>Zobacz także

[Klasa COleDialog](../../mfc/reference/coledialog-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleDialog](../../mfc/reference/coledialog-class.md)
