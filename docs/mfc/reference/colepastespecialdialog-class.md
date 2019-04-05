---
title: Klasa COlePasteSpecialDialog
ms.date: 11/04/2016
f1_keywords:
- COlePasteSpecialDialog
- AFXODLGS/COlePasteSpecialDialog
- AFXODLGS/COlePasteSpecialDialog::COlePasteSpecialDialog
- AFXODLGS/COlePasteSpecialDialog::AddFormat
- AFXODLGS/COlePasteSpecialDialog::AddLinkEntry
- AFXODLGS/COlePasteSpecialDialog::AddStandardFormats
- AFXODLGS/COlePasteSpecialDialog::CreateItem
- AFXODLGS/COlePasteSpecialDialog::DoModal
- AFXODLGS/COlePasteSpecialDialog::GetDrawAspect
- AFXODLGS/COlePasteSpecialDialog::GetIconicMetafile
- AFXODLGS/COlePasteSpecialDialog::GetPasteIndex
- AFXODLGS/COlePasteSpecialDialog::GetSelectionType
- AFXODLGS/COlePasteSpecialDialog::m_ps
helpviewer_keywords:
- COlePasteSpecialDialog [MFC], COlePasteSpecialDialog
- COlePasteSpecialDialog [MFC], AddFormat
- COlePasteSpecialDialog [MFC], AddLinkEntry
- COlePasteSpecialDialog [MFC], AddStandardFormats
- COlePasteSpecialDialog [MFC], CreateItem
- COlePasteSpecialDialog [MFC], DoModal
- COlePasteSpecialDialog [MFC], GetDrawAspect
- COlePasteSpecialDialog [MFC], GetIconicMetafile
- COlePasteSpecialDialog [MFC], GetPasteIndex
- COlePasteSpecialDialog [MFC], GetSelectionType
- COlePasteSpecialDialog [MFC], m_ps
ms.assetid: 0e82ef9a-9bbe-457e-8240-42c86a0534f7
ms.openlocfilehash: 9c31ed6f82f4280206bf233999fac74981636db3
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "58776911"
---
# <a name="colepastespecialdialog-class"></a>Klasa COlePasteSpecialDialog

Stosowane dla okna dialogowego OLE Wklej specjalne.

## <a name="syntax"></a>Składnia

```
class COlePasteSpecialDialog : public COleDialog
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COlePasteSpecialDialog::COlePasteSpecialDialog](#colepastespecialdialog)|Konstruuje `COlePasteSpecialDialog` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COlePasteSpecialDialog::AddFormat](#addformat)|Dodaje formatów niestandardowych do listy formatów, które można wkleić aplikacji.|
|[COlePasteSpecialDialog::AddLinkEntry](#addlinkentry)|Dodaje nowy wpis do listy obsługiwanych formatów Schowka.|
|[COlePasteSpecialDialog::AddStandardFormats](#addstandardformats)|Dodaje CF_METAFILEPICT CF_BITMAP, CF_DIB, i opcjonalnie CF_LINKSOURCE do listy formatów aplikacji można wkleić.|
|[COlePasteSpecialDialog::CreateItem](#createitem)|Tworzy element w dokumencie kontenera przy użyciu określonego formatu.|
|[COlePasteSpecialDialog::DoModal](#domodal)|Wyświetla okno dialogowe w OLE Wklej specjalne.|
|[COlePasteSpecialDialog::GetDrawAspect](#getdrawaspect)|Informuje, czy do rysowania elementu jako ikony, czy nie.|
|[COlePasteSpecialDialog::GetIconicMetafile](#geticonicmetafile)|Pobiera uchwyt do metaplik skojarzony z formularzem ikony tego elementu.|
|[COlePasteSpecialDialog::GetPasteIndex](#getpasteindex)|Pobiera indeks Opcje wklejania dostępne, który został wybrany przez użytkownika.|
|[COlePasteSpecialDialog::GetSelectionType](#getselectiontype)|Pobiera typ wyboru dokonanego.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[COlePasteSpecialDialog::m_ps](#m_ps)|Struktura typu OLEUIPASTESPECIAL kontrolujące funkcji okna dialogowego.|

## <a name="remarks"></a>Uwagi

Utwórz obiekt klasy `COlePasteSpecialDialog` umożliwia wywołanie tego okna dialogowego. Po `COlePasteSpecialDialog` obiekt został skonstruowany, możesz użyć [AddFormat](#addformat) i [AddStandardFormats](#addstandardformats) funkcji elementów członkowskich, aby dodać formaty Schowka do okna dialogowego. Można również użyć [m_ps](#m_ps) strukturę, aby zainicjować wartości lub stany formantów w oknie dialogowym. `m_ps` Struktury jest typu OLEUIPASTESPECIAL.

Aby uzyskać więcej informacji, zobacz [OLEUIPASTESPECIAL](/windows/desktop/api/oledlg/ns-oledlg-tagoleuipastespeciala) struktury w zestawie Windows SDK.

Aby uzyskać więcej informacji dotyczących okien dialogowych OLE specyficzne, zobacz artykuł [okna dialogowe w OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COlePasteSpecialDialog`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxodlgs.h

