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
ms.openlocfilehash: a25823982b9276309e99a2a26cef8d6fe2e764bd
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040668"
---
# <a name="cwinformsdialog-class"></a>Klasa CWinFormsDialog

Otoka dla klasy okna dialogowego MFC, która obsługuje kontrolkę użytkownika Windows Forms.

## <a name="syntax"></a>Składnia

```
template <typename TManagedControl>
class CWinFormsDialog :
    public CDialog
```

#### <a name="parameters"></a>Parametry

*TManagedControl*<br/>
Kontrolka użytkownika .NET Framework, która ma być wyświetlana w aplikacji MFC.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CWinFormsDialog::CWinFormsDialog](#cwinformsdialog)|Konstruuje `CWinFormsDialog` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CWinFormsDialog:: GetControl](#getcontrol)|Pobiera odwołanie do kontrolki użytkownika Windows Forms.|
|[CWinFormsDialog::GetControlHandle](#getcontrolhandle)|Pobiera uchwyt okna do kontrolki użytkownika Windows Forms.|
|[CWinFormsDialog:: OnInitDialog](#oninitdialog)|Inicjuje okno dialogowe MFC, tworząc i udostępniając Windows Formsą kontrolkę użytkownika.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-|
|[CWinFormsDialog:: operator-&gt;](#operator_-_gt)|Zamienia [CWinFormsDialog:: GetControl](#getcontrol) w wyrażeniach.|
|[CWinFormsDialog:: operator TManagedControl ^](#operator-tmanagedcontrol-hat)|Rzutuje typ jako odwołanie do kontrolki użytkownika Windows Forms.|

## <a name="remarks"></a>Uwagi

`CWinFormsDialog` jest otoką dla klasy okna dialogowego MFC ( [CDialog](../../mfc/reference/cdialog-class.md)), która obsługuje kontrolkę użytkownika Windows Forms. Umożliwia to wyświetlanie kontrolek .NET Framework w modalnym lub niemodalnym oknie dialogowym MFC.

Aby uzyskać więcej informacji na temat korzystania z Windows Forms, zobacz [Korzystanie z kontrolki użytkownika formularza systemu Windows w MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md) i [hostowanie kontrolki użytkownika formularza systemu Windows jako okna dialogowego MFC](../../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwinforms. h

## <a name="cwinformsdialogcwinformsdialog"></a><a name="cwinformsdialog"></a> CWinFormsDialog::CWinFormsDialog

Konstruuje `CWinFormsDialog` obiekt.

```
CWinFormsDialog(UINT nIDTemplate = IDD);
```

### <a name="parameters"></a>Parametry

*nIDTemplate*<br/>
Zawiera identyfikator zasobu szablonu okna dialogowego. Użyj edytora okien dialogowych, aby utworzyć szablon okna dialogowego i zapisać go w pliku skryptu zasobu aplikacji. Aby uzyskać więcej informacji na temat szablonów okna dialogowego, zobacz [Klasa CDialog](../../mfc/reference/cdialog-class.md).

## <a name="cwinformsdialoggetcontrol"></a><a name="getcontrol"></a> CWinFormsDialog:: GetControl

Pobiera odwołanie do kontrolki użytkownika Windows Forms.

```
inline TManagedControl^ GetControl() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do kontrolki Windows Forms w oknie dialogowym MFC.

## <a name="cwinformsdialoggetcontrolhandle"></a><a name="getcontrolhandle"></a> CWinFormsDialog::GetControlHandle

Pobiera uchwyt okna do kontrolki użytkownika Windows Forms.

```
inline HWND GetControlHandle() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca uchwyt okna do kontrolki użytkownika Windows Forms.

## <a name="cwinformsdialogoninitdialog"></a><a name="oninitdialog"></a> CWinFormsDialog:: OnInitDialog

Inicjuje okno dialogowe MFC, tworząc i udostępniając Windows Formsą kontrolkę użytkownika.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Wartość zwracana

Wartość logiczna określająca, czy aplikacja ustawi fokus wprowadzania na jeden z kontrolek w oknie dialogowym. Jeśli `OnInitDialog` zwraca wartość różną od zera, system Windows ustawia fokus wprowadzania na pierwszy formant w oknie dialogowym. Ta metoda może zwrócić 0 tylko wtedy, gdy aplikacja jawnie ustawi fokus wprowadzania na jeden z kontrolek w oknie dialogowym.

### <a name="remarks"></a>Uwagi

Po utworzeniu okna dialogowego MFC (za pomocą metody [Create](../../mfc/reference/cdialog-class.md#create) [,](../../mfc/reference/cdialog-class.md#createindirect) [DoModal](../../mfc/reference/cdialog-class.md#domodal) lub [CDialog](../../mfc/reference/cdialog-class.md)), wysyłany jest komunikat WM_INITDIALOG i wywoływana jest ta metoda. Tworzy wystąpienie kontrolki Windows Forms w oknie dialogowym i dostosowuje rozmiar okna dialogowego, aby pomieścić rozmiar kontrolki użytkownika. Następnie jest hostem nowej kontrolki w oknie dialogowym MFC.

Przesłoń tę funkcję elementu członkowskiego, jeśli trzeba przeprowadzić przetwarzanie specjalne po zainicjowaniu okna dialogowego. Aby uzyskać więcej informacji na temat korzystania z tej metody, zobacz [CDialog:: OnInitDialog](../../mfc/reference/cdialog-class.md#oninitdialog).

## <a name="cwinformsdialogoperator--gt"></a><a name="operator_-_gt"></a> CWinFormsDialog:: operator-&gt;

Zamienia [CWinFormsDialog:: GetControl](#getcontrol) w wyrażeniach.

```
inline TManagedControl^  operator->() const throw();
```

### <a name="remarks"></a>Uwagi

Ten operator udostępnia wygodną składnię zastępującą `GetControl` wyrażenia.

Aby uzyskać informacje na temat korzystania z Windows Forms, zobacz [Korzystanie z kontrolki użytkownika formularza systemu Windows w MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="cwinformsdialogoperator-tmanagedcontrol"></a><a name="operator-tmanagedcontrol-hat"></a> CWinFormsDialog:: operator TManagedControl ^

Rzutuje typ jako odwołanie do kontrolki użytkownika Windows Forms.

```
inline operator TManagedControl^() const throw();
```

### <a name="remarks"></a>Uwagi

Ten operator rzutuje typ jako odwołanie do kontrolki Windows Forms. Służy do przekazywania okna `CWinFormsDialog<TManagedControl>` dialogowego do funkcji, które akceptują wskaźnik do Windows Forms obiektu kontroli użytkownika.

## <a name="see-also"></a>Zobacz także

[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Klasa CWinFormsView](../../mfc/reference/cwinformsview-class.md)<br/>
[Klasa CDialog](../../mfc/reference/cdialog-class.md)
