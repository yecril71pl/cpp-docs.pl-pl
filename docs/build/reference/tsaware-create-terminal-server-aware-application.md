---
title: -TSAWARE (Utwórz aplikację świadomą serwera terminali) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /tsaware
- VC.Project.VCLinkerTool.TerminalServerAware
dev_langs:
- C++
helpviewer_keywords:
- Terminal Server
- /TSAWARE linker option
- Terminal Server, Terminal Server-aware applications
- -TSAWARE linker option
- TSAWARE linker option
ms.assetid: fe1c1846-de5b-4839-b562-93fbfe36cd29
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9caf6c9a47a667b57220b6bf577080d3548e94e9
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43198553"
---
# <a name="tsaware-create-terminal-server-aware-application"></a>/TSAWARE (Utwórz aplikację świadomą serwera terminali)
```  
/TSAWARE[:NO]  
```  
  
## <a name="remarks"></a>Uwagi  
 Opcja/tsaware ustawia flagę w polu IMAGE_OPTIONAL_HEADER dllcharacteristics w opcjonalnym nagłówku obrazu programu. Gdy ta flaga jest ustawiona, serwera terminali nie wprowadzi pewnych zmian aplikacji.  
  
 Jeśli aplikacja nie jest świadome serwera terminali (znany także jako starszych aplikacji), serwer terminali sprawia, że pewne zmiany na starszą aplikację, aby działać poprawnie w środowisku wielodostępnym. Na przykład serwera terminali utworzy folder wirtualny Windows tak, aby każdy użytkownik otrzyma folder Windows zamiast uzyskiwania systemu Windows katalogu. To zapewnia użytkownikom dostęp do swoich plików INI. Ponadto serwer terminali sprawia, że pewnych zmian w rejestrze dla starszych aplikacji. Te modyfikacje spowolnić ładowanie starszych aplikacji na serwerze terminali.  
  
 Jeśli aplikacja jest świadome serwera terminali, jego musi korzystają z plików INI ani zapisać **HKEY_CURRENT_USER** rejestru podczas instalacji.  
  
 Jeśli używasz/tsaware, a aplikacja nadal używa plików INI, pliki będą udostępniane przez wszystkich użytkowników systemu. Jeżeli jest to akceptowalne, nadal można połączyć aplikacji za pomocą/tsaware; w przeciwnym razie należy użyć aktywność.  
  
 Opcja/tsaware jest domyślnie włączona, Windows i aplikacji konsoli. Zobacz [/Subsystem](../../build/reference/subsystem-specify-subsystem.md) i [Version](../../build/reference/version-version-information.md) informacji.  
  
 / TSAWARE nie jest prawidłowy dla sterowników, urządzenia vxd lub biblioteki dll.  
  
 Jeśli aplikacja została połączona z/tsaware, DUMPBIN [/HEADERS](../../build/reference/headers.md) spowoduje to wyświetlenie informacji w tym celu.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [ustawienie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **konsolidatora** folderu.  
  
3.  Kliknij przycisk **systemu** stronę właściwości.  
  
4.  Modyfikowanie **serwera terminali** właściwości.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TerminalServerAware%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)   
 [Przechowywanie informacji o użytkowniku](/windows/desktop/TermServ/storing-user-specific-information)   
 [Starsze aplikacje w środowisku usług terminalowych](https://msdn.microsoft.com/library/aa382957.aspx)