##  <a name="addformat"></a>  COlePasteSpecialDialog::AddFormat

Wywołaj tę funkcję, aby dodać nowe formaty do listy formatów obsługiwanych przez aplikację w ramach operacji Wklej specjalne.

```
void AddFormat(
    const FORMATETC& formatEtc,
    LPTSTR lpszFormat,
    LPTSTR lpszResult,
    DWORD flags);

void AddFormat(
    UINT cf,
    DWORD tymed,
    UINT nFormatID,
    BOOL bEnableIcon,
    BOOL bLink);
```

### <a name="parameters"></a>Parametry

*fmt*<br/>
Odwołanie do typu danych do dodania.

*lpszFormat*<br/>
Ciąg opisujący format dla użytkownika.

*lpszResult*<br/>
Ciąg, który opisuje wynik, jeśli ten format jest wybierany w oknie dialogowym.

*flagi*<br/>
Różne łączenie i osadzanie opcjami dostępnymi na potrzeby tego formatu. Ta flaga jest bitową kombinacją jeden lub więcej różnych wartości OLEUIPASTEFLAG Typ wyliczany.

*cf*<br/>
Format schowka do dodania.

*tymed*<br/>
Typów nośników, które są dostępne w tym formacie. Jest bitową kombinacją jeden lub więcej wartości w TYMED Typ wyliczany.

*nFormatID*<br/>
Identyfikator ciąg, który identyfikuje ten format. Format ten ciąg jest dwa oddzielne ciągi oddzielone znakiem "\n". Pierwszy ciąg jest taka sama, które zostaną przekazane w *lpstrFormat* parametru, a drugi jest taka sama jak *lpstrResult* parametru.

*bEnableIcon*<br/>
Flaga określająca, czy pole wyboru Wyświetl jako ikonę jest włączona, gdy ten format jest wybierany w polu listy.

*bLink*<br/>
Flaga określająca, czy przycisk radiowy Wklej łącze jest włączone, gdy ten format jest wybierany w polu listy.

### <a name="remarks"></a>Uwagi

Ta funkcja może zostać wywołana dodać standardowych formatów, takich jak CF_TEXT lub CF_TIFF albo formatów niestandardowych, które aplikacja została zarejestrowana w systemie. Aby uzyskać więcej informacji na temat wklejanie obiektów danych w aplikacji, zobacz artykuł [obiekty danych i źródeł danych: Manipulowanie](../../mfc/data-objects-and-data-sources-manipulation.md).

Aby uzyskać więcej informacji, zobacz [TYMED](/windows/desktop/api/objidl/ne-objidl-tagtymed) typ wyliczeniowy i [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) struktury w zestawie Windows SDK.

Aby uzyskać więcej informacji, zobacz [OLEUIPASTEFLAG](/windows/desktop/api/oledlg/ne-oledlg-tagoleuipasteflag) wyliczyć typów w zestawie Windows SDK.

##  <a name="addlinkentry"></a>  COlePasteSpecialDialog::AddLinkEntry

Dodaje nowy wpis do listy obsługiwanych formatów Schowka.

```
OLEUIPASTEFLAG AddLinkEntry(UINT cf);
```

### <a name="parameters"></a>Parametry

*cf*<br/>
Format schowka do dodania.

### <a name="return-value"></a>Wartość zwracana

[OLEUIPASTEFLAG](/windows/desktop/api/oledlg/ne-oledlg-tagoleuipasteflag) struktury zawierającej informacje dotyczące nowego wpisu łącza.

##  <a name="addstandardformats"></a>  COlePasteSpecialDialog::AddStandardFormats

