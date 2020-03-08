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
ms.openlocfilehash: f4174369620f14f2d1ac410aa5d756c75097ad0f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855608"
---
# <a name="colepastespecialdialog-class"></a>Klasa COlePasteSpecialDialog

Używane dla okna dialogowego specjalne wklejanie OLE.

## <a name="syntax"></a>Składnia

```
class COlePasteSpecialDialog : public COleDialog
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[COlePasteSpecialDialog::COlePasteSpecialDialog](#colepastespecialdialog)|Konstruuje obiekt `COlePasteSpecialDialog`.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[COlePasteSpecialDialog:: AddFormat](#addformat)|Dodaje niestandardowe formaty do listy formatów, które aplikacja może wkleić.|
|[COlePasteSpecialDialog::AddLinkEntry](#addlinkentry)|Dodaje nowy wpis do listy obsługiwanych formatów Schowka.|
|[COlePasteSpecialDialog::AddStandardFormats](#addstandardformats)|Dodaje CF_BITMAP, CF_DIB, CF_METAFILEPICT i opcjonalnie CF_LINKSOURCE do listy formatów, które aplikacja może wkleić.|
|[COlePasteSpecialDialog:: GetItem](#createitem)|Tworzy element w dokumencie kontenera przy użyciu określonego formatu.|
|[COlePasteSpecialDialog::D oModal](#domodal)|Wyświetla okno dialogowe specjalne wklejenie OLE.|
|[COlePasteSpecialDialog::GetDrawAspect](#getdrawaspect)|Informuje, czy element ma być rysowany jako ikona, czy nie.|
|[COlePasteSpecialDialog::GetIconicMetafile](#geticonicmetafile)|Pobiera uchwyt do metapliku skojarzonego z formą Icon tego elementu.|
|[COlePasteSpecialDialog::GetPasteIndex](#getpasteindex)|Pobiera indeks dostępnych opcji wklejania, które zostały wybrane przez użytkownika.|
|[COlePasteSpecialDialog:: GetSelectionType](#getselectiontype)|Pobiera wybrany typ zaznaczenia.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Name (Nazwa)|Opis|
|----------|-----------------|
|[COlePasteSpecialDialog:: m_ps](#m_ps)|Struktura typu OLEUIPASTESPECIAL, która kontroluje funkcję okna dialogowego.|

## <a name="remarks"></a>Uwagi

Utwórz obiekt klasy `COlePasteSpecialDialog`, gdy chcesz wywołać to okno dialogowe. Po skonstruowaniu obiektu `COlePasteSpecialDialog` można użyć funkcji [AddFormat](#addformat) i [AddStandardFormats](#addstandardformats) , aby dodać formaty schowka do okna dialogowego. Można również użyć struktury [m_ps](#m_ps) , aby zainicjować wartości lub Stany kontrolek w oknie dialogowym. Struktura `m_ps` jest typu OLEUIPASTESPECIAL.

Aby uzyskać więcej informacji, zapoznaj się ze strukturą [OLEUIPASTESPECIAL](/windows/win32/api/oledlg/ns-oledlg-oleuipastespecialw) w Windows SDK.

Aby uzyskać więcej informacji dotyczących okien dialogowych specyficznych dla OLE, zobacz [okna dialogowe artykułu w OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COlePasteSpecialDialog`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxodlgs. h

##  <a name="addformat"></a>COlePasteSpecialDialog:: AddFormat

Wywołaj tę funkcję, aby dodać nowe formaty do listy formatów obsługiwanych przez aplikację w operacji wklejania specjalnego.

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

*FMT*<br/>
Odwołanie do typu danych do dodania.

*lpszFormat*<br/>
Ciąg opisujący format użytkownika.

*lpszResult*<br/>
Ciąg opisujący wynik w przypadku wybrania tego formatu w oknie dialogowym.

*znaczników*<br/>
Dostępne są różne opcje łączenia i osadzania dla tego formatu. Ta flaga jest bitową kombinacją co najmniej jednej z różnych wartości w typie wyliczeniowym OLEUIPASTEFLAG.

*Porównaj*<br/>
Format schowka do dodania.

*tymed*<br/>
Typy multimediów dostępne w tym formacie. Jest to bitowa kombinacja co najmniej jednej wartości w typie wyliczeniowym TYMED.

*nFormatID*<br/>
Identyfikator ciągu, który identyfikuje ten format. Formatem tego ciągu są dwa oddzielne ciągi oddzielone znakiem "\n". Pierwszy ciąg jest taki sam, który zostałby przesłany w parametrze *lpstrFormat* , a drugi jest taki sam jak parametr *lpstrResult* .

*bEnableIcon*<br/>
Flaga określająca, czy pole wyboru Wyświetlaj jako ikonę jest włączone, gdy ten format jest wybierany w polu listy.

*Wskaźnika*<br/>
Flaga określająca, czy przycisk radiowy Wklej łącze jest włączony w przypadku wybrania tego formatu w polu listy.

### <a name="remarks"></a>Uwagi

Ta funkcja może zostać wywołana w celu dodania do formatów standardowych, takich jak CF_TEXT lub CF_TIFF lub formatów niestandardowych, które aplikacja zarejestrowała w systemie. Aby uzyskać więcej informacji na temat wklejania obiektów danych do aplikacji, zobacz temat [obiekty danych artykułu i źródła danych: manipulowanie](../../mfc/data-objects-and-data-sources-manipulation.md).

Aby uzyskać więcej informacji, zobacz [TYMED](/windows/win32/api/objidl/ne-objidl-tymed) i strukturę [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) w Windows SDK.

Aby uzyskać więcej informacji, zobacz [OLEUIPASTEFLAG](/windows/win32/api/oledlg/ne-oledlg-oleuipasteflag) typ wyliczeniowy w Windows SDK.

##  <a name="addlinkentry"></a>COlePasteSpecialDialog::AddLinkEntry

Dodaje nowy wpis do listy obsługiwanych formatów Schowka.

```
OLEUIPASTEFLAG AddLinkEntry(UINT cf);
```

### <a name="parameters"></a>Parametry

*Porównaj*<br/>
Format schowka do dodania.

### <a name="return-value"></a>Wartość zwracana

Struktura [OLEUIPASTEFLAG](/windows/win32/api/oledlg/ne-oledlg-oleuipasteflag) zawierająca informacje dla nowego wpisu linku.

##  <a name="addstandardformats"></a>COlePasteSpecialDialog::AddStandardFormats

Wywołaj tę funkcję, aby dodać następujące formaty schowka do listy formatów obsługiwanych przez aplikację w operacji wklejania specjalnego:

```
void AddStandardFormats(BOOL bEnableLink = TRUE);
```

### <a name="parameters"></a>Parametry

*bEnableLink*<br/>
Flaga określająca, czy dodać CF_LINKSOURCE do listy formatów, które aplikacja może wkleić.

### <a name="remarks"></a>Uwagi

- CF_BITMAP

- CF_DIB

- CF_METAFILEPICT

- **"Osadzony obiekt"**

- zdefiniować **"Link źródła"**

Te formaty służą do obsługi osadzania i łączenia.

##  <a name="colepastespecialdialog"></a>COlePasteSpecialDialog::COlePasteSpecialDialog

Konstruuje obiekt `COlePasteSpecialDialog`.

