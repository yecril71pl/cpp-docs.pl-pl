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
ms.openlocfilehash: 47fb421ef9dedcae7f92d33f55988dbbc2ea452d
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753817"
---
# <a name="colepastespecialdialog-class"></a>Klasa COlePasteSpecialDialog

Używane w oknie dialogowym Ole Paste Special.

## <a name="syntax"></a>Składnia

```
class COlePasteSpecialDialog : public COleDialog
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COlePasteSpecialDialog::COlePasteSpecialDialog](#colepastespecialdialog)|Konstruuje `COlePasteSpecialDialog` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COlePasteSpecialDialog::AddFormat](#addformat)|Dodaje niestandardowe formaty do listy formatów, które aplikacja może wklejać.|
|[COlePasteSpecialDialog::AddLinkEntry](#addlinkentry)|Dodaje nowy wpis do listy obsługiwanych formatów Schowka.|
|[COlePasteSpecialDialog::AddStandardFormats](#addstandardformats)|Dodaje CF_BITMAP, CF_DIB, CF_METAFILEPICT i opcjonalnie CF_LINKSOURCE do listy formatów, które aplikacja może wklejać.|
|[COlePasteSpecialDialog::CreateItem](#createitem)|Tworzy element w dokumencie kontenera przy użyciu określonego formatu.|
|[COlePasteSpecialDialog::DoModal](#domodal)|Wyświetla okno dialogowe Specjalne wklejenie OLE.|
|[COlePasteSpecialDialog::GetDrawAspect](#getdrawaspect)|Określa, czy element ma być rysowany jako ikona, czy nie.|
|[COlePasteSpecialDialog::GetIconicMetafile](#geticonicmetafile)|Pobiera uchwyt do metapliku skojarzonego z ikoniczną formą tego elementu.|
|[COlePasteSpecialDialog::GetPasteIndex](#getpasteindex)|Pobiera indeks dostępnych opcji wklejania, który został wybrany przez użytkownika.|
|[COlePasteSpecialDialog::GetSelectionType](#getselectiontype)|Pobiera typ wybranego wyboru.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[COlePasteSpecialDialog::m_ps](#m_ps)|Struktura typu OLEUIPASTESPECIAL, która steruje funkcją okna dialogowego.|

## <a name="remarks"></a>Uwagi

Utwórz obiekt `COlePasteSpecialDialog` klasy, jeśli chcesz wywołać to okno dialogowe. Po `COlePasteSpecialDialog` skonstruowaniu obiektu można użyć funkcji członkowskich [AddFormat](#addformat) i [AddStandardFormats,](#addstandardformats) aby dodać formaty Schowka do okna dialogowego. Można również użyć [struktury m_ps](#m_ps) do zainicjowania wartości lub stanów formantów w oknie dialogowym. Struktura `m_ps` jest typu OLEUIPASTESPECIAL.

Aby uzyskać więcej informacji, zobacz [strukturę OLEUIPASTESPECIAL](/windows/win32/api/oledlg/ns-oledlg-oleuipastespecialw) w windows SDK.

Aby uzyskać więcej informacji dotyczących okien dialogowych specyficznych dla ole, zobacz [okna dialogowe](../../mfc/dialog-boxes-in-ole.md)artykułu OLE .

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cdialog](../../mfc/reference/cdialog-class.md)

[CKlogialny](../../mfc/reference/ccommondialog-class.md)

[COleDialog (Polski)](../../mfc/reference/coledialog-class.md)

`COlePasteSpecialDialog`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxodlgs.h

## <a name="colepastespecialdialogaddformat"></a><a name="addformat"></a>COlePasteSpecialDialog::AddFormat

Wywołanie tej funkcji, aby dodać nowe formaty do listy formatów aplikacji może obsługiwać w wklej specjalne operacji.

```cpp
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

*Fmt*<br/>
Odwołanie do typu danych do dodania.

*lpszFormat*<br/>
Ciąg opisujący format użytkownika.

