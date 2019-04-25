---
title: /TSAWARE (Utwórz aplikację świadomą serwera terminali)
ms.date: 11/04/2016
f1_keywords:
- /tsaware
- VC.Project.VCLinkerTool.TerminalServerAware
helpviewer_keywords:
- Terminal Server
- /TSAWARE linker option
- Terminal Server, Terminal Server-aware applications
- -TSAWARE linker option
- TSAWARE linker option
ms.assetid: fe1c1846-de5b-4839-b562-93fbfe36cd29
ms.openlocfilehash: f6ed6184f8ae4b3a0f9db3c1f962a2918a185138
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62317435"
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

Opcja/tsaware jest domyślnie włączona, Windows i aplikacji konsoli. Zobacz [/Subsystem](subsystem-specify-subsystem.md) i [Version](version-version-information.md) informacji.

/ TSAWARE nie jest prawidłowy dla sterowników, urządzenia vxd lub biblioteki dll.

Jeśli aplikacja została połączona z/tsaware, DUMPBIN [/HEADERS](headers.md) spowoduje to wyświetlenie informacji w tym celu.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Kliknij przycisk **konsolidatora** folderu.

1. Kliknij przycisk **systemu** stronę właściwości.

1. Modyfikowanie **serwera terminali** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TerminalServerAware%2A>.

## <a name="see-also"></a>Zobacz także

[Dokumentacja konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)<br/>
[Przechowywanie informacji o użytkowniku](/windows/desktop/TermServ/storing-user-specific-information)<br/>
[Starsze aplikacje w środowisku usług terminalowych](https://msdn.microsoft.com/library/aa382957.aspx)
