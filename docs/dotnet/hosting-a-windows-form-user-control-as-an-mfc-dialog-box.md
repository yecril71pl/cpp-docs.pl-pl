---
title: Hosting Windows kontrolka formularz, która użytkownika jako okna dialogowego MFC | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 47914a73880f5cea13f1bc64c231604a0d5d05dd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46073817"
---
# <a name="hosting-a-windows-form-user-control-as-an-mfc-dialog-box"></a>Hostowanie kontrolki użytkownika formularza systemu Windows jako okna dialogowego MFC
Biblioteka MFC zawiera klasę szablonu [CWinFormsDialog](../mfc/reference/cwinformsdialog-class.md) tak, że można obsługiwać formant użytkownika interfejsu Windows Forms (<xref:System.Windows.Forms.UserControl>) w modalnym lub niemodalnym oknie dialogowym MFC. `CWinFormsDialog` pochodzi od klasy MFC [CDialog](../mfc/reference/cdialog-class.md), dzięki czemu można uruchomić jako modalne lub niemodalne okno dialogowe.  
  
 Ten proces, `CWinFormsDialog` używa do hostowania formantu użytkownika jest podobny do tego opisanego w [hostowanie kontrolki użytkownika formularzy Windows w oknie dialogowym MFC](../dotnet/hosting-a-windows-form-user-control-in-an-mfc-dialog-box.md). Jednak `CWinFormsDialog` zarządza inicjowaniem i hostingiem kontroli użytkownika, tak aby nie musi być programowana ręcznie.  
  
 Dla przykładowej aplikacji, który pokazuje formularze Windows używane z biblioteką MFC, zobacz [MFC i integracji formularzy Windows](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en).  
  
### <a name="to-create-the-mfc-host-application"></a>Aby utworzyć aplikację hosta MFC  
  
1.  Utwórz projekt aplikacji MFC.  
  
     Na **pliku** menu, wybierz opcję **New**, a następnie kliknij przycisk **projektu**. W **Visual C++** folderu, wybierz **aplikacji MFC**.  
  
     W **nazwa** wprowadź `MFC03` i zmień ustawienie rozwiązanie na **Dodaj do rozwiązania**. Kliknij przycisk **OK**.  
  
     W **Kreator aplikacji MFC**Zaakceptuj wszystkie ustawienia domyślne, a następnie kliknij przycisk **Zakończ**. Tworzy to aplikację MFC z interfejsem wielu dokumentów.  
  
2.  Konfigurowanie projektu.  
  
     W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **MFC03** węzła projektu, a następnie wybierz **właściwości**. **Stron właściwości** pojawi się okno dialogowe.  
  
     W **stron właściwości** dialogowym **właściwości konfiguracji** formantu drzewa, wybierz opcję **ogólne**, a następnie w obszarze **domyślnewartościprojektu**sekcji, ustaw **Obsługa środowiska uruchomieniowego języka wspólnego** do **wsparcie (/ clr)**. Kliknij przycisk **OK**.  
  
3.  Dodaj odwołanie do formantu .NET.  
  
     W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **MFC03** węzeł projektu i wybierz polecenie **Dodaj**, **odwołania**. W **strona właściwości**, kliknij przycisk **Dodaj nowe odwołanie**, zaznacz pozycję WindowsControlLibrary1 (w obszarze **projektów** karty) i kliknij przycisk **OK**. Dodaje to odwołanie w formie [/FU](../build/reference/fu-name-forced-hash-using-file.md) — opcja kompilatora tak, aby program został skompilowany; kopiuje również WindowsControlLibrary1.dll do `MFC03` katalogu projektu, dzięki czemu program będzie uruchamiany.  
  
4.  Dodaj `#include <afxwinforms.h>` do stdafx.h, na końcu istniejącej `#include` instrukcji.  
  
