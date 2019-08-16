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
ms.openlocfilehash: 981158125cf978c2f685501117f95553df9c3c89
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498187"
---
# <a name="tsaware-create-terminal-server-aware-application"></a>/TSAWARE (Utwórz aplikację świadomą serwera terminali)

```
/TSAWARE[:NO]
```

## <a name="remarks"></a>Uwagi

Opcja/TSAWARE ustawia flagę w polu IMAGE_OPTIONAL_HEADER DllCharacteristics w opcjonalnym nagłówku obrazu programu. Po ustawieniu tej flagi serwer terminali nie wprowadza pewnych zmian do aplikacji.

Gdy aplikacja nie jest rozpoznawana przez serwer terminali (znana także jako Starsza aplikacja), serwer terminali wprowadza pewne modyfikacje starszej aplikacji, aby zapewnić prawidłowe działanie w środowisku wielodostępnym. Na przykład serwer terminali utworzy folder wirtualnego systemu Windows, w taki sposób, że każdy użytkownik otrzyma folder systemu Windows zamiast pobrania katalogu systemu Windows. Zapewnia to użytkownikom dostęp do własnych plików INI. Ponadto serwer terminali wprowadza pewne zmiany w rejestrze dla starszej aplikacji. Te modyfikacje spowalniają ładowanie starszej aplikacji na serwerze terminali.

W przypadku aplikacji obsługujących serwer terminali nie należy polegać na plikach INI ani zapisywać w rejestrze **HKEY_CURRENT_USER** podczas instalacji.

Jeśli używasz/TSAWARE, a aplikacja nadal używa plików INI, pliki będą współużytkowane przez wszystkich użytkowników systemu. Jeśli to możliwe, nadal możesz połączyć swoją aplikację z/TSAWARE; w przeciwnym razie musisz użyć/TSAWARE: NO.

Opcja/TSAWARE jest domyślnie włączona dla aplikacji systemu Windows i konsoli. Aby uzyskać więcej informacji, zobacz [/Subsystem](subsystem-specify-subsystem.md) i [/Version](version-version-information.md) .

/TSAWARE jest nieprawidłowy dla sterowników, VxDs lub bibliotek DLL.

Jeśli aplikacja została połączona z/TSAWARE, polecenia DUMPBIN [/Headers](headers.md) będzie wyświetlała informacje w tym efekcie.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [ C++ Ustawianie właściwości kompilatora i Build w programie Visual Studio](../working-with-project-properties.md).

1. Kliknij folder **konsolidator** .

1. Kliknij stronę właściwości **systemu** .

1. Zmodyfikuj właściwość **serwera terminali** .

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TerminalServerAware%2A>.

## <a name="see-also"></a>Zobacz także

[Dokumentacja konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)<br/>
[Przechowywanie informacji specyficznych dla użytkownika](/windows/win32/TermServ/storing-user-specific-information)<br/>
[Starsze aplikacje w środowisku usług terminalowych](https://msdn.microsoft.com/library/aa382957.aspx)
