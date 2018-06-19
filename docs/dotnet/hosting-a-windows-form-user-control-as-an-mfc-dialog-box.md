---
title: Hosting systemu Windows formant użytkownika jako okna dialogowego MFC formularza | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], Windows Forms support
- Windows Forms [C++], hosting as MFC Dialog
- hosting Windows Forms control [C++]
ms.assetid: 0434a9d7-8b14-48e6-ad69-9ba9a684677a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: b356bff4974b43445524d9bc07e1e37c62a6f8d4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33138681"
---
# <a name="hosting-a-windows-form-user-control-as-an-mfc-dialog-box"></a>Hostowanie kontrolki użytkownika formularza systemu Windows jako okna dialogowego MFC
MFC zawiera klasy szablonu [CWinFormsDialog](../mfc/reference/cwinformsdialog-class.md) , dzięki czemu mogą być hostowane kontrolki użytkownika formularza systemu Windows (<xref:System.Windows.Forms.UserControl>) w oknie dialogowym MFC modalne i niemodalne. `CWinFormsDialog` pochodzi od klasy MFC [cdialog —](../mfc/reference/cdialog-class.md), więc jako modalne lub niemodalny można uruchomić okna dialogowego.  
  
 Proces który `CWinFormsDialog` używa do hostowania kontrolki użytkownika jest podobny do opisanego w [hostowanie formantu użytkownika formularza systemu Windows w oknie dialogowym MFC](../dotnet/hosting-a-windows-form-user-control-in-an-mfc-dialog-box.md). Jednak `CWinFormsDialog` zarządza inicjowania i hosting kontrolki użytkownika, dzięki czemu nie trzeba programowane ręcznie.  
  
 Dla przykładowej aplikacji, która zawiera formularze systemu Windows używana z MFC, zobacz [MFC i integracja z formularzy systemu Windows](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en).  
  
### <a name="to-create-the-mfc-host-application"></a>Aby utworzyć aplikację hosta MFC  
  
1.  Utwórz projekt aplikacji MFC.  
  
     Na **pliku** menu, wybierz opcję **nowy**, a następnie kliknij przycisk **projektu**. W **Visual C++** folderu, wybierz opcję **aplikacji MFC**.  
  
     W **nazwa** wprowadź `MFC03` i zmień ustawienie rozwiązania na **dodać do rozwiązania**. Kliknij przycisk **OK**.  
  
     W **Kreator aplikacji MFC**Zaakceptuj wszystkie ustawienia domyślne, a następnie kliknij przycisk **Zakończ**. Spowoduje to utworzenie aplikacji MFC z interfejsem wielu dokumentów.  
  
2.  Konfigurowanie projektu.  
  
     W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **MFC03** węzeł projektu i wybierz polecenie **właściwości**. **Strony właściwości** zostanie wyświetlone okno dialogowe.  
  
     W **strony właściwości** okna dialogowego, **właściwości konfiguracji** formantu drzewa, wybierz opcję **ogólne**, a następnie w **projektu domyślne**sekcji, ustaw **Obsługa środowisko uruchomieniowe języka wspólnego** do **obsługuje wspólnego języka środowiska uruchomieniowego (/ clr)**. Kliknij przycisk **OK**.  
  
3.  Dodaj odwołanie do formantu .NET.  
  
     W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **MFC03** węzeł projektu i wybierz polecenie **Dodaj**, **odwołania**. W **strony właściwości**, kliknij przycisk **Dodaj nowe odwołanie**, wybierz WindowsControlLibrary1 (w obszarze **projekty** kartę) i kliknij przycisk **OK**. To spowoduje dodanie odwołania w formie [/FU](../build/reference/fu-name-forced-hash-using-file.md) — opcja kompilatora, aby program zostanie skompilowany; kopiuje również WindowsControlLibrary1.dll do `MFC03` projektu katalogu, dzięki czemu program będzie uruchamiany.  
  
4.  Dodaj `#include <afxwinforms.h>` do stdafx.h na końcu istniejące `#include` instrukcje.  
  
5.  Dodaj nową klasę o tym podklasy `CDialog`.  
  
     Kliknij prawym przyciskiem myszy nazwę projektu i dodawanie klasy MFC (o nazwie CHostForWinForm) tego podklasy `CDialog`. Ponieważ zasobów okno dialogowe nie jest konieczne, można usunąć Identyfikatora zasobu (Wybierz widok zasobów, rozwiń folder okna dialogowego i Usuń IDD_HOSTFORWINFORM zasobów.  Następnie należy usunąć wszystkie odwołania do Identyfikatora w kodzie.).  
  
