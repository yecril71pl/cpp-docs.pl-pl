---
title: 'Porady: dodawanie obsługi menedżera ponownego uruchamiania'
ms.date: 11/04/2016
helpviewer_keywords:
- Restart manager [MFC]
- C++, application crash support
ms.assetid: 7f3f5867-d4bc-4ba8-b3c9-dc1e7be93642
ms.openlocfilehash: 848cb3bb52ae13eb1b7798126becd13384fddeb6
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625652"
---
# <a name="how-to-add-restart-manager-support"></a>Porady: dodawanie obsługi menedżera ponownego uruchamiania

Menedżer ponownego uruchamiania to funkcja dodana do programu Visual Studio dla systemu Windows Vista lub nowszych systemów operacyjnych. Menedżer ponownego uruchamiania dodaje obsługę aplikacji w przypadku nieoczekiwanego zamknięcia lub ponownego uruchomienia. Zachowanie Menedżera ponownego uruchamiania zależy od typu aplikacji. Jeśli aplikacja jest edytorem dokumentów, Menedżer ponownego uruchamiania włączył aplikację w celu automatycznego zapisania stanu i zawartości wszelkich otwartych dokumentów i ponownego uruchomienia aplikacji po nieoczekiwanym zamknięciu. Jeśli aplikacja nie jest edytorem dokumentów, Menedżer ponownego uruchamiania ponownie uruchomi aplikację, ale nie będzie mógł zapisać stanu aplikacji domyślnie.

Po ponownym uruchomieniu aplikacja wyświetli okno dialogowe zadania, jeśli aplikacja jest w formacie Unicode. Jeśli jest to aplikacja ANSI, aplikacja wyświetli okno komunikatu systemu Windows. W tym momencie użytkownik zdecyduje, czy mają zostać przywrócone automatycznie zapisane dokumenty. Jeśli użytkownik nie przywróci automatycznie zapisanych dokumentów, Menedżer ponownego uruchamiania odrzuca pliki tymczasowe.

> [!NOTE]
> Można zastąpić domyślne zachowanie Menedżera ponownego uruchamiania na potrzeby zapisywania danych i ponownego uruchamiania aplikacji.

Domyślnie aplikacje MFC tworzone przy użyciu Kreatora projektu w programie Visual Studio obsługują Menedżera ponownego uruchamiania, gdy aplikacje są uruchamiane na komputerze z systemem operacyjnym Windows Vista lub nowszym. Jeśli nie chcesz, aby aplikacja obsługiwała Menedżera ponownego uruchamiania, możesz wyłączyć Menedżera ponownego uruchamiania w Kreatorze nowego projektu.

### <a name="to-add-support-for-the-restart-manager-to-an-existing-application"></a>Aby dodać obsługę Menedżera ponownego uruchamiania do istniejącej aplikacji

1. Otwórz istniejącą aplikację MFC w programie Visual Studio.

1. Otwórz plik źródłowy aplikacji głównej. Domyślnie jest to plik. cpp, który ma taką samą nazwę jak aplikacja. Na przykład główny plik źródłowy aplikacji dla elementu WebProject ma wartość WebProject. cpp.

1. Znajdź konstruktora dla głównej aplikacji. Na przykład, jeśli projekt jest projektem, Konstruktor jest `CMyProjectApp::CMyProjectApp()` .

1. Dodaj następujący wiersz kodu do konstruktora.

```
    m_dwRestartManagerSupportFlags = AFX_RESTART_MANAGER_SUPPORT_ALL_ASPECTS;
```

1. Upewnij się, że `InitInstance` Metoda aplikacji wywołuje metodę nadrzędną `InitInstance` : [CWinApp:: InitInstance](reference/cwinapp-class.md#initinstance) lub `CWinAppEx::InitInstance` . `InitInstance`Metoda jest odpowiedzialna za sprawdzanie *m_dwRestartManagerSupportFlags* parametru.

1. Skompiluj i uruchom aplikację.

## <a name="see-also"></a>Zobacz też

[Klasa CDataRecoveryHandler](reference/cdatarecoveryhandler-class.md)<br/>
[CWinApp:: m_dwRestartManagerSupportFlags](reference/cwinapp-class.md#m_dwrestartmanagersupportflags)<br/>
[Klasa CWinApp](reference/cwinapp-class.md)<br/>
[CWinApp:: m_nAutosaveInterval](reference/cwinapp-class.md#m_nautosaveinterval)<br/>
[CDocument:: OnDocumentEvent](reference/cdocument-class.md#ondocumentevent)
