---
title: 'Porady: Dodawanie obsługi Menedżera ponownego uruchamiania | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Restart manager [MFC]
- C++, application crash support
ms.assetid: 7f3f5867-d4bc-4ba8-b3c9-dc1e7be93642
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2a2916bd96bf36333a81b2e8a88e62cc8f562e9e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33351157"
---
# <a name="how-to-add-restart-manager-support"></a>Porady: dodawanie obsługi menedżera ponownego uruchamiania

Menedżer ponownego uruchamiania to funkcja dodana do programu Visual Studio dla systemu Windows Vista lub nowszych systemów operacyjnych. Menedżer ponownego uruchamiania dodaje obsługę aplikacji, jeśli nieoczekiwane zamknięcie lub ponowne uruchomienie. Zachowanie ponownego uruchamiania Menedżera zależy od typu aplikacji. Jeśli aplikacja jest Edytor dokumentów, Menedżer ponownego uruchamiania włączona automatycznie Zapisz stan aplikacji i zawartości wszelkie otwarte dokumenty i ponowne uruchomienie aplikacji po nieoczekiwanego zamknięcia. Jeśli aplikacja nie jest to edytor dokumentu, Menedżer ponownego uruchamiania spowoduje ponowne uruchomienie aplikacji, ale domyślnie nie może zapisać stanu aplikacji.  
  
 Po ponownym uruchomieniu aplikacji Wyświetla okno dialogowe zadania, jeśli aplikacja jest Unicode. Jeśli jest to aplikacja ANSI, aplikacja wyświetla komunikat systemu Windows. W tym momencie użytkownik wybierze opcję przywracania automatycznie zapisanych dokumentów. Jeśli użytkownik nie przywraca automatycznie zapisanych dokumentów, Menedżer ponownego uruchamiania odrzuca plików tymczasowych.  
  
> [!NOTE]
>  Można zastąpić domyślne zachowanie Menedżer ponownego uruchamiania zapisywania danych i ponowne uruchomienie aplikacji.  
  
 Domyślnie aplikacje MFC utworzone za pomocą Kreatora projektu w [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] obsługi Menedżera ponownego uruchomienia, gdy aplikacje są uruchamiane na komputerze z systemem Windows Vista lub nowszego systemu operacyjnego. Jeśli chcesz, aby aplikacja do obsługi Menedżera ponownego uruchomienia, można wyłączyć Menedżera ponownego uruchomienia komputera w Kreatorze nowego projektu.  
  
### <a name="to-add-support-for-the-restart-manager-to-an-existing-application"></a>Aby dodać obsługę Menedżer ponownego uruchamiania do istniejącej aplikacji  
  
1.  Otwórz istniejącą aplikację MFC w [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)].  
  
2.  Otwórz plik źródłowy dla głównej aplikacji. Domyślnie jest to plik .cpp, który ma taką samą nazwę jak aplikacji. Na przykład plik źródłowy aplikacji głównej MyProject jest MyProject.cpp.  
  
3.  Znajdź Konstruktor dla głównej aplikacji. Na przykład, jeśli Twój projekt jest MyProject, jest konstruktor `CMyProjectApp::CMyProjectApp()`.  
  
4.  Dodaj następujący wiersz kodu z konstruktora.  
  
 ```  
    m_dwRestartManagerSupportFlags = AFX_RESTART_MANAGER_SUPPORT_ALL_ASPECTS;  
 ```  
  
5.  Upewnij się, że `InitInstance` nadrzędnego wywołania metod aplikacji `InitInstance` metody: [CWinApp::InitInstance](../mfc/reference/cwinapp-class.md#initinstance) lub `CWinAppEx::InitInstance`. `InitInstance` Metoda jest odpowiedzialna za sprawdzanie `m_dwRestartManagerSupportFlags` parametru.  
  
6.  Skompiluj i uruchom aplikację.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CDataRecoveryHandler](../mfc/reference/cdatarecoveryhandler-class.md)   
 [CWinApp::m_dwRestartManagerSupportFlags](../mfc/reference/cwinapp-class.md#m_dwrestartmanagersupportflags)   
 [Cwinapp — klasa](../mfc/reference/cwinapp-class.md)   
 [CWinApp::m_nAutosaveInterval](../mfc/reference/cwinapp-class.md#m_nautosaveinterval)   
 [CDocument::OnDocumentEvent](../mfc/reference/cdocument-class.md#ondocumentevent)

