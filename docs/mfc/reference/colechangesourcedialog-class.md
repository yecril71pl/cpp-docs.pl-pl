---
title: Klasa COleChangeSourceDialog
ms.date: 11/04/2016
f1_keywords:
- COleChangeSourceDialog
- AFXODLGS/COleChangeSourceDialog
- AFXODLGS/COleChangeSourceDialog::COleChangeSourceDialog
- AFXODLGS/COleChangeSourceDialog::DoModal
- AFXODLGS/COleChangeSourceDialog::GetDisplayName
- AFXODLGS/COleChangeSourceDialog::GetFileName
- AFXODLGS/COleChangeSourceDialog::GetFromPrefix
- AFXODLGS/COleChangeSourceDialog::GetItemName
- AFXODLGS/COleChangeSourceDialog::GetToPrefix
- AFXODLGS/COleChangeSourceDialog::IsValidSource
- AFXODLGS/COleChangeSourceDialog::m_cs
helpviewer_keywords:
- COleChangeSourceDialog [MFC], COleChangeSourceDialog
- COleChangeSourceDialog [MFC], DoModal
- COleChangeSourceDialog [MFC], GetDisplayName
- COleChangeSourceDialog [MFC], GetFileName
- COleChangeSourceDialog [MFC], GetFromPrefix
- COleChangeSourceDialog [MFC], GetItemName
- COleChangeSourceDialog [MFC], GetToPrefix
- COleChangeSourceDialog [MFC], IsValidSource
- COleChangeSourceDialog [MFC], m_cs
ms.assetid: d0e08be7-21ef-45e1-97af-fe27d99e3bac
ms.openlocfilehash: 78da0a495de6ea951deab984550756a2d6f3e2bd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321870"
---
# <a name="colechangesourcedialog-class"></a>Klasa COleChangeSourceDialog

Używane w oknie dialogowym Źródło zmiany OLE.

## <a name="syntax"></a>Składnia

