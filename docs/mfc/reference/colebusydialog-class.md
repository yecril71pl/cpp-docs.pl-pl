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
ms.openlocfilehash: 5be42463c08cacd83de84900fb4d98771774e897
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364243"
---
# <a name="colebusydialog-class"></a>Klasa COleBusyDialog

Używane w oknach dialogowych Nie odpowiadanie serwera OLE lub Zajęty serwer.

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
|[COleBusyDialog::DoModal](#domodal)|Wyświetla okno dialogowe Zajęty serwer OLE.|
|[COleBusyDialog::GetSelectionType](#getselectiontype)|Określa wybór dokonany w oknie dialogowym.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[COleBusyDialog::m_bz](#m_bz)|Struktura typu OLEUIBUSY, który kontroluje zachowanie okna dialogowego.|

## <a name="remarks"></a>Uwagi

Utwórz obiekt `COleBusyDialog` klasy, gdy chcesz wywołać te okna dialogowe. Po `COleBusyDialog` skonstruowaniu obiektu można użyć struktury [m_bz](#m_bz) do zainicjowania wartości lub stanów formantów w oknie dialogowym. Struktura `m_bz` jest typu OLEUIBUSY. Aby uzyskać więcej informacji na temat korzystania z tej klasy okna dialogowego, zobacz Funkcję elementu członkowskiego [DoModal.](#domodal)

> [!NOTE]
> Kod kontenera generowany przez Kreatora aplikacji używa tej klasy.

Aby uzyskać więcej informacji, zobacz [OLEUIBUSY](/windows/win32/api/oledlg/ns-oledlg-oleuibusyw) struktury w windows SDK.

Aby uzyskać więcej informacji na temat okien dialogowych specyficznych dla ole, zobacz [artykuł Okna dialogowe w OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cdialog](../../mfc/reference/cdialog-class.md)

[CKlogialny](../../mfc/reference/ccommondialog-class.md)

[COleDialog (Polski)](../../mfc/reference/coledialog-class.md)

`COleBusyDialog`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxodlgs.h

## <a name="colebusydialogcolebusydialog"></a><a name="colebusydialog"></a>COleBusyDialog::COleBusyDialog

Ta funkcja tworzy `COleBusyDialog` tylko obiekt.

```
explicit COleBusyDialog(
    HTASK htaskBusy,
    BOOL bNotResponding = FALSE,
    DWORD dwFlags = 0,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*htaskBusy (htaskBusy)*<br/>
Obsługa zadania serwera, który jest zajęty.

*bNiereagowanie*<br/>
Jeśli wartość TRUE, wywołanie okna dialogowego Nie odpowiadanie zamiast okna dialogowego Zajęty serwer. Sformułowanie w oknie dialogowym Nie odpowiadanie jest nieco inne niż sformułowanie w oknie dialogowym Zajęty serwer, a przycisk Anuluj jest wyłączony.

*Dwflags*<br/>
Flaga tworzenia. Może zawierać zero lub więcej z następujących wartości w połączeniu z operatorem bitowym-OR:

- BZ_DISABLECANCELBUTTON Wyłącz przycisk Anuluj podczas wywoływania okna dialogowego.

- BZ_DISABLESWITCHTOBUTTON Wyłącz przycisk Przełącz do podczas wywoływania okna dialogowego.

- BZ_DISABLERETRYBUTTON Wyłącz przycisk Ponów próbę podczas wywoływania okna dialogowego.

*pParentWnd*<br/>
Wskazuje obiekt okna nadrzędnego lub `CWnd`właściciela (typu), do którego należy obiekt okna dialogowego. Jeśli jest null, okno nadrzędne obiektu okna dialogowego jest ustawiona na główne okno aplikacji.

### <a name="remarks"></a>Uwagi

Aby wyświetlić okno dialogowe, zadzwoń do [DoModal](#domodal).

Aby uzyskać więcej informacji, zobacz [OLEUIBUSY](/windows/win32/api/oledlg/ns-oledlg-oleuibusyw) struktury w windows SDK.

## <a name="colebusydialogdomodal"></a><a name="domodal"></a>COleBusyDialog::DoModal

Wywołanie tej funkcji powoduje wyświetlenie okna dialogowego Ole Server Busy lub Server Not Responding.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Wartość zwracana

Stan ukończenia okna dialogowego. Jedna z następujących wartości:

- IDOK, jeśli okno dialogowe zostało pomyślnie wyświetlone.

- IDCANCEL, jeśli użytkownik anulował okno dialogowe.

- IDABORT, jeśli wystąpił błąd. Jeśli idabort jest zwracany, wywołać funkcję `COleDialog::GetLastError` elementu członkowskiego, aby uzyskać więcej informacji na temat typu błędu, który wystąpił. Aby uzyskać listę możliwych błędów, zobacz [OleUIBusy](/windows/win32/api/oledlg/nf-oledlg-oleuibusyw) funkcji w zestawie Windows SDK.

### <a name="remarks"></a>Uwagi

Jeśli chcesz zainicjować różne formanty okna dialogowego, ustawiając elementy członkowskie [m_bz](#m_bz) struktury, należy to zrobić przed wywołaniem `DoModal`, ale po skonstruowaniu obiektu okna dialogowego.

Jeśli `DoModal` zwraca IDOK, można wywołać inne funkcje członkowskie, aby pobrać ustawienia lub informacje, które zostały wprowadzone przez użytkownika w oknie dialogowym.

## <a name="colebusydialoggetselectiontype"></a><a name="getselectiontype"></a>COleBusyDialog::GetSelectionType

Wywołanie tej funkcji, aby uzyskać typ wyboru wybrany przez użytkownika w oknie dialogowym Zajęty serwer.

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>Wartość zwracana

Typ dokonanego wyboru.

### <a name="remarks"></a>Uwagi

Wartości typu zwracane są `Selection` określone przez typ wyliczenia zadeklarowany w `COleBusyDialog` klasie.

```
enum Selection {
    switchTo,
    retry,
    callUnblocked
    };
```

Krótkie opisy tych wartości są następujące:

- `COleBusyDialog::switchTo`Naciśnięty został przycisk Przełącz na.

- `COleBusyDialog::retry`Naciśnięty został przycisk Ponów próbę.

- `COleBusyDialog::callUnblocked`Wywołanie, aby aktywować serwer jest teraz odblokowany.

## <a name="colebusydialogm_bz"></a><a name="m_bz"></a>COleBusyDialog::m_bz

Struktura typu OLEUIBUSY używana do kontrolowania zachowania okna dialogowego Zajęty serwer.

```
OLEUIBUSY m_bz;
```

### <a name="remarks"></a>Uwagi

Elementy członkowskie tej struktury mogą być modyfikowane bezpośrednio lub za pośrednictwem funkcji członkowskich.

Aby uzyskać więcej informacji, zobacz [OLEUIBUSY](/windows/win32/api/oledlg/ns-oledlg-oleuibusyw) struktury w windows SDK.

## <a name="see-also"></a>Zobacz też

[Klasa COleDialog](../../mfc/reference/coledialog-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleDialog](../../mfc/reference/coledialog-class.md)
