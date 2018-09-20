---
title: Klasa CWinFormsDialog | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CWinFormsDialog
- AFXWINFORMS/CWinFormsDialog
- AFXWINFORMS/CWinFormsDialog::CWinFormsDialog
- AFXWINFORMS/CWinFormsDialog::GetControl
- AFXWINFORMS/CWinFormsDialog::GetControlHandle
- AFXWINFORMS/CWinFormsDialog::OnInitDialog
dev_langs:
- C++
helpviewer_keywords:
- CWinFormsDialog [MFC], CWinFormsDialog
- CWinFormsDialog [MFC], GetControl
- CWinFormsDialog [MFC], GetControlHandle
- CWinFormsDialog [MFC], OnInitDialog
ms.assetid: e3cec000-a578-448e-b06a-8af256312f61
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3865fe1e1bf3c8dff9861dba2ef12ce1a34fe22a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46428873"
---
# <a name="cwinformsdialog-class"></a>Klasa CWinFormsDialog

Otoka klasy okna dialogowgo MFC, który obsługuje formant użytkownika interfejsu Windows Forms.

## <a name="syntax"></a>Składnia

```
template <typename TManagedControl>
class CWinFormsDialog :
    public CDialog
```

#### <a name="parameters"></a>Parametry

*TManagedControl*<br/>
Formant użytkownika .NET Framework, która mają być wyświetlane w aplikacji MFC.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CWinFormsDialog::CWinFormsDialog](#cwinformsdialog)|Konstruuje `CWinFormsDialog` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CWinFormsDialog::GetControl](#getcontrol)|Pobiera odwołanie do kontrolki użytkownika Windows Forms.|
|[CWinFormsDialog::GetControlHandle](#getcontrolhandle)|Pobiera uchwyt okna do kontrolki użytkownika Windows Forms.|
|[CWinFormsDialog::OnInitDialog](#oninitdialog)|Inicjuje okna dialogowego MFC, tworzenie i hostowanie kontrolki użytkownika interfejsu Windows Forms na nim.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa||
|----------|-|
|[CWinFormsDialog::operator-&gt;](#operator_-_gt)|Zastępuje [CWinFormsDialog::GetControl](#getcontrol) w wyrażeniach.|
|[CWinFormsDialog::operator TManagedControl ^](#operator_tmanagedcontrol)|Rzutuje typu jako odwołanie do formant użytkownika interfejsu Windows Forms.|

## <a name="remarks"></a>Uwagi

`CWinFormsDialog` jest otoką klasy okna dialogowgo MFC ( [CDialog](../../mfc/reference/cdialog-class.md)), która hostuje formant użytkownika interfejsu Windows Forms. Umożliwia to wyświetlanie formantów .NET Framework na modalne lub niemodalne okno dialogowe MFC.

Aby uzyskać więcej informacji na temat korzystania z Windows Forms, zobacz [za pomocą kontrolki użytkownika formularza Windows w MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md) i [hostowanie kontrolki użytkownika formularza Windows jako okna dialogowego MFC](../../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwinforms.h

##  <a name="cwinformsdialog"></a>  CWinFormsDialog::CWinFormsDialog

Konstruuje `CWinFormsDialog` obiektu.

```
CWinFormsDialog(UINT nIDTemplate = IDD);
```

### <a name="parameters"></a>Parametry

*nIDTemplate*<br/>
Zawiera identyfikator zasobu szablon okno dialogowe. Edytor okien dialogowych umożliwia tworzenie szablonu okna dialogowego i zapisz go w pliku skryptu zasobów aplikacji. Aby uzyskać więcej informacji na temat szablonów okna dialogowego, zobacz [klasa CDialog](../../mfc/reference/cdialog-class.md).

##  <a name="getcontrol"></a>  CWinFormsDialog::GetControl

Pobiera odwołanie do kontrolki użytkownika Windows Forms.

```
inline TManagedControl^ GetControl() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do formantu Windows Forms w oknie dialogowym MFC.

##  <a name="getcontrolhandle"></a>  CWinFormsDialog::GetControlHandle

Pobiera uchwyt okna do kontrolki użytkownika Windows Forms.

```
inline HWND GetControlHandle() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca uchwyt okna do kontrolki użytkownika Windows Forms.

##  <a name="oninitdialog"></a>  CWinFormsDialog::OnInitDialog

Inicjuje okna dialogowego MFC, tworzenie i hostowanie kontrolki użytkownika interfejsu Windows Forms na nim.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Wartość zwracana

Wartość logiczna określająca, czy aplikacja została ustawiona fokusu wprowadzania do formantów w oknie dialogowym. Jeśli `OnInitDialog` zwraca wartość różną od zera, Windows ustawia fokus wprowadzania do pierwszego formantu w oknie dialogowym. Ta metoda może zwrócić 0, tylko wtedy, gdy aplikacja ma jawnie ustawić fokusu wprowadzania do formantów w oknie dialogowym.

### <a name="remarks"></a>Uwagi

Po utworzeniu okna dialogowego MFC (przy użyciu [Utwórz](../../mfc/reference/cdialog-class.md#create), [CreateIndirect](../../mfc/reference/cdialog-class.md#createindirect), lub [DoModal](../../mfc/reference/cdialog-class.md#domodal) metody dziedziczone z [CDialog](../../mfc/reference/cdialog-class.md)), WM_ INITDIALOG wiadomość jest wysyłana, a ta metoda jest wywoływana. Tworzy wystąpienie formantu Windows Forms w oknie dialogowym i dopasowuje rozmiar okna dialogowego, aby pomieścić rozmiar kontrolki użytkownika. Następnie pracującymi na nim nowego formantu w oknie dialogowym MFC.

Ta funkcja elementu członkowskiego należy zastąpić, jeśli trzeba wykonać specjalnego przetwarzania, gdy okno dialogowe jest zainicjowany. Aby uzyskać więcej informacji na temat korzystania z tej metody, zobacz [CDialog::OnInitDialog](../../mfc/reference/cdialog-class.md#oninitdialog).

##  <a name="operator_-_gt"></a>  CWinFormsDialog::operator-&gt;

Zastępuje [CWinFormsDialog::GetControl](#getcontrol) w wyrażeniach.

```
inline TManagedControl^  operator->() const throw();
```

### <a name="remarks"></a>Uwagi

Ten operator miejsce wygodnej składni, która zastępuje `GetControl` w wyrażeniach.

Aby uzyskać informacje na temat korzystania z formularzy Windows, zobacz [za pomocą kontrolki użytkownika formularza Windows w MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

##  <a name="operator_tmanagedcontrol_xor"></a>  CWinFormsDialog::operator TManagedControl ^

Rzutuje typu jako odwołanie do formant użytkownika interfejsu Windows Forms.

```
inline operator TManagedControl^() const throw();
```

### <a name="remarks"></a>Uwagi

Ten operator rzutuje typu jako odwołanie do formantu Windows Forms. Służy do przekazywania `CWinFormsDialog<TManagedControl>` okno dialogowe do funkcji, które akceptują wskaźnik do obiektu formant użytkownika Windows Forms.

## <a name="see-also"></a>Zobacz też

[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Klasa CWinFormsView](../../mfc/reference/cwinformsview-class.md)<br/>
[Klasa CDialog](../../mfc/reference/cdialog-class.md)
