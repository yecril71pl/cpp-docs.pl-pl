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
ms.openlocfilehash: 8b30491b2cb46ab0e8b25edc2d39e6616817c9b4
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2018
ms.locfileid: "42465690"
---
# <a name="how-to-add-restart-manager-support"></a>Porady: dodawanie obsługi menedżera ponownego uruchamiania

Menedżera ponownego uruchamiania to funkcja, dodany do programu Visual Studio for Windows Vista lub nowszych systemach operacyjnych. Menedżera ponownego uruchamiania dodaje obsługę aplikacji, jeśli nieoczekiwane zamknięcie lub ponowne uruchomienie. Zachowanie Menedżera ponownego uruchamiania, zależy od typu aplikacji. Jeśli aplikacja jest edytora dokumentów, Menedżera ponownego uruchamiania włączone automatyczne zapisywanie stanu aplikacji i zawartości wszelkie otwarte dokumenty i uruchamia ponownie aplikację po nieoczekiwanego zamknięcia. Jeśli aplikacja nie jest edytora dokumentów, Menedżera ponownego uruchamiania spowoduje ponowne uruchomienie aplikacji, ale domyślnie nie może zapisać stanu aplikacji.  
  
 Po ponownym uruchomieniu aplikacji wyświetli okno dialogowe zadania, jeśli aplikacja jest Unicode. Jeśli jest to aplikacja ANSI, aplikacja wyświetla okno komunikatu Windows. W tym momencie użytkownik wybierze opcję Przywróć automatycznie zapisane dokumenty. Jeśli użytkownik nie przywraca automatycznie zapisanych dokumentów, Menedżera ponownego uruchamiania odrzuca plików tymczasowych.  
  
> [!NOTE]
>  Można zastąpić domyślne zachowanie Menedżera ponownego uruchamiania, zapisywania danych i ponowne uruchomienie aplikacji.  
  
 Domyślnie aplikacje MFC, utworzone przy użyciu Kreatora projektu w programie Visual Studio obsługuje Menedżera ponownego uruchamiania, gdy aplikacje są uruchamiane na komputerze, który ma Windows Vista lub nowszym systemem operacyjnym. Jeśli użytkownik nie chce aplikacji do obsługi Menedżera ponownego uruchamiania, możesz wyłączyć Menedżera ponownego uruchamiania Kreatora nowego projektu.  
  
### <a name="to-add-support-for-the-restart-manager-to-an-existing-application"></a>Dodanie obsługi Menedżera ponownego uruchamiania do istniejącej aplikacji  
  
1.  Otwórz istniejącą aplikację MFC w programie Visual Studio.  
  
2.  Otwórz plik źródłowy dla głównej aplikacji. Domyślnie jest to plik .cpp, który ma taką samą nazwę jak aplikacja. Na przykład plik źródłowy aplikacji głównej MyProject jest MyProject.cpp.  
  
3.  Znajdź Konstruktor dla głównej aplikacji. Na przykład, jeśli projekt jest MyProject, Konstruktor jest `CMyProjectApp::CMyProjectApp()`.  
  
4.  Dodaj następujący wiersz kodu do konstruktora.  
  
 ```  
    m_dwRestartManagerSupportFlags = AFX_RESTART_MANAGER_SUPPORT_ALL_ASPECTS;  
 ```  
  
5.  Upewnij się, że `InitInstance` metoda aplikacji wywołuje jego element nadrzędny `InitInstance` metoda: [CWinApp::InitInstance](../mfc/reference/cwinapp-class.md#initinstance) lub `CWinAppEx::InitInstance`. `InitInstance` Metoda jest odpowiedzialna za sprawdzanie *m_dwRestartManagerSupportFlags* parametru.  
  
6.  Skompiluj i uruchom aplikację.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CDataRecoveryHandler](../mfc/reference/cdatarecoveryhandler-class.md)   
 [CWinApp::m_dwRestartManagerSupportFlags](../mfc/reference/cwinapp-class.md#m_dwrestartmanagersupportflags)   
 [Klasa CWinApp](../mfc/reference/cwinapp-class.md)   
 [CWinApp::m_nAutosaveInterval](../mfc/reference/cwinapp-class.md#m_nautosaveinterval)   
 [CDocument::OnDocumentEvent](../mfc/reference/cdocument-class.md#ondocumentevent)

