---
title: 'Instrukcje: Dodawanie obsługi Menedżera ponownego uruchamiania'
ms.date: 11/04/2016
helpviewer_keywords:
- Restart manager [MFC]
- C++, application crash support
ms.assetid: 7f3f5867-d4bc-4ba8-b3c9-dc1e7be93642
ms.openlocfilehash: 23f860c43c63e3153f4b87f8eaf05d61709af82f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62389531"
---
# <a name="how-to-add-restart-manager-support"></a>Instrukcje: Dodawanie obsługi Menedżera ponownego uruchamiania

Menedżera ponownego uruchamiania to funkcja, dodany do programu Visual Studio for Windows Vista lub nowszych systemach operacyjnych. Menedżera ponownego uruchamiania dodaje obsługę aplikacji, jeśli nieoczekiwane zamknięcie lub ponowne uruchomienie. Zachowanie Menedżera ponownego uruchamiania, zależy od typu aplikacji. Jeśli aplikacja jest edytora dokumentów, Menedżera ponownego uruchamiania włączone automatyczne zapisywanie stanu aplikacji i zawartości wszelkie otwarte dokumenty i uruchamia ponownie aplikację po nieoczekiwanego zamknięcia. Jeśli aplikacja nie jest edytora dokumentów, Menedżera ponownego uruchamiania spowoduje ponowne uruchomienie aplikacji, ale domyślnie nie może zapisać stanu aplikacji.

Po ponownym uruchomieniu aplikacji wyświetli okno dialogowe zadania, jeśli aplikacja jest Unicode. Jeśli jest to aplikacja ANSI, aplikacja wyświetla okno komunikatu Windows. W tym momencie użytkownik wybierze opcję Przywróć automatycznie zapisane dokumenty. Jeśli użytkownik nie przywraca automatycznie zapisanych dokumentów, Menedżera ponownego uruchamiania odrzuca plików tymczasowych.

> [!NOTE]
>  Można zastąpić domyślne zachowanie Menedżera ponownego uruchamiania, zapisywania danych i ponowne uruchomienie aplikacji.

Domyślnie aplikacje MFC, utworzone przy użyciu Kreatora projektu w programie Visual Studio obsługuje Menedżera ponownego uruchamiania, gdy aplikacje są uruchamiane na komputerze, który ma Windows Vista lub nowszym systemem operacyjnym. Jeśli użytkownik nie chce aplikacji do obsługi Menedżera ponownego uruchamiania, możesz wyłączyć Menedżera ponownego uruchamiania Kreatora nowego projektu.

### <a name="to-add-support-for-the-restart-manager-to-an-existing-application"></a>Dodanie obsługi Menedżera ponownego uruchamiania do istniejącej aplikacji

1. Otwórz istniejącą aplikację MFC w programie Visual Studio.

1. Otwórz plik źródłowy dla głównej aplikacji. Domyślnie jest to plik .cpp, który ma taką samą nazwę jak aplikacja. Na przykład plik źródłowy aplikacji głównej MyProject jest MyProject.cpp.

1. Znajdź Konstruktor dla głównej aplikacji. Na przykład, jeśli projekt jest MyProject, Konstruktor jest `CMyProjectApp::CMyProjectApp()`.

1. Dodaj następujący wiersz kodu do konstruktora.

```
    m_dwRestartManagerSupportFlags = AFX_RESTART_MANAGER_SUPPORT_ALL_ASPECTS;
```

1. Upewnij się, że `InitInstance` metoda aplikacji wywołuje jego element nadrzędny `InitInstance` metody: [CWinApp::InitInstance](../mfc/reference/cwinapp-class.md#initinstance) lub `CWinAppEx::InitInstance`. `InitInstance` Metoda jest odpowiedzialna za sprawdzanie *m_dwRestartManagerSupportFlags* parametru.

1. Skompiluj i uruchom aplikację.

## <a name="see-also"></a>Zobacz także

[Klasa CDataRecoveryHandler](../mfc/reference/cdatarecoveryhandler-class.md)<br/>
[CWinApp::m_dwRestartManagerSupportFlags](../mfc/reference/cwinapp-class.md#m_dwrestartmanagersupportflags)<br/>
[Klasa CWinApp](../mfc/reference/cwinapp-class.md)<br/>
[CWinApp::m_nAutosaveInterval](../mfc/reference/cwinapp-class.md#m_nautosaveinterval)<br/>
[CDocument::OnDocumentEvent](../mfc/reference/cdocument-class.md#ondocumentevent)