*lpszResult (wynik)*<br/>
Ciąg opisujący wynik, jeśli ten format jest wybrany w oknie dialogowym.

*flagi*<br/>
Różne opcje łączenia i osadzania dostępne dla tego formatu. Ta flaga jest bitowe połączenie jednej lub więcej różnych wartości w OLEUIPASTEFLAG wyliczonego typu.

*Por*<br/>
Format schowka do dodania.

*Tymed*<br/>
Typy nośników dostępne w tym formacie. Jest to bitowa kombinacja jednej lub więcej wartości w typie wyliczonym TYMED.

*nFormatID*<br/>
Identyfikator ciągu, który identyfikuje ten format. Format tego ciągu to dwa oddzielne ciągi oddzielone znakiem '\n'. Pierwszy ciąg jest taki sam, który byłby przekazywany w *lpstrFormat* parametr, a drugi jest taki sam jak *lpstrResult* parametru.

*bWzdłużnik*<br/>
Flaga określająca, czy pole wyboru Wyświetl jako ikona jest włączone, gdy ten format jest wybrany w polu listy.

*Blink*<br/>
Flaga określająca, czy przycisk opcji Wklej link jest włączony, gdy ten format jest wybrany w polu listy.

### <a name="remarks"></a>Uwagi

Tę funkcję można wywołać w celu dodania standardowych formatów, takich jak CF_TEXT lub CF_TIFF lub formatów niestandardowych, które aplikacja zarejestrowała w systemie. Aby uzyskać więcej informacji na temat wklejania obiektów danych do aplikacji, zobacz artykuł [Obiekty danych i źródła danych: Manipulacja](../../mfc/data-objects-and-data-sources-manipulation.md).

Aby uzyskać więcej informacji, zobacz typ wyliczenia [TYMED](/windows/win32/api/objidl/ne-objidl-tymed) i strukturę [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) w sdk systemu Windows.

Aby uzyskać więcej informacji, zobacz typ wyliczony [OLEUIPASTEFLAG](/windows/win32/api/oledlg/ne-oledlg-oleuipasteflag) w pliku SDK systemu Windows.

## <a name="colepastespecialdialogaddlinkentry"></a><a name="addlinkentry"></a>COlePasteSpecialDialog::AddLinkEntry

Dodaje nowy wpis do listy obsługiwanych formatów Schowka.

```
OLEUIPASTEFLAG AddLinkEntry(UINT cf);
```

### <a name="parameters"></a>Parametry

*Por*<br/>
Format schowka do dodania.

### <a name="return-value"></a>Wartość zwracana

Struktura [OLEUIPASTEFLAG](/windows/win32/api/oledlg/ne-oledlg-oleuipasteflag) zawierająca informacje dotyczące nowego wpisu łącza.

## <a name="colepastespecialdialogaddstandardformats"></a><a name="addstandardformats"></a>COlePasteSpecialDialog::AddStandardFormats

Wywołanie tej funkcji, aby dodać następujące formaty Schowka do listy formatów, które aplikacja może obsługiwać w wklej specjalnej operacji:

```cpp
void AddStandardFormats(BOOL bEnableLink = TRUE);
```

### <a name="parameters"></a>Parametry

*bWzszalny link*<br/>
Flaga, która określa, czy dodać CF_LINKSOURCE do listy formatów, które aplikacja może wkleić.

### <a name="remarks"></a>Uwagi

- CF_BITMAP

- CF_DIB

- CF_METAFILEPICT

- **"Obiekt osadzony"**

- (opcjonalnie) **"Źródło łącza"**

Formaty te są używane do obsługi osadzania i łączenia.

## <a name="colepastespecialdialogcolepastespecialdialog"></a><a name="colepastespecialdialog"></a>COlePasteSpecialDialog::COlePasteSpecialDialog

Konstruuje `COlePasteSpecialDialog` obiekt.

