---
title: Klasa COleChangeIconDialog
ms.date: 11/04/2016
f1_keywords:
- COleChangeIconDialog
- AFXODLGS/COleChangeIconDialog
- AFXODLGS/COleChangeIconDialog::COleChangeIconDialog
- AFXODLGS/COleChangeIconDialog::DoChangeIcon
- AFXODLGS/COleChangeIconDialog::DoModal
- AFXODLGS/COleChangeIconDialog::GetIconicMetafile
- AFXODLGS/COleChangeIconDialog::m_ci
helpviewer_keywords:
- COleChangeIconDialog [MFC], COleChangeIconDialog
- COleChangeIconDialog [MFC], DoChangeIcon
- COleChangeIconDialog [MFC], DoModal
- COleChangeIconDialog [MFC], GetIconicMetafile
- COleChangeIconDialog [MFC], m_ci
ms.assetid: 8d6e131b-ddbb-4dff-a432-f239efda8e3d
ms.openlocfilehash: a319dc0612f68c4d513b7d5ab36ecf67a854bda9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50433647"
---
# <a name="colechangeicondialog-class"></a>Klasa COleChangeIconDialog

Stosowane dla okna dialogowego OLE Zmień ikonę.

## <a name="syntax"></a>Składnia

```
class COleChangeIconDialog : public COleDialog
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleChangeIconDialog::COleChangeIconDialog](#colechangeicondialog)|Konstruuje `COleChangeIconDialog` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleChangeIconDialog::DoChangeIcon](#dochangeicon)|Wykonuje zmian określona w oknie dialogowym.|
|[COleChangeIconDialog::DoModal](#domodal)|Wyświetla okno dialogowe OLE 2 Zmień ikonę.|
|[COleChangeIconDialog::GetIconicMetafile](#geticonicmetafile)|Pobiera uchwyt do metaplik skojarzony z formularzem ikony tego elementu.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[COleChangeIconDialog::m_ci](#m_ci)|Struktura, która steruje zachowaniem okno dialogowe.|

## <a name="remarks"></a>Uwagi

Utwórz obiekt klasy `COleChangeIconDialog` umożliwia wywołanie tego okna dialogowego. Po `COleChangeIconDialog` obiekt został skonstruowany, możesz użyć [m_ci](#m_ci) strukturę, aby zainicjować wartości lub stany formantów w oknie dialogowym. `m_ci` Struktury jest typu OLEUICHANGEICON. Aby uzyskać więcej informacji o korzystaniu z tej klasy okien dialogowych, zobacz [DoModal](#domodal) funkcja elementu członkowskiego.

Aby uzyskać więcej informacji, zobacz [OLEUICHANGEICON](/windows/desktop/api/oledlg/ns-oledlg-tagoleuichangeicona) struktury w zestawie Windows SDK.

Aby uzyskać więcej informacji o okna dialogowe OLE specyficzne artykuł [okna dialogowe w OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleChangeIconDialog`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxodlgs.h

##  <a name="colechangeicondialog"></a>  COleChangeIconDialog::COleChangeIconDialog

Ta funkcja tworzy tylko `COleChangeIconDialog` obiektu.

