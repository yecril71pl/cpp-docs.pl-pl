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
ms.openlocfilehash: e386c9024ea7736adb2766488c1c51c80ff7177b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="tsaware-create-terminal-server-aware-application"></a>/TSAWARE (Utwórz aplikację świadomą serwera terminali)
```  
/TSAWARE[:NO]  
```  
  
## <a name="remarks"></a>Uwagi  
 Opcja/tsaware ustawia flagę w polu IMAGE_OPTIONAL_HEADER DllCharacteristics w obrazie programu opcjonalne nagłówki. Gdy ta flaga jest ustawiona, serwer terminali nie wprowadzić pewne zmiany do aplikacji.  
  
 Jeśli aplikacja nie jest świadome serwera terminali (znanej także jako starszych aplikacji), serwer terminali sprawia, że pewne zmiany do starszej wersji aplikacji, aby działać poprawnie w środowisku wielodostępnym. Na przykład serwera terminali utworzy folder wirtualny systemu Windows tak, aby każdy użytkownik otrzymuje zamiast pobierania systemu Windows katalogu folderu systemu Windows. To umożliwia użytkownikom dostęp do swoich plików INI. Ponadto serwer terminali sprawia, że pewnych zmian w rejestrze dla starszych aplikacji. Te modyfikacje spowalniać ładowanie starszych aplikacji na terminalu.  
  
 Jeśli aplikacja jest świadome serwera terminali, jego musi korzystają z plików INI ani zapisać **HKEY_CURRENT_USER** rejestru podczas instalacji.  
  
 Jeśli używasz/tsaware i aplikacja nadal używa plików INI, pliki będzie współdzielona przez wszystkich użytkowników systemu. Jeśli jest to dopuszczalne, nadal można połączyć aplikacji z/tsaware; w przeciwnym razie należy użyć: no.  
  
 Opcja/tsaware jest domyślnie włączona dla systemów Windows i aplikacji konsoli. Zobacz [/Subsystem](../../build/reference/subsystem-specify-subsystem.md) i [/Version](../../build/reference/version-version-information.md) informacji.  
  
 / TSAWARE jest nieprawidłowa dla sterowników, urządzenia vxd lub biblioteki dll.  
  
 Jeśli aplikacja został połączony z/tsaware, DUMPBIN [/HEADERS](../../build/reference/headers.md) spowoduje wyświetlenie informacji w tym celu.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Ustawianie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **konsolidatora** folderu.  
  
3.  Kliknij przycisk **systemu** strony właściwości.  
  
4.  Modyfikowanie **serwera terminali** właściwości.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TerminalServerAware%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)   
 [Przechowuje informacje specyficzne dla użytkownika](http://msdn.microsoft.com/library/aa383452)   
 [Starsze aplikacje w środowisku usług terminalowych](https://msdn.microsoft.com/en-us/library/aa382957.aspx)