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
ms.openlocfilehash: 4cbf1137a15a9f86a6377980526e6d188f4d0a69
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504782"
---
# <a name="colechangeicondialog-class"></a>Klasa COleChangeIconDialog

Używane na potrzeby okna dialogowego ikona zmiany OLE.

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
|[COleChangeIconDialog::D oChangeIcon](#dochangeicon)|Wykonuje zmianę określoną w oknie dialogowym.|
|[COleChangeIconDialog::D oModal](#domodal)|Wyświetla okno dialogowe ikona zmiany OLE 2.|
|[COleChangeIconDialog::GetIconicMetafile](#geticonicmetafile)|Pobiera uchwyt do metapliku skojarzonego z formą Icon tego elementu.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[COleChangeIconDialog::m_ci](#m_ci)|Struktura, która kontroluje zachowanie okna dialogowego.|

## <a name="remarks"></a>Uwagi

Utwórz obiekt klasy `COleChangeIconDialog` , gdy chcesz wywołać to okno dialogowe. Po skonstruowaniu obiektu można użyć struktury m_ci, aby zainicjować wartości lub Stany kontrolek w oknie dialogowym. [](#m_ci) `COleChangeIconDialog` `m_ci` Struktura jest typu OLEUICHANGEICON. Aby uzyskać więcej informacji o używaniu tej klasy okna dialogowego, zobacz funkcja członkowska [DoModal](#domodal) .

Aby uzyskać więcej informacji, zapoznaj się ze strukturą [OLEUICHANGEICON](/windows/win32/api/oledlg/ns-oledlg-oleuichangeiconw) w Windows SDK.

Aby uzyskać więcej informacji o oknach dialogowych specyficznych dla OLE, zobacz [okna dialogowe artykułu w OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleChangeIconDialog`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxodlgs. h

##  <a name="colechangeicondialog"></a>COleChangeIconDialog::COleChangeIconDialog

Ta funkcja tworzy tylko `COleChangeIconDialog` obiekt.

```
explicit COleChangeIconDialog(
    COleClientItem* pItem,
    DWORD dwFlags = CIF_SELECTCURRENT,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*pItem*<br/>
Wskazuje element do przekonwertowania.

*flagiDW*<br/>
Flaga tworzenia, która zawiera dowolną liczbę następujących wartości połączonych przy użyciu operatora bitowego lub:

- CIF_SELECTCURRENT określa, że bieżący przycisk radiowy będzie wybierany początkowo po wywołaniu okna dialogowego. Domyślnie włączone.

- CIF_SELECTDEFAULT określa, że domyślny przycisk radiowy zostanie wybrany jako pierwszy po wywołaniu okna dialogowego.

- CIF_SELECTFROMFILE określa, że przycisk radiowy z pliku będzie wybierany początkowo po wywołaniu okna dialogowego.

- CIF_SHOWHELP Określa, że przycisk Pomoc będzie wyświetlany po wywołaniu okna dialogowego.

- CIF_USEICONEXE określa, że ikona powinna zostać wyodrębniona z pliku wykonywalnego określonego `szIconExe` w polu [m_ci](#m_ci) , a nie do pobrania z tego typu. Jest to przydatne w przypadku osadzania lub łączenia z plikami nienależącymi do OLE.

*pParentWnd*<br/>
Wskazuje obiekt nadrzędny lub właściciel (typu `CWnd`), do którego należy obiekt okna dialogowego. Jeśli ma wartość NULL, okno dialogowe nadrzędne okna dialogowego zostanie ustawione na główne okno aplikacji.

### <a name="remarks"></a>Uwagi

Aby wyświetlić okno dialogowe, wywołaj funkcję [DoModal](#domodal) .

Aby uzyskać więcej informacji, zapoznaj się ze strukturą [OLEUICHANGEICON](/windows/win32/api/oledlg/ns-oledlg-oleuichangeiconw) w Windows SDK.

##  <a name="dochangeicon"></a>COleChangeIconDialog::D oChangeIcon

Wywołaj tę funkcję, aby zmienić ikonę reprezentującą element do zaznaczonego w oknie dialogowym po [DoModal](#domodal) zwraca IDOK.

```
BOOL DoChangeIcon(COleClientItem* pItem);
```

### <a name="parameters"></a>Parametry

*pItem*<br/>
Wskazuje element, którego ikona zmienia się.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli zmiana zakończyła się pomyślnie; w przeciwnym razie 0.

##  <a name="domodal"></a>COleChangeIconDialog::D oModal

Wywołaj tę funkcję, aby wyświetlić okno dialogowe ikony zmiany OLE.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Wartość zwracana

Stan ukończenia dla okna dialogowego. Jedna z następujących wartości:

- IDOK, jeśli okno dialogowe zostało wyświetlone pomyślnie.

- IDCANCEL, jeśli użytkownik anulował okno dialogowe.

- IDABORT, jeśli wystąpił błąd. Jeśli IDABORT jest zwracany, wywołaj `COleDialog::GetLastError` funkcję członkowską, aby uzyskać więcej informacji na temat typu błędu, który wystąpił. Listę możliwych błędów można znaleźć w funkcji [OLEUICHANGEICON](/windows/win32/api/oledlg/nf-oledlg-oleuichangeiconw) w Windows SDK.

### <a name="remarks"></a>Uwagi

Jeśli chcesz zainicjować różne kontrolki okna dialogowego, ustawiając elementy członkowskie struktury [m_ci](#m_ci) , należy to zrobić przed wywołaniem `DoModal`, ale po skonstruowaniu obiektu okna dialogowego.

Jeśli `DoModal` zwraca IDOK, można wywołać inne funkcje członkowskie, aby pobrać ustawienia lub informacje, które zostały wprowadzone przez użytkownika w oknie dialogowym.

##  <a name="geticonicmetafile"></a>COleChangeIconDialog::GetIconicMetafile

Wywołaj tę funkcję, aby uzyskać uchwyt do metapliku zawierającego ikonę wybranego elementu.

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>Wartość zwracana

Uchwyt do metapliku zawierającego ikonę ikony nowej ikony, jeśli okno dialogowe zostało odrzucone przez kliknięcie przycisku **OK**; w przeciwnym razie ikona jest wyświetlana przed wyświetleniem okna dialogowego.

##  <a name="m_ci"></a>COleChangeIconDialog::m_ci

Struktura typu OLEUICHANGEICON używana do sterowania zachowaniem okna dialogowego Zmień ikonę.

```
OLEUICHANGEICON m_ci;
```

### <a name="remarks"></a>Uwagi

Elementy członkowskie tej struktury można modyfikować bezpośrednio lub za pomocą funkcji składowych.

Aby uzyskać więcej informacji, zapoznaj się ze strukturą [OLEUICHANGEICON](/windows/win32/api/oledlg/ns-oledlg-oleuichangeiconw) w Windows SDK.

## <a name="see-also"></a>Zobacz także

[Klasa COleDialog](../../mfc/reference/coledialog-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleDialog](../../mfc/reference/coledialog-class.md)
