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
ms.openlocfilehash: 6d6690b8d06df29ce9fcd323eb8724009ee3cca9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366168"
---
# <a name="coleconvertdialog-class"></a>Klasa COleConvertDialog

Aby uzyskać więcej informacji, zobacz [STRUKTURĘ OLEUICONVERT](/windows/win32/api/oledlg/ns-oledlg-oleuiconvertw) w windows SDK.

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
|[COleConvertDialog::DoConvert](#doconvert)|Wykonuje konwersję określoną w oknie dialogowym.|
|[COleConvertDialog::DoModal](#domodal)|Wyświetla okno dialogowe Zmienianie elementu OLE.|
|[COleConvertDialog::GetClassID](#getclassid)|Pobiera CLSID skojarzone z wybranym elementem.|
|[COleConvertDialog::GetDrawAspect](#getdrawaspect)|Określa, czy element ma być rysowany jako ikona.|
|[COleConvertDialog::GetIconicMetafile](#geticonicmetafile)|Pobiera uchwyt do metapliku skojarzonego z ikoniczną formą tego elementu.|
|[COleConvertDialog::GetSelectionType](#getselectiontype)|Pobiera typ wybranego wyboru.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[COleConvertDialog::m_cv](#m_cv)|Struktura, która kontroluje zachowanie okna dialogowego.|

## <a name="remarks"></a>Uwagi

> [!NOTE]
> Kod kontenera generowany przez Kreatora aplikacji używa tej klasy.

Aby uzyskać więcej informacji na temat okien dialogowych specyficznych dla ole, zobacz [artykuł Okna dialogowe w ole](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cdialog](../../mfc/reference/cdialog-class.md)

[CKlogialny](../../mfc/reference/ccommondialog-class.md)

[COleDialog (Polski)](../../mfc/reference/coledialog-class.md)

`COleConvertDialog`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxodlgs.h

## <a name="coleconvertdialogcoleconvertdialog"></a><a name="coleconvertdialog"></a>COleConvertDialog::COleConvertDialog

Konstruuje `COleConvertDialog` tylko obiekt.

```
explicit COleConvertDialog (
    COleClientItem* pItem,
    DWORD dwFlags = CF_SELECTCONVERTTO,
    CLSID* pClassID = NULL,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*pItem (własówce)*<br/>
Wskazuje przedmiot do konwersji lub aktywacji.

*Dwflags*<br/>
Flaga tworzenia, która zawiera dowolną liczbę następujących wartości połączonych za pomocą operatora bitowego lub operatora:

- CF_SELECTCONVERTTO Określa, że przycisk opcji Konwertuj na zostanie wybrany początkowo po wywołaniu okna dialogowego. Domyślnie włączone.

- CF_SELECTACTIVATEAS Określa, że przycisk opcji Aktywuj jako zostanie wybrany początkowo po wywołaniu okna dialogowego.

- CF_SETCONVERTDEFAULT Określa, że klasa, której identyfikator CLSID jest określony przez `clsidConvertDefault` element `m_cv` członkowski struktury, będzie używana jako domyślny wybór w polu listy klasy po wybraniu przycisku opcji Konwertuj na.

- CF_SETACTIVATEDEFAULT Określa, że klasa, której identyfikator CLSID jest określony przez `clsidActivateDefault` element `m_cv` członkowski struktury, będzie używana jako domyślny wybór w polu listy klas po wybraniu przycisku opcji Aktywuj jako.

- CF_SHOWHELPBUTTON Określa, że przycisk Pomoc będzie wyświetlany po wywołaniu okna dialogowego.

*Pclassid*<br/>
Wskazuje identyfikator CLSID elementu, który ma zostać przekonwertowany lub aktywowany. Jeśli null, CLSID skojarzone z *pItem* będą używane.

*pParentWnd*<br/>
Wskazuje obiekt okna nadrzędnego lub `CWnd`właściciela (typu), do którego należy obiekt okna dialogowego. Jeśli jest null, okno nadrzędne okna dialogowego jest ustawiona na główne okno aplikacji.

### <a name="remarks"></a>Uwagi

Aby wyświetlić okno dialogowe, należy wywołać funkcję [DoModal.](#domodal)

Aby uzyskać więcej informacji, zobacz [CLSID key](/windows/win32/com/clsid-key-hklm) i [OLEUICONVERT](/windows/win32/api/oledlg/ns-oledlg-oleuiconvertw) struktury.

## <a name="coleconvertdialogdoconvert"></a><a name="doconvert"></a>COleConvertDialog::DoConvert

Wywołanie tej funkcji, po pomyślnym powrocie z [DoModal](#domodal), albo do konwersji lub aktywować obiekt typu [COleClientItem](../../mfc/reference/coleclientitem-class.md).

```
BOOL DoConvert(COleClientItem* pItem);
```

### <a name="parameters"></a>Parametry

*pItem (własówce)*<br/>
Wskazuje przedmiot do konwersji lub aktywacji. Nie może być null.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Element jest konwertowany lub aktywowany zgodnie z informacjami wybranymi przez użytkownika w oknie dialogowym Konwertowanie.

## <a name="coleconvertdialogdomodal"></a><a name="domodal"></a>COleConvertDialog::DoModal

Wywołanie tej funkcji w celu wyświetlenia okna dialogowego Konwertowanie OLE.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Wartość zwracana

Stan ukończenia okna dialogowego. Jedna z następujących wartości:

- IDOK, jeśli okno dialogowe zostało pomyślnie wyświetlone.

- IDCANCEL, jeśli użytkownik anulował okno dialogowe.

- IDABORT, jeśli wystąpił błąd. Jeśli idabort jest zwracany, wywołać [COleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) funkcji elementu członkowskiego, aby uzyskać więcej informacji na temat typu błędu, który wystąpił. Aby uzyskać listę możliwych błędów, zobacz [OleUIKonwertowanie](/windows/win32/api/oledlg/nf-oledlg-oleuiconvertw) funkcji w zestawie Windows SDK.

### <a name="remarks"></a>Uwagi

Jeśli chcesz zainicjować różne formanty okna dialogowego, ustawiając elementy członkowskie [m_cv](#m_cv) `DoModal`struktury, należy to zrobić przed wywołaniem , ale po skonstruowaniu obiektu okna dialogowego.

Jeśli `DoModal` zwraca IDOK, można wywołać inne funkcje członkowskie, aby pobrać ustawienia lub informacje, które zostały wprowadzone przez użytkownika w oknie dialogowym.

## <a name="coleconvertdialoggetclassid"></a><a name="getclassid"></a>COleConvertDialog::GetClassID

Wywołanie tej funkcji, aby uzyskać CLSID skojarzone z elementem wybranym przez użytkownika w oknie dialogowym Konwertowanie.

```
REFCLSID GetClassID() const;
```

### <a name="return-value"></a>Wartość zwracana

Identyfikator CLSID skojarzony z elementem wybranym w oknie dialogowym Konwertowanie.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji tylko po [DoModal](#domodal) zwraca IDOK.

Aby uzyskać więcej informacji, zobacz [ClsID klucz](/windows/win32/com/clsid-key-hklm) w windows SDK.

## <a name="coleconvertdialoggetdrawaspect"></a><a name="getdrawaspect"></a>COleConvertDialog::GetDrawAspect

Wywołanie tej funkcji, aby ustalić, czy użytkownik wybrał wyświetlanie wybranego elementu jako ikonę.

```
DVASPECT GetDrawAspect() const;
```

### <a name="return-value"></a>Wartość zwracana

Metoda potrzebna do renderowania obiektu.

- DVASPECT_CONTENT Zwrócony, jeśli pole wyboru Wyświetl jako ikonę nie zostało zaznaczone.

- DVASPECT_ICON zwrócone, jeśli zaznaczono pole wyboru Wyświetl jako ikonę.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji tylko po [DoModal](#domodal) zwraca IDOK.

Aby uzyskać więcej informacji na temat aspektu rysowania, zobacz strukturę danych [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) w zestaw windows SDK.

## <a name="coleconvertdialoggeticonicmetafile"></a><a name="geticonicmetafile"></a>COleConvertDialog::GetIconicMetafile

Wywołanie tej funkcji, aby uzyskać uchwyt do metapliku, który zawiera kultowy aspekt wybranego elementu.

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>Wartość zwracana

Uchwyt do metapliku zawierającego kultowy aspekt wybranego elementu, jeśli pole wyboru Wyświetl jako ikonę zostało zaznaczone, gdy okno dialogowe zostało odrzucone, wybierając przycisk OK; w przeciwnym razie NULL.

## <a name="coleconvertdialoggetselectiontype"></a><a name="getselectiontype"></a>COleConvertDialog::GetSelectionType

Wywołanie tej funkcji w celu określenia typu konwersji wybranego w oknie dialogowym Konwertowanie.

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>Wartość zwracana

Typ dokonanego wyboru.

### <a name="remarks"></a>Uwagi

Wartości typu zwracane są `Selection` określone przez typ wyliczenia zadeklarowany w `COleConvertDialog` klasie.

```
enum Selection {
    noConversion,
    convertItem,
    activateAs
    };
```

Krótkie opisy tych wartości są następujące:

- `COleConvertDialog::noConversion`Zwracane, jeśli okno dialogowe zostało anulowane lub użytkownik nie wybrał konwersji. Jeśli `COleConvertDialog::DoModal` zwrócony IDOK, jest możliwe, że użytkownik wybrał inną ikonę niż poprzednio zaznaczone.

- `COleConvertDialog::convertItem`Zwrócony, jeśli przycisk opcji Konwertuj na został zaznaczony, `DoModal` użytkownik wybrał inny element do konwersji i zwrócił IDOK.

- `COleConvertDialog::activateAs`Zwrócony, jeśli zaznaczono przycisk opcji Aktywuj jako, użytkownik wybrał `DoModal` inny element do aktywacji i zwrócił IDOK.

## <a name="coleconvertdialogm_cv"></a><a name="m_cv"></a>COleConvertDialog::m_cv

Struktura typu OLEUICONVERT używana do kontrolowania zachowania okna dialogowego Konwertowanie.

```
OLEUICONVERT m_cv;
```

### <a name="remarks"></a>Uwagi

Elementy członkowskie tej struktury mogą być modyfikowane bezpośrednio lub za pośrednictwem funkcji członkowskich.

Aby uzyskać więcej informacji, zobacz [STRUKTURĘ OLEUICONVERT](/windows/win32/api/oledlg/ns-oledlg-oleuiconvertw) w windows SDK.

## <a name="see-also"></a>Zobacz też

[Klasa COleDialog](../../mfc/reference/coledialog-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleDialog](../../mfc/reference/coledialog-class.md)