```
COlePasteSpecialDialog(
    DWORD dwFlags = PSF_SELECTPASTE,
    COleDataObject* pDataObject = NULL,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*Dwflags*<br/>
Flaga tworzenia, zawiera dowolną liczbę następujących flag połączonych za pomocą operatora bitowego OR:

- PSF_SELECTPASTE Określa, że przycisk opcji Wklej zostanie początkowo sprawdzony po wywołaniu okna dialogowego. Nie można używać w połączeniu z PSF_SELECTPASTELINK. Domyślnie włączone.

- PSF_SELECTPASTELINK Określa, że przycisk opcji Wklej łącze zostanie początkowo sprawdzony po wywołaniu okna dialogowego. Nie można używać w połączeniu z PSF_SELECTPASTE.

- PSF_CHECKDISPLAYASICON Określa, że pole wyboru Wyświetl jako ikonę zostanie początkowo zaznaczone po wywołaniu okna dialogowego.

- PSF_SHOWHELP Określa, że przycisk Pomoc będzie wyświetlany po wywołaniu okna dialogowego.

*pDataObject (1000)*<br/>
Wskazuje na [COleDataObject](../../mfc/reference/coledataobject-class.md) do wklejania. Jeśli ta wartość ma wartość `COleDataObject` NULL, pobiera ją ze Schowka.

*pParentWnd*<br/>
Wskazuje obiekt okna nadrzędnego lub `CWnd`właściciela (typu), do którego należy obiekt okna dialogowego. Jeśli jest null, okno nadrzędne okna dialogowego jest ustawiona na główne okno aplikacji.

### <a name="remarks"></a>Uwagi

Ta funkcja tworzy `COlePasteSpecialDialog` tylko obiekt. Aby wyświetlić okno dialogowe, należy wywołać funkcję [DoModal.](#domodal)

Aby uzyskać więcej informacji, zobacz typ wyliczony [OLEUIPASTEFLAG](/windows/win32/api/oledlg/ne-oledlg-oleuipasteflag) w pliku SDK systemu Windows.

## <a name="colepastespecialdialogcreateitem"></a><a name="createitem"></a>COlePasteSpecialDialog::CreateItem

Tworzy nowy element wybrany w oknie dialogowym Wklej specjalnie.

```
BOOL CreateItem(COleClientItem* pNewItem);
```

### <a name="parameters"></a>Parametry

*pNewItem (Niemka)*<br/>
Wskazuje na `COleClientItem` wystąpienie. Nie może być null.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli element został pomyślnie utworzony; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja powinna być wywoływana tylko po [domodal](#domodal) zwraca IDOK.

## <a name="colepastespecialdialogdomodal"></a><a name="domodal"></a>COlePasteSpecialDialog::DoModal

Wyświetla okno dialogowe Specjalne wklejenie OLE.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Wartość zwracana

Stan ukończenia okna dialogowego. Jedna z następujących wartości:

- IDOK, jeśli okno dialogowe zostało pomyślnie wyświetlone.

- IDCANCEL, jeśli użytkownik anulował okno dialogowe.

- IDABORT, jeśli wystąpił błąd. Jeśli idabort jest zwracany, wywołać funkcję `COleDialog::GetLastError` elementu członkowskiego, aby uzyskać więcej informacji na temat typu błędu, który wystąpił. Aby uzyskać listę możliwych błędów, zobacz [OleUIPasteSpecial](/windows/win32/api/oledlg/nf-oledlg-oleuipastespecialw) funkcji w zestawie Windows SDK.

### <a name="remarks"></a>Uwagi

Jeśli chcesz zainicjować różne formanty okna dialogowego, ustawiając elementy członkowskie [m_ps](#m_ps) `DoModal`struktury, należy to zrobić przed wywołaniem , ale po skonstruowaniu obiektu okna dialogowego.

Jeśli `DoModal` zwraca IDOK, można wywołać inne funkcje członkowskie, aby pobrać ustawienia lub informacje wprowadzone przez użytkownika w oknie dialogowym.

## <a name="colepastespecialdialoggetdrawaspect"></a><a name="getdrawaspect"></a>COlePasteSpecialDialog::GetDrawAspect

Określa, czy użytkownik zdecydował się wyświetlić zaznaczony element jako ikonę.

```
DVASPECT GetDrawAspect() const;
```

### <a name="return-value"></a>Wartość zwracana

Metoda potrzebna do renderowania obiektu.

- DVASPECT_CONTENT Zwrócony, jeśli pole wyboru Wyświetl jako ikona nie zostało zaznaczone po odrzuceniu okna dialogowego.

- DVASPECT_ICON Zwrócony, jeśli pole wyboru Wyświetl jako ikonę zostało zaznaczone po odrzuceniu okna dialogowego.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję tylko po [domodal](#domodal) zwraca IDOK.

Aby uzyskać więcej informacji na temat aspektu rysowania, zobacz strukturę [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) w sdk systemu Windows.

## <a name="colepastespecialdialoggeticonicmetafile"></a><a name="geticonicmetafile"></a>COlePasteSpecialDialog::GetIconicMetafile

Pobiera metaplik skojarzony z elementem wybranym przez użytkownika.

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>Wartość zwracana

Uchwyt do metapliku zawierającego kultowy aspekt zaznaczonego elementu, jeśli pole wyboru Wyświetl jako ikonę zostało zaznaczone, gdy okno dialogowe zostało odrzucone, wybierając **przycisk OK**; w przeciwnym razie NULL.

## <a name="colepastespecialdialoggetpasteindex"></a><a name="getpasteindex"></a>COlePasteSpecialDialog::GetPasteIndex

Pobiera wartość indeksu skojarzone z wpisem wybranym przez użytkownika.

```
int GetPasteIndex() const;
```

### <a name="return-value"></a>Wartość zwracana

Indeks do tablicy `OLEUIPASTEENTRY` struktur, który został wybrany przez użytkownika. Format odpowiadający wybranemu indeksowi powinien być używany podczas wykonywania operacji wklejania.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [strukturę OLEUIPASTEENTRY](/windows/win32/api/oledlg/ns-oledlg-oleuipasteentryw) w windows SDK.

## <a name="colepastespecialdialoggetselectiontype"></a><a name="getselectiontype"></a>COlePasteSpecialDialog::GetSelectionType

Określa typ dokonanego przez użytkownika.

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca typ dokonanego wyboru.

### <a name="remarks"></a>Uwagi

Wartości typu zwracane są `Selection` określone przez typ wyliczenia zadeklarowany w `COlePasteSpecialDialog` klasie.

```
enum Selection {
    pasteLink,
    pasteNormal,
    pasteOther,
    pasteStatic
    };
