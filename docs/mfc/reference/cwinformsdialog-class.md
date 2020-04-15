---
title: Klasa CWinFormsDialog
ms.date: 03/27/2019
f1_keywords:
- CWinFormsDialog
- AFXWINFORMS/CWinFormsDialog
- AFXWINFORMS/CWinFormsDialog::CWinFormsDialog
- AFXWINFORMS/CWinFormsDialog::GetControl
- AFXWINFORMS/CWinFormsDialog::GetControlHandle
- AFXWINFORMS/CWinFormsDialog::OnInitDialog
helpviewer_keywords:
- CWinFormsDialog [MFC], CWinFormsDialog
- CWinFormsDialog [MFC], GetControl
- CWinFormsDialog [MFC], GetControlHandle
- CWinFormsDialog [MFC], OnInitDialog
ms.assetid: e3cec000-a578-448e-b06a-8af256312f61
ms.openlocfilehash: 3772033df59e065cedca61012cd479c812cf5b66
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367424"
---
# <a name="cwinformsdialog-class"></a>Klasa CWinFormsDialog

Otoka dla klasy okna dialogowego MFC, która obsługuje kontrolkę użytkownika formularzy systemu Windows.

## <a name="syntax"></a>Składnia

```
template <typename TManagedControl>
class CWinFormsDialog :
    public CDialog
```

#### <a name="parameters"></a>Parametry