```
class COleChangeSourceDialog : public COleDialog
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleChangeSourceDialog::COleChangeSourceDialog](#colechangesourcedialog)|Konstruuje `COleChangeSourceDialog` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleChangeSourceDialog::DoModal](#domodal)|Wyświetla okno dialogowe Źródło zmiany OLE.|
|[COleChangeSourceDialog::GetDisplayName](#getdisplayname)|Pobiera pełną nazwę wyświetlaną źródła.|
|[COleChangeSourceDialog::GetFileName](#getfilename)|Pobiera nazwę pliku z nazwy źródła.|
|[COleChangeSourceDialog::GetFromPrefix](#getfromprefix)|Pobiera prefiks poprzedniego źródła.|
|[COleChangeSourceDialog::GetItemName](#getitemname)|Pobiera nazwę elementu od nazwy źródła.|
|[COleChangeSourceDialog::GetToPrefix](#gettoprefix)|Pobiera prefiks nowego źródła|
|[COleChangeSourceDialog::IsValidSource](#isvalidsource)|Wskazuje, czy źródło jest prawidłowe.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[COleChangeSourceDialog::m_cs](#m_cs)|Struktura, która kontroluje zachowanie okna dialogowego.|

## <a name="remarks"></a>Uwagi

Utwórz obiekt `COleChangeSourceDialog` klasy, jeśli chcesz wywołać to okno dialogowe. Po `COleChangeSourceDialog` skonstruowaniu obiektu można użyć struktury [m_cs](#m_cs) do zainicjowania wartości lub stanów formantów w oknie dialogowym. Struktura `m_cs` jest typu [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew). Aby uzyskać więcej informacji na temat korzystania z tej klasy okna dialogowego, zobacz Funkcję elementu członkowskiego [DoModal.](#domodal)

Aby uzyskać więcej informacji, zobacz STRUKTURĘ [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) w windows SDK.

Aby uzyskać więcej informacji na temat okien dialogowych specyficznych dla ole, zobacz [artykuł Okna dialogowe w ole](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cdialog](../../mfc/reference/cdialog-class.md)

[CKlogialny](../../mfc/reference/ccommondialog-class.md)

[COleDialog (Polski)](../../mfc/reference/coledialog-class.md)

`COleChangeSourceDialog`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxodlgs.h

## <a name="colechangesourcedialogcolechangesourcedialog"></a><a name="colechangesourcedialog"></a>COleChangeSourceDialog::COleChangeSourceDialog

Ta funkcja konstruuje `COleChangeSourceDialog` obiekt.

```
explicit COleChangeSourceDialog(
    COleClientItem* pItem,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*pItem (własówce)*<br/>
Wskaźnik do połączonego [COleClientItem,](../../mfc/reference/coleclientitem-class.md) którego źródło ma zostać zaktualizowane.

*pParentWnd*<br/>
Wskazuje obiekt okna nadrzędnego lub `CWnd`właściciela (typu), do którego należy obiekt okna dialogowego. Jeśli jest null, okno nadrzędne okna dialogowego zostanie ustawiona na główne okno aplikacji.

### <a name="remarks"></a>Uwagi

Aby wyświetlić okno dialogowe, należy wywołać funkcję [DoModal.](#domodal)

Aby uzyskać więcej informacji, zobacz [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) struktury i [OleUIChangeSource](/windows/win32/api/oledlg/nf-oledlg-oleuichangesourcew) funkcji w windows SDK.

## <a name="colechangesourcedialogdomodal"></a><a name="domodal"></a>COleChangeSourceDialog::DoModal

Wywołanie tej funkcji powoduje wyświetlenie okna dialogowego Ole Change Source.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Wartość zwracana

Stan ukończenia okna dialogowego. Jedna z następujących wartości:

- IDOK, jeśli okno dialogowe zostało pomyślnie wyświetlone.

- IDCANCEL, jeśli użytkownik anulował okno dialogowe.

- IDABORT, jeśli wystąpił błąd. Jeśli idabort jest zwracany, wywołać [COleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) funkcji elementu członkowskiego, aby uzyskać więcej informacji na temat typu błędu, który wystąpił. Aby uzyskać listę możliwych błędów, zobacz [OleUIChangeSource](/windows/win32/api/oledlg/nf-oledlg-oleuichangesourcew) funkcji w zestawie Windows SDK.

### <a name="remarks"></a>Uwagi

Jeśli chcesz zainicjować różne formanty okna dialogowego, ustawiając elementy członkowskie [m_cs](#m_cs) `DoModal`struktury, należy to zrobić przed wywołaniem , ale po skonstruowaniu obiektu okna dialogowego.

Jeśli `DoModal` zwraca IDOK, można wywołać funkcje członkowskie, aby pobrać wprowadzone przez użytkownika ustawienia lub informacje z okna dialogowego. Następująca lista wymienia typowe funkcje kwerendy:

- [GetFileName](#getfilename)

- [Nazwa GetDisplay](#getdisplayname)

- [Nazwa GetItem](#getitemname)

## <a name="colechangesourcedialoggetdisplayname"></a><a name="getdisplayname"></a>COleChangeSourceDialog::GetDisplayName

Wywołanie tej funkcji, aby pobrać pełną nazwę wyświetlaną dla połączonego elementu klienta.

```
CString GetDisplayName();
```

### <a name="return-value"></a>Wartość zwracana

Pełna nazwa wyświetlana źródła (moniker) dla [COleClientItem](../../mfc/reference/coleclientitem-class.md) określony w konstruktorze.

## <a name="colechangesourcedialoggetfilename"></a><a name="getfilename"></a>COleChangeSourceDialog::GetFileName

Wywołanie tej funkcji, aby pobrać część moniker pliku nazwy wyświetlanej dla połączonego elementu klienta.

```
CString GetFileName();
```

### <a name="return-value"></a>Wartość zwracana

Część moniker pliku nazwy wyświetlania źródła dla [COleClientItem](../../mfc/reference/coleclientitem-class.md) określony w konstruktorze.

### <a name="remarks"></a>Uwagi

Moniker pliku wraz z monikerem elementu podaje pełną nazwę wyświetlaną.

## <a name="colechangesourcedialoggetfromprefix"></a><a name="getfromprefix"></a>COleChangeSourceDialog::GetFromPrefix

Wywołanie tej funkcji, aby uzyskać poprzedni ciąg prefiksu dla źródła.

```
CString GetFromPrefix();
```

### <a name="return-value"></a>Wartość zwracana

Poprzedni ciąg prefiksu źródła.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji tylko po [DoModal](#domodal) zwraca IDOK.

Ta wartość pochodzi bezpośrednio `lpszFrom` z elementu członkowskiego [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) struktury.

Aby uzyskać więcej informacji, zobacz STRUKTURĘ [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) w windows SDK.

## <a name="colechangesourcedialoggetitemname"></a><a name="getitemname"></a>COleChangeSourceDialog::GetItemName

Wywołanie tej funkcji, aby pobrać część moniker elementu nazwy wyświetlanej dla połączonego elementu klienta.

```
CString GetItemName();
```

### <a name="return-value"></a>Wartość zwracana

Element moniker część nazwy wyświetlania źródła dla [COleClientItem](../../mfc/reference/coleclientitem-class.md) określony w konstruktorze.

### <a name="remarks"></a>Uwagi

Moniker pliku wraz z monikerem elementu podaje pełną nazwę wyświetlaną.

## <a name="colechangesourcedialoggettoprefix"></a><a name="gettoprefix"></a>COleChangeSourceDialog::GetToPrefix

Wywołanie tej funkcji, aby uzyskać nowy ciąg prefiksu dla źródła.

```
CString GetToPrefix();
```

### <a name="return-value"></a>Wartość zwracana

Nowy ciąg prefiksu źródła.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji tylko po [DoModal](#domodal) zwraca IDOK.

Ta wartość pochodzi bezpośrednio `lpszTo` z elementu członkowskiego [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) struktury.

Aby uzyskać więcej informacji, zobacz STRUKTURĘ [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) w windows SDK.

## <a name="colechangesourcedialogm_cs"></a><a name="m_cs"></a>COleChangeSourceDialog::m_cs

Ten element członkowski danych jest strukturą typu [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew).

```
OLEUICHANGESOURCE m_cs;
```

### <a name="remarks"></a>Uwagi

`OLEUICHANGESOURCE`służy do kontrolowania zachowania okna dialogowego Ole Change Source. Elementy członkowskie tej struktury mogą być modyfikowane bezpośrednio.

Aby uzyskać więcej informacji, zobacz STRUKTURĘ [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) w windows SDK.

## <a name="colechangesourcedialogisvalidsource"></a><a name="isvalidsource"></a>COleChangeSourceDialog::IsValidSource

Wywołanie tej funkcji, aby ustalić, czy nowe źródło jest prawidłowe.

```
BOOL IsValidSource();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli nowe źródło jest prawidłowe, w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji tylko po [DoModal](#domodal) zwraca IDOK.

Aby uzyskać więcej informacji, zobacz STRUKTURĘ [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) w windows SDK.

## <a name="see-also"></a>Zobacz też

[Klasa COleDialog](../../mfc/reference/coledialog-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleDialog](../../mfc/reference/coledialog-class.md)