6.  Zastąp `CDialog` w plikach CHostForWinForm.h i CHostForWinForm.cpp z `CWinFormsDialog<WindowsControlLibrary1::UserControl1>`.  
  
7.  Wywołać DoModal w klasie CHostForWinForm.  
  
     W MFC03.cpp, Dodaj `#include "HostForWinForm.h"`.  
  
     Przed instrukcji return w definicji CMFC03App::InitInstance należy dodać:  
  
     `CHostForWinForm m_HostForWinForm;`  
  
     `m_HostForWinForm.DoModal();`  
  
8.  Tworzenie i uruchamianie projektu.  
  
     Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.  
  
     Na **debugowania** menu, kliknij przycisk **uruchomienie bez debugowania**.  
  
     Następnie dodasz kod umożliwiający monitorowanie stanu formantu w formularzach systemu Windows z aplikacji MFC.  
  
9. Dodaj obsługę OnInitDialog.  
  
     Wyświetl **właściwości** okna (F4). W **widoku klasy**, wybierz CHostForWinForm. W **właściwości** okna, wybierz zastąpienia w wierszu OnInitDialog, kliknij kolumnę po lewej stronie i wybierz \< Dodaj >. Spowoduje to dodanie następujący wiersz do CHostForWinForm.h:  
  
    ```  
    virtual BOOL OnInitDialog();  
    ```  
  
10. Zdefiniuj OnInitDialog (w CHostForWinForm.cpp) w następujący sposób:  
  
    ```  
    BOOL CHostForWinForm::OnInitDialog() {  
       CWinFormsDialog<WindowsControlLibrary1::UserControl1>::OnInitDialog();  
       GetControl()->button1->Click += MAKE_DELEGATE(System::EventHandler, OnButton1);  
       return TRUE;  
    }  
    ```  
  
11. Następnie Dodaj program obsługi OnButton1. Dodaj następujące wiersze do sekcji publicznej klasy CHostForWinForm w CHostForWinForm.h:  
  
    ```  
    virtual void OnButton1( System::Object^ sender, System::EventArgs^ e );  
  
    BEGIN_DELEGATE_MAP( CHostForWinForm )  
       EVENT_DELEGATE_ENTRY( OnButton1, System::Object^, System::EventArgs^ );  
    END_DELEGATE_MAP()  
    ```  
  
     W CHostForWinForm.cpp Dodaj tę definicję:  
  
    ```  
    void CHostForWinForm::OnButton1( System::Object^ sender, System::EventArgs^ e )   
    {  
       System::Windows::Forms::MessageBox::Show("test");  
    }  
    ```  
  
12. Tworzenie i uruchamianie projektu. Po kliknięciu przycisku, który znajduje się w formularzu systemu Windows, zostanie uruchomiony kodu w aplikacji MFC.  
  
     Następnie dodasz kod, aby wyświetlić kod MFC wartość w polu tekstowym w formularzu systemu Windows.  
  
13. W sekcji publicznej klasy CHostForWinForm w CHostForWinForm.h Dodaj następujące oświadczenie:  
  
    ```  
    CString m_sEditBoxOnWinForm;  
    ```  
  
14. W definicji DoDataExchange w CHostForWinForm.cpp należy dodać następujące trzy wiersze na końcu funkcji:  
  
    ```  
    if (pDX->m_bSaveAndValidate)  
       m_sEditBoxOnWinForm = CString( GetControl()->textBox1->Text);  
    else  
       GetControl()->textBox1->Text = gcnew System::String(m_sEditBoxOnWinForm);  
    ```  
  
15. W definicji OnButton1 w CHostForWinForm.cpp należy dodać następujące trzy wiersze na końcu funkcji:  
  
    ```  
    this->UpdateData(TRUE);  
    System::String ^ z = gcnew System::String(m_sEditBoxOnWinForm);  
    System::Windows::Forms::MessageBox::Show(z);  
    ```  
  
16. Tworzenie i uruchamianie projektu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.UserControl?displayProperty=fullName>   
 [Używanie kontrolki użytkownika formularza systemu Windows w MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md)