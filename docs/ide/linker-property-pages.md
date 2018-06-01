---
title: Strony właściwości konsolidatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/21/2017
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCLinkerTool.RegisterOutput
- VC.Project.VCLinkerTool.OVERWRITEImportLibrary
- VC.Project.VCLinkerTool.UseLibraryDependencyInputs
- VC.Project.VCLinkerTool.LinkLibraryDependencies
dev_langs:
- C++
helpviewer_keywords:
- per-user redirection
- Linker property pages
ms.assetid: 7e7671e5-a35a-4e67-9bdb-661d75c4d11e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2cec232bb4e4f2f6ac1ab9af703b368eec0ba5dd
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "33331522"
---
# <a name="linker-property-pages"></a>Strony właściwości konsolidatora

W tym temacie omówiono następujące właściwości na **ogólne** strony właściwości konsolidatora. Dla wersji systemu Linux na tej stronie, zobacz [właściwości konsolidatora (Linux C++)](../linux/prop-pages/linker-linux.md).

## <a name="general-page-properties"></a>Ogólna strona właściwości

### <a name="ignore-import-library"></a>Ignoruj biblioteki importowane

Ta właściwość informuje konsolidator, nie, aby połączyć wszystkie wartości wyjściowe lib wygenerowane z kompilacji w żadnym projekcie zależnych. Dzięki temu system projektu może obsługiwać pliki .dll, które podczas kompilacji nie tworzą pliku .lib. Jeśli projekt zależy od innego projektu, który tworzy bibliotekę DLL, system projektu automatycznie łączy pliku lib utworzone przez tego projektu podrzędnego. Może to być niepotrzebne w projektach generujących pliki COM DLL lub pliki DLL z samymi zasobami, ponieważ te pliki DLL nie eksportują żadnych istotnych danych. Biblioteka DLL nie ma żadnego eksportu, konsolidator nie generuje pliku lib. Jeśli nie jest obecny na dysku żaden plik .lib eksportu, a system projektu informuje konsolidator, aby połączyć się z tym DLL (Brak), łącze nie powiedzie się. Użyj **Ignoruj bibliotekę importowaną** właściwości, aby rozwiązać ten problem. Jeśli wartość **tak**, system projektu ignoruje obecności lub braku pliku lib i powoduje, że wszystkie projektu, który jest zależny od tego projektu, aby nie łączy się z plikiem nieistniejącą .lib.

Do uzyskania programowego dostępu do tej właściwości, zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreImportLibrary%2A>.

### <a name="register-output"></a>Rejestruj produkt wyjściowy

Uruchamia `regsvr32.exe /s $(TargetPath)` danych wyjściowych kompilacji, która jest prawidłowa tylko dla projektów dll. W projektach plików .exe właściwość jest ignorowana. Aby zarejestrować wyjścia .exe, ustaw postbuild zdarzeń konfiguracji do niestandardowych rejestracji, który jest zawsze wymagany do plików .exe zarejestrowanych.

Do uzyskania programowego dostępu do tej właściwości, zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.RegisterOutput%2A>.

### <a name="per-user-redirection"></a>Przekierowanie na użytkownika

Rejestracja w programie Visual Studio tradycyjnie przeprowadzono wpisów z HKEY_CLASSES_ROOT (HKCR). Systemu Windows Vista i nowszych systemów operacyjnych aby dostęp HKCR należy uruchomić programu Visual Studio w trybie podniesionych uprawnień. Deweloperzy nie zawsze chcą pracować w trybie podwyższonych uprawnień, a mimo to muszą dokonywać rejestracji. Przekierowanie na użytkownika umożliwia rejestrowanie bez konieczności pracy w tym trybie.

Przekierowanie na użytkownika wymusza na dowolnym HKCR do HKEY\_bieżącego\_użytkownika (HKCU). Przekierowanie na użytkownika jest wyłączona, może spowodować [projektu kompilacji błąd PRJ0050](../error-messages/tool-errors/project-build-error-prj0050.md) kiedy program próbuje zapisać w kluczu HKCR.

### <a name="link-library-dependencies"></a>Połącz zależności biblioteki

Określa, czy łącze pliki .lib, które są tworzone przez projektów zależnych. Zazwyczaj który chcesz połączyć z plików lib, ale nie można w przypadku niektórych bibliotek DLL.

Można również określić plik .obj, podając nazwę pliku i ścieżki względnej, na przykład "... \\.. \MyLibProject\MyObjFile.obj". Jeśli kodu źródłowego dla pliku obj. #includes prekompilowanego nagłówka, na przykład pch.h, a następnie plik pch.obj znajduje się w tym samym folderze co MyObjFile.obj i pch.obj należy również dodać jako dodatkowe zależności.

### <a name="use-library-dependency-inputs"></a>Używaj wejść biblioteki zależności

W dużym projekcie, gdy projekt zależny tworzy plik .lib, łączenie przyrostowe jest wyłączone. Jeśli istnieje wiele projektów zależnych generujących pliki .lib, kompilowanie aplikacji może trwać długo. Jeśli ta właściwość jest skonfigurowana **tak**, linki systemu projektu w plikach .obj .libs utworzonego przez projektów zależnych, umożliwiając w ten sposób konsolidowania przyrostowego.

Aby uzyskać informacje dotyczące dostępu do **ogólne** strony właściwości konsolidatora, zobacz [Praca z właściwościami projektu](../ide/working-with-project-properties.md).

## <a name="see-also"></a>Zobacz także

[Ustawienia projektu VC ++, projekty i rozwiązania, opcje — Okno dialogowe](/visualstudio/ide/reference/vcpp-project-settings-projects-and-solutions-options-dialog-box)  
[Strony właściwości](../ide/property-pages-visual-cpp.md)  