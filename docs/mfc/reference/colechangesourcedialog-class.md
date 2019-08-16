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
ms.openlocfilehash: 239d7eed89796f414a7665b203ca50fafec51277
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504385"
---
# <a name="colechangesourcedialog-class"></a>Klasa COleChangeSourceDialog

Używane dla źródła zmiany OLE okno dialogowe.

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
|[COleChangeSourceDialog::D oModal](#domodal)|Wyświetla okno dialogowe Źródło zmian OLE.|
|[COleChangeSourceDialog:: GetDisplayName](#getdisplayname)|Pobiera pełną nazwę wyświetlaną źródła.|
|[COleChangeSourceDialog::GetFileName](#getfilename)|Pobiera nazwę pliku z nazwy źródłowej.|
|[COleChangeSourceDialog::GetFromPrefix](#getfromprefix)|Pobiera prefiks poprzedniego źródła.|
|[COleChangeSourceDialog:: getitemname](#getitemname)|Pobiera nazwę elementu z nazwy źródłowej.|
|[COleChangeSourceDialog::GetToPrefix](#gettoprefix)|Pobiera prefiks nowego źródła|
|[COleChangeSourceDialog::IsValidSource](#isvalidsource)|Wskazuje, czy źródło jest prawidłowe.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[COleChangeSourceDialog::m_cs](#m_cs)|Struktura, która kontroluje zachowanie okna dialogowego.|

## <a name="remarks"></a>Uwagi

Utwórz obiekt klasy `COleChangeSourceDialog` , gdy chcesz wywołać to okno dialogowe. Po skonstruowaniu obiektu można użyć struktury m_cs, aby zainicjować wartości lub Stany kontrolek w oknie dialogowym. [](#m_cs) `COleChangeSourceDialog` Struktura jest typu OLEUICHANGESOURCE. [](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) `m_cs` Aby uzyskać więcej informacji o używaniu tej klasy okna dialogowego, zobacz funkcja członkowska [DoModal](#domodal) .

Aby uzyskać więcej informacji, zapoznaj się ze strukturą [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) w Windows SDK.

Aby uzyskać więcej informacji o oknach dialogowych specyficznych dla OLE, zobacz [okna dialogowe artykułu w OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleChangeSourceDialog`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxodlgs. h

##  <a name="colechangesourcedialog"></a>COleChangeSourceDialog::COleChangeSourceDialog

Ta funkcja konstruuje `COleChangeSourceDialog` obiekt.

```
explicit COleChangeSourceDialog(
    COleClientItem* pItem,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*pItem*<br/>
Wskaźnik do połączonej [COleClientItem](../../mfc/reference/coleclientitem-class.md) , którego źródło ma zostać zaktualizowane.

*pParentWnd*<br/>
Wskazuje obiekt nadrzędny lub właściciel (typu `CWnd`), do którego należy obiekt okna dialogowego. Jeśli ma wartość NULL, okno dialogowe nadrzędne okna dialogowego zostanie ustawione na główne okno aplikacji.

### <a name="remarks"></a>Uwagi

Aby wyświetlić okno dialogowe, wywołaj funkcję [DoModal](#domodal) .

Aby uzyskać więcej informacji, zobacz [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) Structure and [OLEUICHANGESOURCE](/windows/win32/api/oledlg/nf-oledlg-oleuichangesourcew) function in w Windows SDK.

##  <a name="domodal"></a>COleChangeSourceDialog::D oModal

Wywołaj tę funkcję, aby wyświetlić okno dialogowe Źródło zmian OLE.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Wartość zwracana

Stan ukończenia dla okna dialogowego. Jedna z następujących wartości:

- IDOK, jeśli okno dialogowe zostało wyświetlone pomyślnie.

- IDCANCEL, jeśli użytkownik anulował okno dialogowe.

- IDABORT, jeśli wystąpił błąd. Jeśli IDABORT jest zwracany, wywołaj funkcję członkowską [COleDialog:: GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) , aby uzyskać więcej informacji na temat typu błędu, który wystąpił. Listę możliwych błędów można znaleźć w funkcji [OLEUICHANGESOURCE](/windows/win32/api/oledlg/nf-oledlg-oleuichangesourcew) w Windows SDK.

### <a name="remarks"></a>Uwagi

Jeśli chcesz zainicjować różne kontrolki okna dialogowego, ustawiając elementy członkowskie struktury [m_cs](#m_cs) , należy to zrobić przed wywołaniem `DoModal`, ale po skonstruowaniu obiektu okna dialogowego.

Jeśli `DoModal` zwraca IDOK, można wywołać funkcje członkowskie, aby pobrać ustawienia wprowadzone przez użytkownika lub informacje z okna dialogowego. Następujące nazwy list typowe funkcje zapytania:

- [GetFileName](#getfilename)

- [GetDisplayName](#getdisplayname)

- [GetItemName](#getitemname)

##  <a name="getdisplayname"></a>COleChangeSourceDialog:: GetDisplayName

Wywołaj tę funkcję, aby pobrać pełną nazwę wyświetlaną dla połączonego elementu klienta.

```
CString GetDisplayName();
```

### <a name="return-value"></a>Wartość zwracana

Pełna źródłowa nazwa wyświetlana (moniker) dla [COleClientItem](../../mfc/reference/coleclientitem-class.md) określonego w konstruktorze.

##  <a name="getfilename"></a>COleChangeSourceDialog:: GetFileName

Wywołaj tę funkcję, aby pobrać część nazwy wyświetlanej dla połączonego elementu klienta.

```
CString GetFileName();
```

### <a name="return-value"></a>Wartość zwracana

Część monikera pliku źródłowej nazwy wyświetlanej dla [COleClientItem](../../mfc/reference/coleclientitem-class.md) określonego w konstruktorze.

### <a name="remarks"></a>Uwagi

Moniker pliku wraz z monikerem elementu zawiera pełną nazwę wyświetlaną.

##  <a name="getfromprefix"></a>COleChangeSourceDialog::GetFromPrefix

Wywołaj tę funkcję, aby pobrać poprzedni ciąg prefiksu dla źródła.

```
CString GetFromPrefix();
```

### <a name="return-value"></a>Wartość zwracana

Poprzedni ciąg prefiksu źródła.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję tylko po [DoModal](#domodal) zwraca IDOK.

Ta wartość jest pobierana bezpośrednio `lpszFrom` z elementu członkowskiego struktury [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) .

Aby uzyskać więcej informacji, zapoznaj się ze strukturą [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) w Windows SDK.

##  <a name="getitemname"></a>COleChangeSourceDialog:: getitemname

Wywołaj tę funkcję, aby pobrać część nazwy wyświetlanej dla połączonego elementu klienta.

```
CString GetItemName();
```

### <a name="return-value"></a>Wartość zwracana

Część monikera elementu źródłowej nazwy wyświetlanej dla [COleClientItem](../../mfc/reference/coleclientitem-class.md) określonego w konstruktorze.

### <a name="remarks"></a>Uwagi

Moniker pliku wraz z monikerem elementu zawiera pełną nazwę wyświetlaną.

##  <a name="gettoprefix"></a>COleChangeSourceDialog::GetToPrefix

Wywołaj tę funkcję, aby uzyskać nowy ciąg prefiksu dla źródła.

```
CString GetToPrefix();
```

### <a name="return-value"></a>Wartość zwracana

Nowy ciąg prefiksu źródła.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję tylko po [DoModal](#domodal) zwraca IDOK.

Ta wartość jest pobierana bezpośrednio `lpszTo` z elementu członkowskiego struktury [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) .

Aby uzyskać więcej informacji, zapoznaj się ze strukturą [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) w Windows SDK.

##  <a name="m_cs"></a>COleChangeSourceDialog::m_cs

Ten element członkowski danych jest strukturą typu [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew).

```
OLEUICHANGESOURCE m_cs;
```

### <a name="remarks"></a>Uwagi

`OLEUICHANGESOURCE`służy do sterowania zachowaniem okna dialogowego źródła zmian OLE. Elementy członkowskie tej struktury można modyfikować bezpośrednio.

Aby uzyskać więcej informacji, zapoznaj się ze strukturą [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) w Windows SDK.

##  <a name="isvalidsource"></a>COleChangeSourceDialog::IsValidSource

Wywołaj tę funkcję, aby określić, czy nowe źródło jest prawidłowe.

```
BOOL IsValidSource();
```

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli nowe źródło jest prawidłowe, w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję tylko po [DoModal](#domodal) zwraca IDOK.

Aby uzyskać więcej informacji, zapoznaj się ze strukturą [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) w Windows SDK.

## <a name="see-also"></a>Zobacz także

[Klasa COleDialog](../../mfc/reference/coledialog-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleDialog](../../mfc/reference/coledialog-class.md)