Wywołaj tę funkcję, aby dodać następujące formaty Schowka do listy formatów obsługiwanych przez aplikację w ramach operacji Wklej specjalne:

```
void AddStandardFormats(BOOL bEnableLink = TRUE);
```

### <a name="parameters"></a>Parametry

*bEnableLink*<br/>
Flaga określająca, czy należy dodać CF_LINKSOURCE do listy formatów aplikacji można wkleić.

### <a name="remarks"></a>Uwagi

- CF_BITMAP

- CF_DIB

- CF_METAFILEPICT

- **"Osadzonego"**

- (opcjonalnie) **"Link źródła"**

Te formaty są używane do obsługi, osadzanie i łączenie.

##  <a name="colepastespecialdialog"></a>  COlePasteSpecialDialog::COlePasteSpecialDialog

Konstruuje `COlePasteSpecialDialog` obiektu.

```
COlePasteSpecialDialog(
    DWORD dwFlags = PSF_SELECTPASTE,
    COleDataObject* pDataObject = NULL,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*Flagidw*<br/>
Flagi tworzenia zawiera dowolną liczbę następujące flagi, które są połączone za pomocą operatora bitowego OR:

- PSF_SELECTPASTE Określa, że przycisk radiowy Wklej będą sprawdzane początkowo, gdy okno dialogowe jest wywoływana. Nie można używać w połączeniu z PSF_SELECTPASTELINK. Domyślnie włączone.

- PSF_SELECTPASTELINK Określa, że przycisk radiowy Wklej łącze jest sprawdzany początkowo, gdy okno dialogowe jest wywoływana. Nie można używać w połączeniu z PSF_SELECTPASTE.

- Określa PSF_CHECKDISPLAYASICON, która będzie wyświetlana jako ikona okno wyboru zaznaczone początkowo, gdy okno dialogowe jest wywoływana.

- PSF_SHOWHELP Określa, że przycisk Pomoc, będą wyświetlane, gdy wywoływana jest okno dialogowe.

*pDataObject*<br/>
Wskazuje [COleDataObject](../../mfc/reference/coledataobject-class.md) wklejania. Jeśli ta wartość wynosi NULL, pobiera `COleDataObject` ze Schowka.

*pParentWnd*<br/>
Wskazuje na obiekt okna nadrzędnego lub właściciela (typu `CWnd`) do którego należy obiekt okna dialogowego. Jeśli ma wartość NULL, okno nadrzędne, okno dialogowe jest ustawiony na okna głównego aplikacji.

### <a name="remarks"></a>Uwagi

Ta funkcja tylko tworzy `COlePasteSpecialDialog` obiektu. Aby wyświetlić okno dialogowe, należy wywołać [DoModal](#domodal) funkcji.

Aby uzyskać więcej informacji, zobacz [OLEUIPASTEFLAG](/windows/desktop/api/oledlg/ne-oledlg-tagoleuipasteflag) wyliczyć typów w zestawie Windows SDK.

##  <a name="createitem"></a>  COlePasteSpecialDialog::CreateItem

Tworzy nowy element, który został wybrany w oknie dialogowym Wklej specjalne.

```
BOOL CreateItem(COleClientItem* pNewItem);
```

### <a name="parameters"></a>Parametry

*pNewItem*<br/>
Wskazuje `COleClientItem` wystąpienia. Nie może mieć wartości NULL.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli element został utworzony pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja powinna być wywoływana tylko po [DoModal](#domodal) zwraca IDOK.

##  <a name="domodal"></a>  COlePasteSpecialDialog::DoModal

Wyświetla okno dialogowe w OLE Wklej specjalne.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Wartość zwracana

Stan ukończenia dla okna dialogowego. Jeden z następujących wartości:

- IDOK, jeśli pomyślnie zostało wyświetlone okno dialogowe.

- IDCANCEL, jeśli użytkownik anulował okno dialogowe.

- IDABORT, jeśli wystąpił błąd. Jeśli zwracana jest IDABORT, wywołaj `COleDialog::GetLastError` funkcja elementu członkowskiego, aby uzyskać więcej informacji o typie błędu, który wystąpił. Aby uzyskać listę możliwych błędów, zobacz [OleUIPasteSpecial](/windows/desktop/api/oledlg/nf-oledlg-oleuipastespeciala) funkcji w zestawie Windows SDK.

### <a name="remarks"></a>Uwagi

Aby inicjowanie różne formanty okna dialogowego, ustawiając członkowie [m_ps](#m_ps) struktury, należy to zrobić przed wywołaniem `DoModal`, ale po jest konstruowany obiektu okna dialogowego.

Jeśli `DoModal` zwraca IDOK, może wywołać inny członek funkcje, które można pobrać ustawień lub wprowadzania informacji przez użytkownika w oknie dialogowym.

##  <a name="getdrawaspect"></a>  COlePasteSpecialDialog::GetDrawAspect

Określa, jeśli użytkownik wybrał opcję wyświetlania wybrany element jako ikona.

```
DVASPECT GetDrawAspect() const;
```

### <a name="return-value"></a>Wartość zwracana

Metoda wymagane do renderowania obiektu.

- DVASPECT_CONTENT jest zwracana, jeśli nie jest wyświetlana jako ikona okno wyboru sprawdzane podczas odrzucania okno dialogowe.

- DVASPECT_ICON zwracany, jeśli pole wyboru Wyświetl jako ikonę została sprawdzona podczas odrzucania okno dialogowe.

### <a name="remarks"></a>Uwagi

Tylko wywołać tę funkcję po [DoModal](#domodal) zwraca IDOK.

Aby uzyskać więcej informacji na temat Rysowanie aspektu, zobacz [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) struktury w zestawie Windows SDK.

##  <a name="geticonicmetafile"></a>  COlePasteSpecialDialog::GetIconicMetafile

Pobiera metaplik skojarzone z elementem wybrane przez użytkownika.

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>Wartość zwracana

Dojście do Metaplik zawierający ikony aspektów wybranego elementu, jeśli zaznaczono pole wyboru Wyświetl jako ikonę podczas odrzucania okna dialogowego wybierając **OK**; w przeciwnym razie wartość NULL.

##  <a name="getpasteindex"></a>  COlePasteSpecialDialog::GetPasteIndex

Pobiera wartość indeksu skojarzone z wpisem wybranego użytkownika.

```
int GetPasteIndex() const;
```

### <a name="return-value"></a>Wartość zwracana

Indeks do tablicy `OLEUIPASTEENTRY` struktur, które zostało wybrane przez użytkownika. Format, który odnosi się do wybranego indeksu należy używać podczas wykonywania operacji wklejania.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [OLEUIPASTEENTRY](/windows/desktop/api/oledlg/ns-oledlg-tagoleuipasteentrya) struktury w zestawie Windows SDK.

##  <a name="getselectiontype"></a>  COlePasteSpecialDialog::GetSelectionType

Określa typ wybranego użytkownika.

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca typ dokonano wyboru.

### <a name="remarks"></a>Uwagi

Wartości zwracanej są określane przez `Selection` typ wyliczeniowy zadeklarowany w `COlePasteSpecialDialog` klasy.

```
enum Selection {
    pasteLink,
    pasteNormal,
    pasteOther,
    pasteStatic
    };