*Sterowanie TManagedcontrol*<br/>
Formant użytkownika platformy .NET Framework, który ma być wyświetlany w aplikacji MFC.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CWinFormsDialog::CWinFormsDialog](#cwinformsdialog)|Konstruuje `CWinFormsDialog` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CWinFormsDialog::GetControl](#getcontrol)|Pobiera odwołanie do formantu użytkownika formularzy systemu Windows.|
|[CWinFormsDialog::GetControlHandle](#getcontrolhandle)|Pobiera dojście okna do formantu użytkownika formularzy systemu Windows.|
|[CWinFormsDialog::OnInitDialog](#oninitdialog)|Inicjuje okno dialogowe MFC, tworząc i hostując na nim kontrolkę użytkownika formularzy systemu Windows.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa||
|----------|-|
|[CWinFormsDialog::operator -&gt;](#operator_-_gt)|Zastępuje [CWinFormsDialog::GetControl](#getcontrol) w wyrażeniach.|
|[CWinFormsDialog::operator TManagedControl^](#operator-tmanagedcontrol-hat)|Rzutuje typ jako odwołanie do formantu użytkownika formularzy systemu Windows.|

## <a name="remarks"></a>Uwagi

`CWinFormsDialog`jest otoką dla klasy okna dialogowego MFC [(CDialog),](../../mfc/reference/cdialog-class.md)która obsługuje kontrolkę użytkownika windows forms. Dzięki temu można wyświetlić formanty .NET Framework w modalnym lub niemodalnym oknie dialogowym MFC.

Aby uzyskać więcej informacji na temat korzystania z formularzy systemu Windows, zobacz [Korzystanie z formantu użytkownika formularza systemu Windows w interfejsie MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md) i [hostowanie formantu użytkownika formularza systemu Windows jako okna dialogowego MFC](../../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwinforms.h

## <a name="cwinformsdialogcwinformsdialog"></a><a name="cwinformsdialog"></a>CWinFormsDialog::CWinFormsDialog

Konstruuje `CWinFormsDialog` obiekt.

```
CWinFormsDialog(UINT nIDTemplate = IDD);
```

### <a name="parameters"></a>Parametry

*nIDTemplate*<br/>
Zawiera identyfikator zasobu szablonu okna dialogowego. Użyj edytora dialogów, aby utworzyć szablon okna dialogowego i przechowywać go w pliku skryptu zasobów aplikacji. Aby uzyskać więcej informacji na temat szablonów okien dialogowych, zobacz [CDialog Class](../../mfc/reference/cdialog-class.md).

## <a name="cwinformsdialoggetcontrol"></a><a name="getcontrol"></a>CWinFormsDialog::GetControl

Pobiera odwołanie do formantu użytkownika formularzy systemu Windows.

```
inline TManagedControl^ GetControl() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do formantu Windows Forms w oknie dialogowym MFC.

## <a name="cwinformsdialoggetcontrolhandle"></a><a name="getcontrolhandle"></a>CWinFormsDialog::GetControlHandle

Pobiera dojście okna do formantu użytkownika formularzy systemu Windows.

```
inline HWND GetControlHandle() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca dojście okna do formantu użytkownika formularzy systemu Windows.

## <a name="cwinformsdialogoninitdialog"></a><a name="oninitdialog"></a>CWinFormsDialog::OnInitDialog

Inicjuje okno dialogowe MFC, tworząc i hostując na nim kontrolkę użytkownika formularzy systemu Windows.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Wartość zwracana

Wartość logiczna określająca, czy aplikacja ustawiła fokus wejściowy na jeden z formantów w oknie dialogowym. Jeśli `OnInitDialog` zwraca wartość niezerową, system Windows ustawia fokus wejściowy na pierwszy formant w oknie dialogowym. Ta metoda może zwrócić 0 tylko wtedy, gdy aplikacja jawnie ustawi fokus wejściowy do jednego z formantów w oknie dialogowym.

### <a name="remarks"></a>Uwagi

Po utworzeniu okna dialogowego MFC (przy użyciu metody [Utwórz](../../mfc/reference/cdialog-class.md#create), [CreateIndirect](../../mfc/reference/cdialog-class.md#createindirect)lub [DoModal](../../mfc/reference/cdialog-class.md#domodal) odziedziczonej po [CDialog),](../../mfc/reference/cdialog-class.md)wysyłany jest komunikat WM_INITDIALOG i ta metoda jest wywoływana. Tworzy wystąpienie formantu Windows Forms w oknie dialogowym i dostosowuje rozmiar okna dialogowego, aby pomieścić rozmiar formantu użytkownika. Następnie hostuje nowy formant w oknie dialogowym MFC.

Zastąpość tę funkcję elementu członkowskiego, jeśli konieczne jest wykonanie specjalnego przetwarzania podczas inicjowania okna dialogowego. Aby uzyskać więcej informacji na temat korzystania z tej metody, zobacz [CDialog::OnInitDialog](../../mfc/reference/cdialog-class.md#oninitdialog).

## <a name="cwinformsdialogoperator--gt"></a><a name="operator_-_gt"></a>CWinFormsDialog::operator -&gt;

Zastępuje [CWinFormsDialog::GetControl](#getcontrol) w wyrażeniach.

```
inline TManagedControl^  operator->() const throw();
```

### <a name="remarks"></a>Uwagi

Ten operator zapewnia wygodną składnię, która zastępuje `GetControl` w wyrażeniach.

Aby uzyskać informacje dotyczące korzystania z formularzy systemu Windows, zobacz [Korzystanie z formantu użytkownika formularza systemu Windows w programie MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="cwinformsdialogoperator-tmanagedcontrol"></a><a name="operator-tmanagedcontrol-hat"></a>CWinFormsDialog::operator TManagedControl^

Rzutuje typ jako odwołanie do formantu użytkownika formularzy systemu Windows.

```
inline operator TManagedControl^() const throw();
```

### <a name="remarks"></a>Uwagi

Ten operator rzutuje typ jako odwołanie do formantu Windows Forms. Służy do przekazywania `CWinFormsDialog<TManagedControl>` okna dialogowego do funkcji, które akceptują wskaźnik do obiektu sterującego użytkownika formularzy systemu Windows.

## <a name="see-also"></a>Zobacz też

[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Klasa CWinFormsView](../../mfc/reference/cwinformsview-class.md)<br/>
[Klasa CDialog](../../mfc/reference/cdialog-class.md)