```
explicit COleChangeIconDialog(
    COleClientItem* pItem,
    DWORD dwFlags = CIF_SELECTCURRENT,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*pItem*<br/>
Wskazuje element, który ma zostać przekonwertowany.

*Flagidw*<br/>
Flagi tworzenia zawiera dowolną liczbę następujące wartości łączyć, używając operatora testu koniunkcji — lub operator:

- CIF_SELECTCURRENT Określa, że bieżący przycisk radiowy zostanie wybrany początkowo, gdy okno dialogowe jest wywoływana. Domyślnie włączone.

- CIF_SELECTDEFAULT Określa, że domyślny przycisk radiowy zostanie wybrany początkowo, gdy okno dialogowe jest wywoływana.

- CIF_SELECTFROMFILE Określa, że przycisk radiowy z pliku będzie wybrać wstępnie, gdy okno dialogowe jest wywoływana.

- CIF_SHOWHELP Określa, że przycisk Pomoc, będą wyświetlane, gdy wywoływana jest okno dialogowe.

- CIF_USEICONEXE Określa, że ikona mają zostać wyodrębnione z pliku wykonywalnego, określony w `szIconExe` pole [m_ci](#m_ci) zamiast pobranej z typu. Jest to przydatne w przypadku osadzania lub łącza do plików innych niż OLE.

*pParentWnd*<br/>
Wskazuje na obiekt okna nadrzędnego lub właściciela (typu `CWnd`) do którego należy obiekt okna dialogowego. Jeśli ma wartość NULL, okno nadrzędne, okno dialogowe zostanie ustawiona do okna głównego aplikacji.

### <a name="remarks"></a>Uwagi

Aby wyświetlić okno dialogowe, należy wywołać [DoModal](#domodal) funkcji.

Aby uzyskać więcej informacji, zobacz [OLEUICHANGEICON](/windows/desktop/api/oledlg/ns-oledlg-tagoleuichangeicona) struktury w zestawie Windows SDK.

##  <a name="dochangeicon"></a>  COleChangeIconDialog::DoChangeIcon

Wywołaj tę funkcję, aby zmienić ikonę reprezentujący elementu wybranego w oknie dialogowym po [DoModal](#domodal) zwraca IDOK.

```
BOOL DoChangeIcon(COleClientItem* pItem);
```

### <a name="parameters"></a>Parametry

*pItem*<br/>
Wskazuje element, którego ikonę ulega zmianie.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli zmiana jest kończy się pomyślnie; w przeciwnym razie 0.

##  <a name="domodal"></a>  COleChangeIconDialog::DoModal

Wywołaj tę funkcję, aby wyświetlić okna dialogowego OLE Zmień ikonę.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Wartość zwracana

Stan ukończenia dla okna dialogowego. Jeden z następujących wartości:

- IDOK, jeśli pomyślnie zostało wyświetlone okno dialogowe.

- IDCANCEL, jeśli użytkownik anulował okno dialogowe.

- IDABORT, jeśli wystąpił błąd. Jeśli zwracana jest IDABORT, wywołaj `COleDialog::GetLastError` funkcja elementu członkowskiego, aby uzyskać więcej informacji o typie błędu, który wystąpił. Aby uzyskać listę możliwych błędów, zobacz [OleUIChangeIcon](/windows/desktop/api/oledlg/nf-oledlg-oleuichangeicona) funkcji w zestawie Windows SDK.

### <a name="remarks"></a>Uwagi

Aby inicjowanie różne formanty okna dialogowego, ustawiając członkowie [m_ci](#m_ci) struktury, należy to zrobić przed wywołaniem `DoModal`, ale po jest konstruowany obiektu okna dialogowego.

Jeśli `DoModal` zwraca IDOK, może wywołać inny członek funkcje, które można pobrać ustawień lub informacje, które zostało wprowadzone przez użytkownika do okna dialogowego.

##  <a name="geticonicmetafile"></a>  COleChangeIconDialog::GetIconicMetafile

Wywołaj tę funkcję można pobrać uchwytu do metaplik, który zawiera ikony aspektów wybranego elementu.

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>Wartość zwracana

Dojście do Metaplik zawierający ikony aspekt nową ikonę, jeśli okno dialogowe został odrzucony, wybierając **OK**; w przeciwnym razie ikona, ponieważ był przed został wyświetlony w oknie dialogowym.

##  <a name="m_ci"></a>  COleChangeIconDialog::m_ci

Struktury typu OLEUICHANGEICON używane do sterowania zachowaniem okno dialogowe Zmienianie ikony.

```
OLEUICHANGEICON m_ci;
```

### <a name="remarks"></a>Uwagi

Elementy członkowskie tej struktury można zmodyfikować bezpośrednio lub za pośrednictwem funkcji elementów członkowskich.

Aby uzyskać więcej informacji, zobacz [OLEUICHANGEICON](/windows/desktop/api/oledlg/ns-oledlg-tagoleuichangeicona) struktury w zestawie Windows SDK.

## <a name="see-also"></a>Zobacz też

[Klasa COleDialog](../../mfc/reference/coledialog-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleDialog](../../mfc/reference/coledialog-class.md)