```
COlePasteSpecialDialog(
    DWORD dwFlags = PSF_SELECTPASTE,
    COleDataObject* pDataObject = NULL,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*flagiDW*<br/>
Flaga tworzenia zawiera dowolną liczbę następujących flag połączonych przy użyciu operatora bitowego lub:

- PSF_SELECTPASTE określa, że po wywołaniu okna dialogowego zostanie zaewidencjonować przycisk radiowy Wklej. Nie można używać w połączeniu z PSF_SELECTPASTELINK. Domyślnie włączone.

- PSF_SELECTPASTELINK określa, że przycisk radiowy Wklej łącze jest sprawdzany początkowo po wywołaniu okna dialogowego. Nie można używać w połączeniu z PSF_SELECTPASTE.

- PSF_CHECKDISPLAYASICON określa, że pole wyboru Wyświetlaj jako ikonę zostanie zaznaczone początkowo po wywołaniu okna dialogowego.

- PSF_SHOWHELP określa, że przycisk Pomoc będzie wyświetlany po wywołaniu okna dialogowego.

*pDataObject*<br/>
Wskazuje [COleDataObject](../../mfc/reference/coledataobject-class.md) do wklejenia. Jeśli ta wartość jest RÓWNa NULL, pobiera `COleDataObject` ze schowka.

*pParentWnd*<br/>
Wskazuje obiekt obiektu nadrzędnego lub właściciela (typu `CWnd`), do którego należy obiekt okna dialogowego. Jeśli ma wartość NULL, okno dialogowe nadrzędne okna dialogowego jest ustawione na główne okno aplikacji.

### <a name="remarks"></a>Uwagi

Ta funkcja konstruuje tylko obiekt `COlePasteSpecialDialog`. Aby wyświetlić okno dialogowe, wywołaj funkcję [DoModal](#domodal) .

Aby uzyskać więcej informacji, zobacz [OLEUIPASTEFLAG](/windows/win32/api/oledlg/ne-oledlg-oleuipasteflag) typ wyliczeniowy w Windows SDK.

##  <a name="createitem"></a>COlePasteSpecialDialog:: GetItem

Tworzy nowy element, który został wybrany w oknie dialogowym wklejanie specjalne.

```
BOOL CreateItem(COleClientItem* pNewItem);
```

### <a name="parameters"></a>Parametry

*pNewItem*<br/>
Wskazuje na wystąpienie `COleClientItem`. Nie może mieć wartości NULL.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli element został utworzony pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja powinna być wywoływana tylko po [DoModal](#domodal) zwraca IDOK.

##  <a name="domodal"></a>COlePasteSpecialDialog::D oModal

Wyświetla okno dialogowe specjalne wklejenie OLE.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Wartość zwracana

Stan ukończenia dla okna dialogowego. Jedna z następujących wartości:

- IDOK, jeśli okno dialogowe zostało wyświetlone pomyślnie.

- IDCANCEL, jeśli użytkownik anulował okno dialogowe.

- IDABORT, jeśli wystąpił błąd. Jeśli IDABORT jest zwracany, wywołaj funkcję członkowską `COleDialog::GetLastError`, aby uzyskać więcej informacji na temat typu błędu, który wystąpił. Listę możliwych błędów można znaleźć w funkcji [OLEUIPASTESPECIAL](/windows/win32/api/oledlg/nf-oledlg-oleuipastespecialw) w Windows SDK.

### <a name="remarks"></a>Uwagi

Jeśli chcesz zainicjować różne kontrolki okna dialogowego, ustawiając elementy członkowskie struktury [m_ps](#m_ps) , należy to zrobić przed wywołaniem `DoModal`, ale po skonstruowaniu obiektu okna dialogowego.

Jeśli `DoModal` zwraca IDOK, można wywołać inne funkcje członkowskie, aby pobrać ustawienia lub dane wejściowe użytkownika w oknie dialogowym.

##  <a name="getdrawaspect"></a>COlePasteSpecialDialog::GetDrawAspect

Określa, czy użytkownik zdecydował się wyświetlić wybrany element jako ikonę.

```
DVASPECT GetDrawAspect() const;
```

### <a name="return-value"></a>Wartość zwracana

Metoda wymagana do renderowania obiektu.

- DVASPECT_CONTENT zwracana, jeśli pole wyboru Wyświetlaj jako ikonę nie zostało zaznaczone, gdy okno dialogowe zostało odrzucone.

- DVASPECT_ICON zwracana, jeśli pole wyboru Wyświetlaj jako ikonę zostało zaznaczone, gdy okno dialogowe zostało odrzucone.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję tylko po [DoModal](#domodal) zwraca IDOK.

Aby uzyskać więcej informacji na temat aspektów rysowania, zapoznaj się ze strukturą [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) w Windows SDK.

##  <a name="geticonicmetafile"></a>COlePasteSpecialDialog::GetIconicMetafile

Pobiera metaplik skojarzony z elementem wybranym przez użytkownika.

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>Wartość zwracana

Uchwyt do metapliku zawierającego ikonę ikony wybranego elementu, jeśli pole wyboru Wyświetlaj jako ikonę zostało zaznaczone, gdy okno dialogowe zostało odrzucone, wybierając **przycisk OK**. w przeciwnym razie wartość NULL.

##  <a name="getpasteindex"></a>COlePasteSpecialDialog::GetPasteIndex

Pobiera wartość indeksu skojarzoną z wpisem wybranym przez użytkownika.

```
int GetPasteIndex() const;
```

### <a name="return-value"></a>Wartość zwracana

Indeks do tablicy struktur `OLEUIPASTEENTRY`, które zostały wybrane przez użytkownika. Format, który odpowiada wybranemu indeksowi, powinien być używany podczas wykonywania operacji wklejania.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zapoznaj się ze strukturą [OLEUIPASTEENTRY](/windows/win32/api/oledlg/ns-oledlg-oleuipasteentryw) w Windows SDK.

##  <a name="getselectiontype"></a>COlePasteSpecialDialog:: GetSelectionType

Określa typ wyboru dokonany przez użytkownika.

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca typ dokonanego wyboru.

### <a name="remarks"></a>Uwagi

Wartości typu zwracanego są określane przez `Selection` typ wyliczeniowy zadeklarowany w klasie `COlePasteSpecialDialog`.

```
enum Selection {
    pasteLink,
    pasteNormal,
    pasteOther,
    pasteStatic
    };
```

Poniżej przedstawiono krótkie desccriptions następujących wartości:

- `COlePasteSpecialDialog::pasteLink` sprawdzono przycisk radiowy wklejania linku, a wybrany format był standardowym formatem OLE.

- `COlePasteSpecialDialog::pasteNormal` sprawdzono przycisk radiowy wklejania, a wybrany format był standardowym formatem OLE.

- `COlePasteSpecialDialog::pasteOther` wybrany format nie jest standardowym formatem OLE.

- `COlePasteSpecialDialog::pasteStatic` wybrany format to metaplik.

##  <a name="m_ps"></a>COlePasteSpecialDialog:: m_ps

Struktura typu OLEUIPASTESPECIAL używana do kontrolowania zachowania okna dialogowego wklejanie specjalne.

```
OLEUIPASTESPECIAL m_ps;
```

### <a name="remarks"></a>Uwagi

Elementy członkowskie tej struktury mogą być modyfikowane bezpośrednio lub za poorednictwem funkcji składowych.

Aby uzyskać więcej informacji, zapoznaj się ze strukturą [OLEUIPASTESPECIAL](/windows/win32/api/oledlg/ns-oledlg-oleuipastespecialw) w Windows SDK.

## <a name="see-also"></a>Zobacz też

[Przykład OCLIENT MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa COleDialog](../../mfc/reference/coledialog-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleDialog](../../mfc/reference/coledialog-class.md)