```

Krótkie ekskriptions tych wartości następują:

- `COlePasteSpecialDialog::pasteLink`Przycisk opcji Wklej link został sprawdzony, a wybrany format był standardowym formatem OLE.

- `COlePasteSpecialDialog::pasteNormal`Wklej przycisk opcji został sprawdzony, a wybrany format był standardowym formatem OLE.

- `COlePasteSpecialDialog::pasteOther`Wybrany format nie jest standardowym formatem OLE.

- `COlePasteSpecialDialog::pasteStatic`Wybranym formatem był metaplik.

## <a name="colepastespecialdialogm_ps"></a><a name="m_ps"></a>COlePasteSpecialDialog::m_ps

Struktura typu OLEUIPASTESPECIAL używana do kontrolowania zachowania okna dialogowego Wklej specjalne.

```
OLEUIPASTESPECIAL m_ps;
```

### <a name="remarks"></a>Uwagi

Elementy członkowskie tej struktury mogą być modyfikowane bezpośrednio lub za pośrednictwem funkcji członkowskich.

Aby uzyskać więcej informacji, zobacz [strukturę OLEUIPASTESPECIAL](/windows/win32/api/oledlg/ns-oledlg-oleuipastespecialw) w windows SDK.

## <a name="see-also"></a>Zobacz też

[Próbka MFC OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[Klasa COleDialog](../../mfc/reference/coledialog-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleDialog](../../mfc/reference/coledialog-class.md)
