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
ms.openlocfilehash: 6cdc0ed6bfa4765817de8b7628f339db5e7e5bf5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369626"
---
# <a name="colechangeicondialog-class"></a>Klasa COleChangeIconDialog

Używane w oknie dialogowym Ikona zmiany OLE.

## <a name="syntax"></a>Składnia

```
class COleChangeIconDialog : public COleDialog
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleChangeIconDialog::COleChangeIconDialog](#colechangeicondialog)|Konstruuje `COleChangeIconDialog` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleChangeIconDialog::DoChangeIcon](#dochangeicon)|Wykonuje zmianę określoną w oknie dialogowym.|
|[COleChangeIconDialog::DoModal](#domodal)|Wyświetla okno dialogowe Ikona zmiany OLE 2.|
|[COleChangeIconDialog::GetIconicMetafile](#geticonicmetafile)|Pobiera uchwyt do metapliku skojarzonego z ikoniczną formą tego elementu.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[COleChangeIconDialog::m_ci](#m_ci)|Struktura, która kontroluje zachowanie okna dialogowego.|

## <a name="remarks"></a>Uwagi

Utwórz obiekt `COleChangeIconDialog` klasy, jeśli chcesz wywołać to okno dialogowe. Po `COleChangeIconDialog` skonstruowaniu obiektu można użyć struktury [m_ci](#m_ci) do zainicjowania wartości lub stanów formantów w oknie dialogowym. Struktura `m_ci` jest typu OLEUICHANGEICON. Aby uzyskać więcej informacji na temat korzystania z tej klasy okna dialogowego, zobacz Funkcję elementu członkowskiego [DoModal.](#domodal)

Aby uzyskać więcej informacji, zobacz strukturę [OLEUICHANGEICON](/windows/win32/api/oledlg/ns-oledlg-oleuichangeiconw) w sdk systemu Windows.

Aby uzyskać więcej informacji na temat okien dialogowych specyficznych dla ole, zobacz [artykuł Okna dialogowe w ole](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cdialog](../../mfc/reference/cdialog-class.md)

[CKlogialny](../../mfc/reference/ccommondialog-class.md)

[COleDialog (Polski)](../../mfc/reference/coledialog-class.md)

`COleChangeIconDialog`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxodlgs.h

## <a name="colechangeicondialogcolechangeicondialog"></a><a name="colechangeicondialog"></a>COleChangeIconDialog::COleChangeIconDialog

Ta funkcja konstruuje tylko `COleChangeIconDialog` obiekt.

```
explicit COleChangeIconDialog(
    COleClientItem* pItem,
    DWORD dwFlags = CIF_SELECTCURRENT,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*pItem (własówce)*<br/>
Wskazuje element do konwersji.

*Dwflags*<br/>
Flaga tworzenia, która zawiera dowolną liczbę następujących wartości połączonych za pomocą operatora bitowego lub operatora:

- CIF_SELECTCURRENT Określa, że przycisk Bieżący zostanie wybrany początkowo, gdy zostanie wywołane okno dialogowe. Domyślnie włączone.

- CIF_SELECTDEFAULT Określa, że domyślny przycisk opcji zostanie wybrany początkowo, gdy zostanie wywołane okno dialogowe.

- CIF_SELECTFROMFILE Określa, że przycisk opcji Od pliku zostanie wybrany początkowo po wywołaniu okna dialogowego.

- CIF_SHOWHELP Określa, że przycisk Pomoc będzie wyświetlany po wywołaniu okna dialogowego.

- CIF_USEICONEXE Określa, że ikona powinna zostać wyodrębniona z pliku `szIconExe` wykonywalnego określonego w polu [m_ci,](#m_ci) a nie pobrana z typu. Jest to przydatne do osadzania lub łączenia z plikami nienawiązanymi OLE.

*pParentWnd*<br/>
Wskazuje obiekt okna nadrzędnego lub `CWnd`właściciela (typu), do którego należy obiekt okna dialogowego. Jeśli jest null, okno nadrzędne okna dialogowego zostanie ustawiona na główne okno aplikacji.

### <a name="remarks"></a>Uwagi

Aby wyświetlić okno dialogowe, należy wywołać funkcję [DoModal.](#domodal)

Aby uzyskać więcej informacji, zobacz strukturę [OLEUICHANGEICON](/windows/win32/api/oledlg/ns-oledlg-oleuichangeiconw) w sdk systemu Windows.

## <a name="colechangeicondialogdochangeicon"></a><a name="dochangeicon"></a>COleChangeIconDialog::DoChangeIcon

Wywołanie tej funkcji, aby zmienić ikonę reprezentującą element do tej wybranej w oknie dialogowym po [domodal](#domodal) zwraca IDOK.

```
BOOL DoChangeIcon(COleClientItem* pItem);
```

### <a name="parameters"></a>Parametry

*pItem (własówce)*<br/>
Wskazuje element, którego ikona się zmienia.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli zmiana zakończy się pomyślnie; w przeciwnym razie 0.

## <a name="colechangeicondialogdomodal"></a><a name="domodal"></a>COleChangeIconDialog::DoModal

Wywołanie tej funkcji powoduje wyświetlenie okna dialogowego Ikona zmiany OLE.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Wartość zwracana

Stan ukończenia okna dialogowego. Jedna z następujących wartości:

- IDOK, jeśli okno dialogowe zostało pomyślnie wyświetlone.

- IDCANCEL, jeśli użytkownik anulował okno dialogowe.

- IDABORT, jeśli wystąpił błąd. Jeśli idabort jest zwracany, wywołać funkcję `COleDialog::GetLastError` elementu członkowskiego, aby uzyskać więcej informacji na temat typu błędu, który wystąpił. Aby uzyskać listę możliwych błędów, zobacz [OleUIChangeIcon](/windows/win32/api/oledlg/nf-oledlg-oleuichangeiconw) funkcji w zestawie Windows SDK.

### <a name="remarks"></a>Uwagi

Jeśli chcesz zainicjować różne formanty okna dialogowego, ustawiając elementy członkowskie [m_ci](#m_ci) `DoModal`struktury, należy to zrobić przed wywołaniem , ale po skonstruowaniu obiektu okna dialogowego.

Jeśli `DoModal` zwraca IDOK, można wywołać inne funkcje członkowskie, aby pobrać ustawienia lub informacje, które zostały wprowadzone przez użytkownika w oknie dialogowym.

## <a name="colechangeicondialoggeticonicmetafile"></a><a name="geticonicmetafile"></a>COleChangeIconDialog::GetIconicMetafile

Wywołanie tej funkcji, aby uzyskać uchwyt do metapliku, który zawiera kultowy aspekt wybranego elementu.

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>Wartość zwracana

Uchwyt do metapliku zawierającego kultowy aspekt nowej ikony, jeśli okno dialogowe zostało odrzucone, wybierając **PRZYCISK OK**; w przeciwnym razie ikona, jak to było przed wyświetleniem okna dialogowego.

## <a name="colechangeicondialogm_ci"></a><a name="m_ci"></a>COleChangeIconDialog::m_ci

Struktura typu OLEUICHANGEICON używana do kontrolowania zachowania okna dialogowego Zmień ikonę.

```
OLEUICHANGEICON m_ci;
```

### <a name="remarks"></a>Uwagi

Elementy członkowskie tej struktury mogą być modyfikowane bezpośrednio lub za pośrednictwem funkcji członkowskich.

Aby uzyskać więcej informacji, zobacz strukturę [OLEUICHANGEICON](/windows/win32/api/oledlg/ns-oledlg-oleuichangeiconw) w sdk systemu Windows.

## <a name="see-also"></a>Zobacz też

[Klasa COleDialog](../../mfc/reference/coledialog-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleDialog](../../mfc/reference/coledialog-class.md)
