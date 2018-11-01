---
title: 'Porady: powiązanie danych DDX / DDV za pomocą interfejsu Windows Forms'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], hosting a Windows Forms Control
- Windows Forms [C++], MFC support
ms.assetid: b2957370-cf1f-4779-94ac-228cd393686c
ms.openlocfilehash: 793d6728c7726028c02b885784f122792d84dd2e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456441"
---
# <a name="how-to-do-ddxddv-data-binding-with-windows-forms"></a>Porady: powiązanie danych DDX/DDV za pomocą interfejsu Windows Forms

[Ddx_managedcontrol —](../mfc/reference/standard-dialog-data-exchange-routines.md#ddx_managedcontrol) wywołania [CWinFormsControl::CreateManagedControl](../mfc/reference/cwinformscontrol-class.md#createmanagedcontrol) utworzyć kontrolkę dopasowania identyfikatora zasobu formantu. Jeśli używasz `DDX_ManagedControl` dla `CWinFormsControl` formantu (w generowanych przez kreatora kod), nie powinien wywoływać `CreateManagedControl` jawnie dla tej samej kontrolki.

Wywołaj `DDX_ManagedControl` w [CWnd::DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange) do tworzenia kontrolek z identyfikatorów zasobów. Dla danych programu exchange nie musisz funkcje DDX/DDV za pomocą kontrolek formularzy Windows Forms. Zamiast tego można umieścić kod, aby uzyskać dostęp do właściwości zarządzanego formantu w `DoDataExchange` metody klasy okna dialogowego (lub Widok), jak w poniższym przykładzie.

Poniższy przykład pokazuje, jak powiązać formant użytkownika .NET native ciągu języka C++.

## <a name="example"></a>Przykład

Oto przykład powiązanie danych DDX/DDV ciągu MFC `m_str` za pomocą zdefiniowanych przez użytkownika `NameText` właściwości kontrolki użytkownika platformy .NET.

Formant zostanie utworzony, kiedy [CDialog::OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) wywołania `CMyDlg::DoDataExchange` po raz pierwszy, więc każdy kod odwołujący się `m_UserControl` musi przypadać po `DDX_ManagedControl` wywołania.

Ten kod można zaimplementować w utworzonej w aplikacji MFC01 [porady: tworzenie kontrolki użytkownika i hosta w oknie dialogowym](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md).

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

```
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

Teraz dodamy metody obsługi dla kliknij przycisk OK. Kliknij przycisk **widok zasobów** kartę. W widoku zasobów, kliknij dwukrotnie `IDD_MFC01_DIALOG`. Zasoby dialogowe pojawiają się w edytorze zasobów. Następnie kliknij dwukrotnie przycisk OK...

Zdefiniuj obsługi w następujący sposób.

```
void CMFC01Dlg::OnBnClickedOk()
{
   AfxMessageBox(CString(m_MyControl.GetControl()->textBox1->Text));
   OnOK();
}
```

## <a name="example"></a>Przykład

I Dodaj następujący wiersz do implementacji BOOL CMFC01Dlg::OnInitDialog().

```
m_MyControl.GetControl()->textBox1->Text = "hello";
```

Można teraz tworzyć i uruchomić aplikację. Należy zauważyć, że dowolny tekst w polu tekstowym będą wyświetlane w oknie podręcznym komunikatu po zamknięciu aplikacji.

## <a name="see-also"></a>Zobacz też

[Klasa CWinFormsControl](../mfc/reference/cwinformscontrol-class.md)<br/>
[Ddx_managedcontrol —](../mfc/reference/standard-dialog-data-exchange-routines.md#ddx_managedcontrol)<br/>
[CWnd::DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange)