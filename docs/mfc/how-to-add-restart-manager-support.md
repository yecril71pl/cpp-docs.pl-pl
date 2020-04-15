---
title: 'Porady: dodawanie obsługi menedżera ponownego uruchamiania'
ms.date: 11/04/2016
helpviewer_keywords:
- Restart manager [MFC]
- C++, application crash support
ms.assetid: 7f3f5867-d4bc-4ba8-b3c9-dc1e7be93642
ms.openlocfilehash: 7cf3fede663a7c4bc85573e17dd9c2f8bf3622b4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373316"
---
# <a name="how-to-add-restart-manager-support"></a>Porady: dodawanie obsługi menedżera ponownego uruchamiania

Menedżer ponownego uruchamiania to funkcja dodana do programu Visual Studio dla systemów operacyjnych Windows Vista lub nowszych. Menedżer ponownego uruchamiania dodaje obsługę aplikacji, jeśli nieoczekiwanie zostanie zamknięta lub ponownie uruchomiona. Zachowanie menedżera ponownego uruchamiania zależy od typu aplikacji. Jeśli aplikacja jest edytorem dokumentów, menedżer ponownego uruchamiania włączył aplikację do automatycznego zapisywania stanu i zawartości wszystkich otwartych dokumentów i uruchamia ponownie aplikację po nieoczekiwanym zamknięciu. Jeśli aplikacja nie jest edytorem dokumentów, menedżer ponownego uruchamiania uruchomi ponownie aplikację, ale domyślnie nie może zapisać stanu aplikacji.

Po ponownym uruchomieniu aplikacja wyświetla okno dialogowe zadania, jeśli aplikacja jest Unicode. Jeśli jest to aplikacja ANSI, aplikacja wyświetla okno komunikatu systemu Windows. W tym momencie użytkownik decyduje, czy mają być przywracane automatycznie zapisane dokumenty. Jeśli użytkownik nie przywróci automatycznie zapisanych dokumentów, menedżer ponownego uruchomienia odrzuci pliki tymczasowe.

> [!NOTE]
> Można zastąpić domyślne zachowanie menedżera ponownego uruchamiania w celu zapisania danych i ponownego uruchomienia aplikacji.

Domyślnie aplikacje MFC utworzone przy użyciu kreatora projektu w programie Visual Studio obsługują menedżera ponownego uruchamiania, gdy aplikacje są uruchamiane na komputerze z systemem operacyjnym Windows Vista lub nowszym. Jeśli nie chcesz, aby aplikacja obsługiwała menedżera ponownego uruchamiania, możesz wyłączyć menedżera ponownego uruchamiania w nowym kreatorze projektu.

### <a name="to-add-support-for-the-restart-manager-to-an-existing-application"></a>Aby dodać obsługę Menedżera ponownego uruchamiania do istniejącej aplikacji

1. Otwórz istniejącą aplikację MFC w programie Visual Studio.

1. Otwórz plik źródłowy dla głównej aplikacji. Domyślnie jest to plik .cpp, który ma taką samą nazwę jak aplikacja. Na przykład głównym plikiem źródłowym aplikacji dla MyProject jest MyProject.cpp.

1. Znajdź konstruktora dla głównej aplikacji. Na przykład jeśli projekt jest MyProject, `CMyProjectApp::CMyProjectApp()`konstruktorem jest .

1. Dodaj następujący wiersz kodu do konstruktora.

```
    m_dwRestartManagerSupportFlags = AFX_RESTART_MANAGER_SUPPORT_ALL_ASPECTS;
```

1. Upewnij `InitInstance` się, że metoda aplikacji `InitInstance` wywołuje metodę nadrzędną: [CWinApp::InitInstance](../mfc/reference/cwinapp-class.md#initinstance) lub `CWinAppEx::InitInstance`. Metoda `InitInstance` jest odpowiedzialna za sprawdzenie *parametru m_dwRestartManagerSupportFlags.*

1. Skompiluj i uruchom aplikację.

## <a name="see-also"></a>Zobacz też

[Klasa CDataRecoveryHandler](../mfc/reference/cdatarecoveryhandler-class.md)<br/>
[CWinApp::m_dwRestartManagerSupportFlags](../mfc/reference/cwinapp-class.md#m_dwrestartmanagersupportflags)<br/>
[Klasa CWinApp](../mfc/reference/cwinapp-class.md)<br/>
[CWinApp::m_nAutosaveInterval](../mfc/reference/cwinapp-class.md#m_nautosaveinterval)<br/>
[CDocument::OnDocumentEvent](../mfc/reference/cdocument-class.md#ondocumentevent)