```

Wykonaj krótki desccriptions z następujących wartości:

- `COlePasteSpecialDialog::pasteLink` Przycisk radiowy Wklej łącze zostało zaznaczone, a wybrany format był to standardowy format OLE.

- `COlePasteSpecialDialog::pasteNormal` Przycisk radiowy Wklej zostało zaznaczone, a wybrany format był to standardowy format OLE.

- `COlePasteSpecialDialog::pasteOther` Wybrany format nie jest to standardowy format OLE.

- `COlePasteSpecialDialog::pasteStatic` Wybrany format był metaplik.

##  <a name="m_ps"></a>  COlePasteSpecialDialog::m_ps

Struktury typu OLEUIPASTESPECIAL używane do sterowania zachowaniem Wklej specjalne okno dialogowe.

```
OLEUIPASTESPECIAL m_ps;
```

### <a name="remarks"></a>Uwagi

Można modyfikować składowe tej struktury, bezpośrednio lub za pośrednictwem funkcji elementów członkowskich.

Aby uzyskać więcej informacji, zobacz [OLEUIPASTESPECIAL](/windows/desktop/api/oledlg/ns-oledlg-tagoleuipastespeciala) struktury w zestawie Windows SDK.

## <a name="see-also"></a>Zobacz także

[Próbki MFC OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[Klasa COleDialog](../../mfc/reference/coledialog-class.md)<br/>
[Diagram hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleDialog](../../mfc/reference/coledialog-class.md)
