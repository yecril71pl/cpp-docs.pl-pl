---
title: 'Porady: wykonaj wiązania danych DDX DDV za pomocą formularzy systemu Windows | Dokumentacja firmy Microsoft'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], hosting a Windows Forms Control
- Windows Forms [C++], MFC support
ms.assetid: b2957370-cf1f-4779-94ac-228cd393686c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 2f6992aa0c7238d2dc89a8084c7b870dae23067a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-do-ddxddv-data-binding-with-windows-forms"></a>Porady: powiązanie danych DDX/DDV za pomocą interfejsu Windows Forms
[Ddx_managedcontrol —](../mfc/reference/standard-dialog-data-exchange-routines.md#ddx_managedcontrol) wywołania [CWinFormsControl::CreateManagedControl](../mfc/reference/cwinformscontrol-class.md#createmanagedcontrol) można utworzyć formantu, pasujące z identyfikatorem zasobu formantu. Jeśli używasz `DDX_ManagedControl` dla `CWinFormsControl` formantu (w generowanych przez kreatora kodu), nie powinny wywoływać `CreateManagedControl` jawnie dla tej samej kontrolki.  
  
 Wywołanie `DDX_ManagedControl` w [CWnd::DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange) do tworzenia kontrolek z identyfikatorów zasobów. Dla danych programu exchange nie trzeba funkcje DDX/DDV za pomocą formantów formularzy systemu Windows. Zamiast tego możesz umieścić kod, aby uzyskać dostęp do właściwości formantu zarządzanych w `DoDataExchange` metody klasy okna dialogowego (lub Widok), jak w poniższym przykładzie.  
  
 Poniższy przykład pokazuje, jak można powiązać natywnego ciąg C++ do kontrolki użytkownika platformy .NET.  
  
## <a name="example"></a>Przykład  
 Poniżej przedstawiono przykład powiązanie danych DDX/ddv za ciągu MFC `m_str` z użytkownika `NameText` właściwości kontrolki użytkownika platformy .NET.  
  
 Kontrolka jest tworzone, gdy [CDialog::OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) wywołania `CMyDlg::DoDataExchange` po raz pierwszy, dlatego każdy kod odwołujący się `m_UserControl` musi występować po `DDX_ManagedControl` wywołania.  
  
 Można zaimplementować ten kod w aplikacji MFC01 utworzony w [porady: Tworzenie formantu użytkownika i hosta w oknie dialogowym](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md).  
  
 Umieść następujący kod w deklaracji CMFC01Dlg:  
  
```  
class CMFC01Dlg : public CDialog  
{  
   CWinFormsControl<WindowsFormsControlLibrary1::UserControl1> m_MyControl;  
   CString m_str;  
};  
```  
  
## <a name="example"></a>Przykład  
 Umieść następujący kod do implementacji CMFC01Dlg:  
  
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
 Teraz dodamy metodę obsługi kliknij przycisk OK. Kliknij przycisk **widok zasobów** kartę. W widokach, kliknij dwukrotnie `IDD_MFC01_DIALOG`. Zasób okna dialogowego zostanie wyświetlony w edytorze zasobów. Następnie kliknij dwukrotnie przycisk OK.  
  
 Definiowanie procedury obsługi w następujący sposób.  
  
```  
void CMFC01Dlg::OnBnClickedOk()  
{  
   AfxMessageBox(CString(m_MyControl.GetControl()->textBox1->Text));  
   OnOK();  
}  
```  
  
## <a name="example"></a>Przykład  
 I Dodaj następujący wiersz do implementacji CMFC01Dlg::OnInitDialog() wartość logiczna.  
  
```  
m_MyControl.GetControl()->textBox1->Text = "hello";  
```  
  
 Teraz możesz skompilować i uruchomić aplikację. Należy zauważyć, że tekst w polu tekstowym będą wyświetlane w oknie podręcznym komunikatu po zamknięciu aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CWinFormsControl](../mfc/reference/cwinformscontrol-class.md)   
 [Ddx_managedcontrol —](../mfc/reference/standard-dialog-data-exchange-routines.md#ddx_managedcontrol)   
 [CWnd::DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange)