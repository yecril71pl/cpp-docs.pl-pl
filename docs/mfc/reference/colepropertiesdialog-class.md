---
title: Klasa COlePropertiesDialog
ms.date: 11/04/2016
f1_keywords:
- COlePropertiesDialog
- AFXODLGS/COlePropertiesDialog
- AFXODLGS/COlePropertiesDialog::COlePropertiesDialog
- AFXODLGS/COlePropertiesDialog::DoModal
- AFXODLGS/COlePropertiesDialog::OnApplyScale
- AFXODLGS/COlePropertiesDialog::m_gp
- AFXODLGS/COlePropertiesDialog::m_lp
- AFXODLGS/COlePropertiesDialog::m_op
- AFXODLGS/COlePropertiesDialog::m_psh
- AFXODLGS/COlePropertiesDialog::m_vp
helpviewer_keywords:
- COlePropertiesDialog [MFC], COlePropertiesDialog
- COlePropertiesDialog [MFC], DoModal
- COlePropertiesDialog [MFC], OnApplyScale
- COlePropertiesDialog [MFC], m_gp
- COlePropertiesDialog [MFC], m_lp
- COlePropertiesDialog [MFC], m_op
- COlePropertiesDialog [MFC], m_psh
- COlePropertiesDialog [MFC], m_vp
ms.assetid: a54dbc89-1447-4329-bd01-00e98ec9e935
ms.openlocfilehash: f065894ff49af755ab4020f71b0213b19db49054
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374893"
---
# <a name="colepropertiesdialog-class"></a>Klasa COlePropertiesDialog

Hermetyzuje okno dialogowe Typowe właściwości obiektu OLE systemu Windows.

## <a name="syntax"></a>Składnia

```
class COlePropertiesDialog : public COleDialog
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COlePropertiesDialog::COlePropertiesDialog](#colepropertiesdialog)|Konstruuje `COlePropertiesDialog` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COlePropertiesDialog::DoModal](#domodal)|Wyświetla okno dialogowe i umożliwia użytkownikowi dokonanie wyboru.|
|[COlePropertiesDialog::OnApplyScale](#onapplyscale)|Wywoływane przez strukturę, gdy skalowanie elementu dokumentu uległo zmianie.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[COlePropertiesDialog::m_gp](#m_gp)|Struktura używana do inicjowania strony `COlePropertiesDialog` "Ogólne" obiektu.|
|[COlePropertiesDialog::m_lp](#m_lp)|Struktura używana do inicjowania strony `COlePropertiesDialog` "Łącze" obiektu.|
|[COlePropertiesDialog::m_op](#m_op)|Struktura używana do inicjowania `COlePropertiesDialog` obiektu.|
|[COlePropertiesDialog::m_psh](#m_psh)|Struktura używana do dodawania dodatkowych stron właściwości niestandardowych.|
|[COlePropertiesDialog::m_vp](#m_vp)|Struktura używana do dostosowywania strony "Widok" `COlePropertiesDialog` obiektu.|

## <a name="remarks"></a>Uwagi

Okna dialogowe Typowe właściwości obiektu OLE umożliwiają łatwe wyświetlanie i modyfikowanie właściwości elementu dokumentu OLE w sposób zgodny ze standardami systemu Windows. Właściwości te obejmują między innymi informacje o pliku reprezentowanym przez element dokumentu, opcje wyświetlania ikony i skalowania obrazu oraz informacje o łączu elementu (jeśli element jest połączony).

Aby użyć `COlePropertiesDialog` obiektu, należy najpierw `COlePropertiesDialog` utworzyć obiekt przy użyciu konstruktora. Po skonstruowaniu okna dialogowego należy `DoModal` wywołać funkcję elementu członkowskiego, aby wyświetlić okno dialogowe i zezwolić użytkownikowi na modyfikowanie dowolnych właściwości elementu. `DoModal`zwraca, czy użytkownik wybrał przycisk OK (IDOK) czy Anuluj (IDCANCEL). Oprócz przycisków OK i Anuluj istnieje przycisk Zastosuj. Gdy użytkownik wybierze Zastosuj, wszelkie zmiany wprowadzone do właściwości elementu dokumentu są stosowane do elementu, a jego obraz jest automatycznie aktualizowany, ale pozostaje aktywny.

Element [członkowski m_psh](#m_psh) danych jest wskaźnikiem `PROPSHEETHEADER` do struktury i w większości przypadków nie trzeba będzie uzyskać do niego jawnie dostępu. Wyjątkiem jest sytuacja, gdy potrzebne są dodatkowe strony właściwości poza domyślnymi stronami Ogólne, Widok i Łącze. W takim przypadku można `m_psh` zmodyfikować element członkowski danych, `DoModal` aby uwzględnić strony niestandardowe przed wywołaniem funkcji elementu członkowskiego.

Aby uzyskać więcej informacji na temat okien dialogowych OLE, zobacz [artykuł Okna dialogowe w ole](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cdialog](../../mfc/reference/cdialog-class.md)

[CKlogialny](../../mfc/reference/ccommondialog-class.md)

[COleDialog (Polski)](../../mfc/reference/coledialog-class.md)

`COlePropertiesDialog`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxodlgs.h

## <a name="colepropertiesdialogcolepropertiesdialog"></a><a name="colepropertiesdialog"></a>COlePropertiesDialog::COlePropertiesDialog

Tworzy obiekt `COlePropertiesDialog`.

```
COlePropertiesDialog(
    COleClientItem* pItem,
    UINT nScaleMin = 10,
    UINT nScaleMax = 500,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*pItem (własówce)*<br/>
Wskaźnik do elementu dokumentu, którego właściwości są dostępne.

*nScaleMin*<br/>
Minimalna wartość procentowa skalowania obrazu elementu dokumentu.

*nScaleMax (Polski)*<br/>
Maksymalny procent skalowania obrazu elementu dokumentu.

*pParentWnd*<br/>
Wskaźnik do obiektu nadrzędnego lub właściciela okna dialogowego.

### <a name="remarks"></a>Uwagi

Wywodź z klasy okna `COlePropertiesDialog` dialogowego typowe właściwości obiektu OLE, aby zaimplementować skalowanie elementów dokumentu. Wszystkie okna dialogowe zaimplementowane przez wystąpienie tej klasy nie będą obsługiwać skalowania elementu dokumentu.

Domyślnie typowe okno dialogowe Właściwości obiektu OLE ma trzy strony domyślne:

- Ogólne

   Ta strona zawiera informacje o systemie dla pliku reprezentowanego przez wybrany element dokumentu. Na tej stronie użytkownik może przekonwertować wybrany element na inny typ.

- Widok

   Ta strona zawiera opcje wyświetlania elementu, zmiany ikony i zmiany skalowania obrazu.

- Link

   Ta strona zawiera opcje zmiany lokalizacji połączonego elementu i aktualizacji połączonego elementu. Na tej stronie użytkownik może podzielić łącze wybranego elementu.

Aby dodać strony poza tymi dostarczonymi domyślnie, zmodyfikuj zmienną [m_psh](#m_psh) elementu członkowskiego przed zamknięciem konstruktora `COlePropertiesDialog`klasy pochodnej. Jest to zaawansowana implementacja konstruktora. `COlePropertiesDialog`

## <a name="colepropertiesdialogdomodal"></a><a name="domodal"></a>COlePropertiesDialog::DoModal

Wywołanie tej funkcji elementu członkowskiego, aby wyświetlić okno dialogowe Typowe właściwości obiektu OLE systemu Windows i umożliwić użytkownikowi wyświetlanie i/lub zmienianie różnych właściwości elementu dokumentu.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Wartość zwracana

IDOK lub IDCANCEL jeśli się powiedzie; w przeciwnym razie 0. IDOK i IDCANCEL to stałe wskazujące, czy użytkownik wybrał przycisk OK, czy Anuluj.

Jeśli funkcja IDCANCEL jest zwracana, można wywołać funkcję [Windows CommDlgExtendedError,](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) aby ustalić, czy wystąpił błąd.

## <a name="colepropertiesdialogm_gp"></a><a name="m_gp"></a>COlePropertiesDialog::m_gp

Struktura typu [OLEUIGNRLPROPS](/windows/win32/api/oledlg/ns-oledlg-oleuignrlpropsw), używana do inicjowania strony ogólne okna dialogowego Właściwości obiektu OLE.

```
OLEUIGNRLPROPS m_gp;
```

### <a name="remarks"></a>Uwagi

Ta strona pokazuje typ i rozmiar osadzania i umożliwia użytkownikowi dostęp do okna dialogowego Konwertowanie. Ta strona pokazuje również miejsce docelowe łącza, jeśli obiekt jest łączem.

Aby uzyskać więcej `OLEUIGNRLPROPS` informacji na temat struktury, zobacz Windows SDK.

## <a name="colepropertiesdialogm_lp"></a><a name="m_lp"></a>COlePropertiesDialog::m_lp

Struktura typu [OLEUILINKPROPS](/windows/win32/api/oledlg/ns-oledlg-oleuilinkpropsw), używana do inicjowania strony łącze okna dialogowego Właściwości obiektu OLE.

```
OLEUILINKPROPS m_lp;
```

### <a name="remarks"></a>Uwagi

Ta strona pokazuje lokalizację połączonego elementu i umożliwia użytkownikowi zaktualizowanie lub przerwanie łącza do elementu.

Aby uzyskać więcej `OLEUILINKPROPS` informacji na temat struktury, zobacz Windows SDK.

## <a name="colepropertiesdialogm_op"></a><a name="m_op"></a>COlePropertiesDialog::m_op

Struktura typu [OLEUIOBJECTPROPS](/windows/win32/api/oledlg/ns-oledlg-oleuiobjectpropsw), używana do inicjowania wspólnego okna dialogowego Właściwości obiektu OLE.

```
OLEUIOBJECTPROPS m_op;
```

### <a name="remarks"></a>Uwagi

Ta struktura zawiera elementy członkowskie używane do inicjowania stron Ogólne, Łącze i Widok.

Aby uzyskać więcej informacji, zobacz OLEUIOBJECTPROPS i [OLEUILINKPROPS](/windows/win32/api/oledlg/ns-oledlg-oleuilinkpropsw) struktur w windows SDK.

## <a name="colepropertiesdialogm_psh"></a><a name="m_psh"></a>COlePropertiesDialog::m_psh

Struktura typu [PROPSHEETHEADER](/windows/win32/api/prsht/ns-prsht-propsheetheadera_v2), którego członkowie przechowują właściwości obiektu okna dialogowego.

```
PROPSHEETHEADER m_psh;
```

### <a name="remarks"></a>Uwagi

Po skonstruowaniu `COlePropertiesDialog` obiektu, można `m_psh` użyć, aby ustawić różne aspekty `DoModal` okna dialogowego przed wywołaniem funkcji elementu członkowskiego.

Jeśli zmodyfikujesz `m_psh` element członkowski danych bezpośrednio, należy zastąpić wszelkie domyślne zachowanie.

Aby uzyskać więcej `PROPSHEETHEADER` informacji na temat struktury, zobacz Windows SDK.

## <a name="colepropertiesdialogm_vp"></a><a name="m_vp"></a>COlePropertiesDialog::m_vp

Struktura typu [OLEUIVIEWPROPS](/windows/win32/api/oledlg/ns-oledlg-oleuiviewpropsw), używana do inicjowania strony Widok okna dialogowego Właściwości obiektu OLE.

```
OLEUIVIEWPROPS m_vp;
```

### <a name="remarks"></a>Uwagi

Ta strona umożliwia użytkownikowi przełączanie między "zawartość" i "ikoniczny" widoki obiektu i zmienić jego skalowanie w kontenerze. Umożliwia również użytkownikowi dostęp do okna dialogowego Zmień ikonę, gdy obiekt jest wyświetlany jako ikona.

Aby uzyskać więcej `OLEUIVIEWPROPS` informacji na temat struktury, zobacz Windows SDK.

## <a name="colepropertiesdialogonapplyscale"></a><a name="onapplyscale"></a>COlePropertiesDialog::OnApplyScale

Wywoływana przez platformę, gdy wartość skalowania została zmieniona i wybrano opcję OK lub Zastosuj.

```
virtual BOOL OnApplyScale(
    COleClientItem* pItem,
    int nCurrentScale,
    BOOL bRelativeToOrig);
```

### <a name="parameters"></a>Parametry

*pItem (własówce)*<br/>
Wskaźnik do elementu dokumentu, którego właściwości są dostępne.

*nObserwalość prądu*<br/>
Wartość liczbowa skali okna dialogowego.

*bRelativeToOrig (Doo- 100)*<br/>
Wskazuje, czy skalowanie ma zastosowanie do oryginalnego rozmiaru elementu dokumentu.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli obsługiwane; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Domyślna implementacja nic nie robi. Należy zastąpić tę funkcję, aby włączyć kontrolki skalowania.

> [!NOTE]
> Przed wyświetleniem wspólnego okna dialogowego Właściwości obiektu OLE, struktura wywołuje tę funkcję z wartością NULL dla *pItem* i a - 1 dla *nCurrentScale*. Odbywa się to w celu określenia, czy formanty skalowania powinny być włączone.

## <a name="see-also"></a>Zobacz też

[Przykładowy CIRC MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa COleDialog](../../mfc/reference/coledialog-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleDialog](../../mfc/reference/coledialog-class.md)<br/>
[Klasa CPropertyPage](../../mfc/reference/cpropertypage-class.md)
