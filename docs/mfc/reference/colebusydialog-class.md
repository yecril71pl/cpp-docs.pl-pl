---
title: Klasa COleBusyDialog
ms.date: 11/04/2016
f1_keywords:
- COleBusyDialog
- AFXODLGS/COleBusyDialog
- AFXODLGS/COleBusyDialog::COleBusyDialog
- AFXODLGS/COleBusyDialog::DoModal
- AFXODLGS/COleBusyDialog::GetSelectionType
- AFXODLGS/COleBusyDialog::m_bz
helpviewer_keywords:
- COleBusyDialog [MFC], COleBusyDialog
- COleBusyDialog [MFC], DoModal
- COleBusyDialog [MFC], GetSelectionType
- COleBusyDialog [MFC], m_bz
ms.assetid: c881a532-9672-4c41-b51b-5ce4a7246a6b
ms.openlocfilehash: aa3f0d85bcbf34d325125187b22b38c4da01fb43
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504408"
---
# <a name="colebusydialog-class"></a>Klasa COleBusyDialog

Używany w oknach dialogowych serwer nie odpowiada lub serwer jest zajęty.

## <a name="syntax"></a>Składnia

```
class COleBusyDialog : public COleDialog
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleBusyDialog::COleBusyDialog](#colebusydialog)|Konstruuje `COleBusyDialog` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleBusyDialog::D oModal](#domodal)|Wyświetla okno dialogowe zajęty serwer OLE.|
|[COleBusyDialog:: GetSelectionType](#getselectiontype)|Określa wybór dokonany w oknie dialogowym.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[COleBusyDialog::m_bz](#m_bz)|Struktura typu OLEUIBUSY, która kontroluje zachowanie okna dialogowego.|

## <a name="remarks"></a>Uwagi

Utwórz obiekt klasy `COleBusyDialog` , gdy chcesz wywołać te okna dialogowe. Po skonstruowaniu obiektu można użyć struktury m_bz, aby zainicjować wartości lub Stany kontrolek w oknie dialogowym. [](#m_bz) `COleBusyDialog` `m_bz` Struktura jest typu OLEUIBUSY. Aby uzyskać więcej informacji o używaniu tej klasy okna dialogowego, zobacz funkcja członkowska [DoModal](#domodal) .

> [!NOTE]
>  Kod kontenera wygenerowany przez Kreatora aplikacji używa tej klasy.

Aby uzyskać więcej informacji, zapoznaj się ze strukturą [OLEUIBUSY](/windows/win32/api/oledlg/ns-oledlg-oleuibusyw) w Windows SDK.

Aby uzyskać więcej informacji o oknach dialogowych specyficznych dla OLE, zobacz [okna dialogowe artykułu w OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleBusyDialog`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxodlgs. h

##  <a name="colebusydialog"></a>COleBusyDialog::COleBusyDialog

Ta funkcja konstruuje `COleBusyDialog` tylko obiekt.

```
explicit COleBusyDialog(
    HTASK htaskBusy,
    BOOL bNotResponding = FALSE,
    DWORD dwFlags = 0,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*htaskBusy*<br/>
Dojście do zadania serwera, które jest zajęte.

*bNotResponding*<br/>
W przypadku wartości TRUE należy wywołać okno dialogowe nie odpowiada, zamiast okna dialogowego zajęte serwera. Słowa w oknie dialogowym nie odpowiadają nieco różnić się od wyrazów w oknie dialogowym zajęty serwer i przycisk Anuluj jest wyłączony.

*flagiDW*<br/>
Flaga tworzenia. Może zawierać zero lub więcej z następujących wartości połączonych z operatorem bitowym lub:

- BZ_DISABLECANCELBUTTON Wyłącz przycisk Anuluj podczas wywoływania okna dialogowego.

- BZ_DISABLESWITCHTOBUTTON wyłączyć przycisk Przełącz do podczas wywoływania okna dialogowego.

- BZ_DISABLERETRYBUTTON wyłączyć przycisk Ponów próbę podczas wywoływania okna dialogowego.

*pParentWnd*<br/>
Wskazuje obiekt nadrzędny lub właściciel (typu `CWnd`), do którego należy obiekt okna dialogowego. Jeśli ma wartość NULL, okno nadrzędne obiektu okna dialogowego jest ustawione na główne okno aplikacji.

### <a name="remarks"></a>Uwagi

Aby wyświetlić okno dialogowe, wywołaj [DoModal](#domodal).

Aby uzyskać więcej informacji, zapoznaj się ze strukturą [OLEUIBUSY](/windows/win32/api/oledlg/ns-oledlg-oleuibusyw) w Windows SDK.

##  <a name="domodal"></a>COleBusyDialog::D oModal

Wywołaj tę funkcję, aby wyświetlić okno dialogowe zajęty serwer OLE lub serwer nie odpowiada.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Wartość zwracana

Stan ukończenia dla okna dialogowego. Jedna z następujących wartości:

- IDOK, jeśli okno dialogowe zostało wyświetlone pomyślnie.

- IDCANCEL, jeśli użytkownik anulował okno dialogowe.

- IDABORT, jeśli wystąpił błąd. Jeśli IDABORT jest zwracany, wywołaj `COleDialog::GetLastError` funkcję członkowską, aby uzyskać więcej informacji na temat typu błędu, który wystąpił. Listę możliwych błędów można znaleźć w funkcji [OLEUIBUSY](/windows/win32/api/oledlg/nf-oledlg-oleuibusyw) w Windows SDK.

### <a name="remarks"></a>Uwagi

Jeśli chcesz zainicjować różne kontrolki okna dialogowego, ustawiając elementy członkowskie struktury [m_bz](#m_bz) , należy to zrobić przed wywołaniem `DoModal`, ale po skonstruowaniu obiektu okna dialogowego.

Jeśli `DoModal` zwraca IDOK, można wywołać inne funkcje członkowskie, aby pobrać ustawienia lub informacje, które zostały wprowadzone przez użytkownika w oknie dialogowym.

##  <a name="getselectiontype"></a>COleBusyDialog:: GetSelectionType

Wywołaj tę funkcję, aby uzyskać typ wyboru wybrany przez użytkownika w oknie dialogowym zajęty serwer.

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>Wartość zwracana

Typ dokonanego wyboru.

### <a name="remarks"></a>Uwagi

Wartości typu zwracanego są określane przez `Selection` typ wyliczeniowy zadeklarowany `COleBusyDialog` w klasie.

```
enum Selection {
    switchTo,
    retry,
    callUnblocked
    };
```

Poniżej przedstawiono krótkie opisy następujących wartości:

- `COleBusyDialog::switchTo`Naciśnięto przycisk Przełącz do przycisku.

- `COleBusyDialog::retry`Kliknięto przycisk Ponów próbę.

- `COleBusyDialog::callUnblocked`Wywołanie aktywowania serwera jest teraz odblokowywane.

##  <a name="m_bz"></a>COleBusyDialog::m_bz

Struktura typu OLEUIBUSY używana do sterowania zachowaniem okna dialogowego zajęte przez serwer.

```
OLEUIBUSY m_bz;
```

### <a name="remarks"></a>Uwagi

Elementy członkowskie tej struktury mogą być modyfikowane bezpośrednio lub za poorednictwem funkcji składowych.

Aby uzyskać więcej informacji, zapoznaj się ze strukturą [OLEUIBUSY](/windows/win32/api/oledlg/ns-oledlg-oleuibusyw) w Windows SDK.

## <a name="see-also"></a>Zobacz także

[Klasa COleDialog](../../mfc/reference/coledialog-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleDialog](../../mfc/reference/coledialog-class.md)
