---
title: 'Instrukcje: powiązanie danych DDX/DDV za pomocą interfejsu Windows Forms'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], hosting a Windows Forms Control
- Windows Forms [C++], MFC support
ms.assetid: b2957370-cf1f-4779-94ac-228cd393686c
ms.openlocfilehash: 31629a4db2559112ba49f5c069b08de7abdfc2db
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754352"
---
# <a name="how-to-do-ddxddv-data-binding-with-windows-forms"></a>Porady: powiązanie danych DDX/DDV za pomocą interfejsu Windows Forms

[DDX_ManagedControl](../mfc/reference/standard-dialog-data-exchange-routines.md#ddx_managedcontrol) wywołuje [CWinFormsControl::CreateManagedControl,](../mfc/reference/cwinformscontrol-class.md#createmanagedcontrol) aby utworzyć formant pasujący do identyfikatora kontroli zasobów. Jeśli używasz `DDX_ManagedControl` `CWinFormsControl` formantu (w kodzie wygenerowanym `CreateManagedControl` przez kreatora), nie należy wywoływać jawnie dla tego samego formantu.

Wywołanie `DDX_ManagedControl` w [CWnd::DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange) do tworzenia formantów z identyfikatorów zasobów. Do wymiany danych nie trzeba używać funkcji DDX/DDV z formantami Windows Forms. Zamiast tego można umieścić kod, aby uzyskać dostęp do `DoDataExchange` właściwości formantu zarządzanego w metodzie klasy okna dialogowego (lub widoku), jak w poniższym przykładzie.

W poniższym przykładzie pokazano, jak powiązać natywnego ciągu C++ z formantem użytkownika platformy .NET.

## <a name="example"></a>Przykład

Poniżej przedstawiono przykład powiązania danych DDX/DDV `m_str` ciągu MFC `NameText` z właściwością zdefiniowaną przez użytkownika formantu użytkownika .NET.

Formant jest tworzony, gdy [CDialog::OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) wywołuje `CMyDlg::DoDataExchange` po raz `m_UserControl` pierwszy, więc `DDX_ManagedControl` każdy kod, który odwołuje się musi pochodzić po wywołaniu.

Ten kod można zaimplementować w aplikacji MFC01 utworzonej w [aplikacji Jak: Tworzenie formantu użytkownika i hosta w oknie dialogowym](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md).

Umieść następujący kod w deklaracji CMFC01Dlg:

```
class CMFC01Dlg : public CDialog
{
   CWinFormsControl<WindowsFormsControlLibrary1::UserControl1> m_MyControl;
   CString m_str;
};
```

## <a name="example"></a>Przykład

Umieść następujący kod w implementacji CMFC01Dlg:

```cpp
void CMFC01Dlg::DoDataExchange(CDataExchange* pDX)
{
   CDialog::DoDataExchange(pDX);
   DDX_ManagedControl(pDX, IDC_CTRL1, m_MyControl);

   if (pDX->m_bSaveAndValidate) {
      m_str = m_MyControl->textBox1->Text;
   } else
   {
      m_MyControl->textBox1->Text = gcnew System::String(m_str);
   }
}
```

## <a name="example"></a>Przykład

Teraz dodamy metodę obsługi za kliknięcie przycisku OK. Kliknij kartę **Widok zasobów.** W widoku zasobów kliknij `IDD_MFC01_DIALOG`dwukrotnie przycisk . Zasób okna dialogowego pojawi się w Edytorze zasobów. Następnie kliknij dwukrotnie przycisk OK..

Zdefiniuj program obsługi w następujący sposób.

```cpp
void CMFC01Dlg::OnBnClickedOk()
{
   AfxMessageBox(CString(m_MyControl.GetControl()->textBox1->Text));
   OnOK();
}
```

## <a name="example"></a>Przykład

I dodać następujący wiersz do implementacji BOOL CMFC01Dlg::OnInitDialog().

```
m_MyControl.GetControl()->textBox1->Text = "hello";
```

Teraz możesz skompilować i uruchomić aplikację. Należy zauważyć, że każdy tekst w polu tekstowym będą wyświetlane w wyskakującym oknie komunikatów po zamknięciu aplikacji.

## <a name="see-also"></a>Zobacz też

[Klasa CWinFormsControl](../mfc/reference/cwinformscontrol-class.md)<br/>
[DDX_ManagedControl](../mfc/reference/standard-dialog-data-exchange-routines.md#ddx_managedcontrol)<br/>
[CWnd::DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange)