5.  Dodaj nową klasę tej podklasy `CDialog`.  
  
     Kliknij prawym przyciskiem myszy nazwę projektu i dodać klasę MFC (o nazwie chostforwinform podzieloną) na podklasy `CDialog`. Ponieważ zasobu okna dialogowego pole nie jest potrzebne, można usunąć Identyfikatora zasobu (zaznacz widok zasobu, rozwiń Dialog folder i Usuń zasób IDD_HOSTFORWINFORM.  Następnie usuń wszelkie odwołania do Identyfikatora w kodzie.).  
  
6.  Zastąp `CDialog` w plikach CHostForWinForm.h i CHostForWinForm.cpp z `CWinFormsDialog<WindowsControlLibrary1::UserControl1>`.  
  
7.  Wywołanie DoModal klasy CHostForWinForm.  
  
     W pliku MFC03.cpp Dodaj `#include "HostForWinForm.h"`.  
  
     Przed instrukcją powrotu w definicji cmfc03app::initinstance należy dodać:  
  
    ```cpp
    CHostForWinForm m_HostForWinForm;
    m_HostForWinForm.DoModal();
    ```
  
8.  Skompiluj i uruchom projekt.  
  
     Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.  
  
     Na **debugowania** menu, kliknij przycisk **Uruchom bez debugowania**.  
  
     Następnie dodasz kod do monitorowania stanu formantu w interfejsie Windows Forms z aplikacji MFC.  
  
9. Dodawanie obsługi dla OnInitDialog.  
  
     Wyświetlanie **właściwości** okna (F4). W **Widok klas**, wybierz pozycję CHostForWinForm. W **właściwości** okna, zaznacz zastąpienia i w wierszu zdarzenia OnInitDialog kliknij w lewej kolumnie i zaznacz \< Dodaj >. Spowoduje to dodanie następujący wiersz do CHostForWinForm.h:  
  
    ```cpp  
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
  
11. Następnie Dodaj program obsługi OnButton1. Dodaj następujące wiersze do sekcji publicznej klasy CHostForWinForm w obiekcie CHostForWinForm.h:  
  
    ```  
    virtual void OnButton1( System::Object^ sender, System::EventArgs^ e );  
  
    BEGIN_DELEGATE_MAP( CHostForWinForm )  
       EVENT_DELEGATE_ENTRY( OnButton1, System::Object^, System::EventArgs^ );  
    END_DELEGATE_MAP()  
    ```  
  
     W pliku CHostForWinForm.cpp Dodaj tę definicję:  
  
    ```  
    void CHostForWinForm::OnButton1( System::Object^ sender, System::EventArgs^ e )   
    {  
       System::Windows::Forms::MessageBox::Show("test");  
    }  
    ```  
  
12. Skompiluj i uruchom projekt. Po kliknięciu przycisku, który znajduje się w formularzu Windows, uruchomi się kod w aplikacji MFC.  
  
     Następnie dodasz kod, aby wyświetlić z kodu MFC wartość w polu tekstowym w formularzu Windows.  
  
13. W sekcji publicznej klasy CHostForWinForm w obiekcie CHostForWinForm.h należy dodać następującą deklarację:  
  
    ```  
    CString m_sEditBoxOnWinForm;  
    ```  
  
14. W definicji elementu DoDataExchange w pliku CHostForWinForm.cpp należy dodać następujące trzy wiersze na końcu funkcji:  
  
    ```  
    if (pDX->m_bSaveAndValidate)  
       m_sEditBoxOnWinForm = CString( GetControl()->textBox1->Text);  
    else  
       GetControl()->textBox1->Text = gcnew System::String(m_sEditBoxOnWinForm);  
    ```  
  
15. W definicji elementu OnButton1 w pliku CHostForWinForm.cpp należy dodać następujące trzy wiersze na końcu funkcji:  
  
    ```  
    this->UpdateData(TRUE);  
    System::String ^ z = gcnew System::String(m_sEditBoxOnWinForm);  
    System::Windows::Forms::MessageBox::Show(z);  
    ```  
  
16. Skompiluj i uruchom projekt.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.UserControl?displayProperty=fullName>   
 [Używanie kontrolki użytkownika formularza systemu Windows w MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md)