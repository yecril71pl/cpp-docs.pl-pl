---
title: Strony właściwości konsolidatora
ms.date: 11/21/2017
f1_keywords:
- VC.Project.VCLinkerTool.RegisterOutput
- VC.Project.VCLinkerTool.OVERWRITEImportLibrary
- VC.Project.VCLinkerTool.UseLibraryDependencyInputs
- VC.Project.VCLinkerTool.LinkLibraryDependencies
helpviewer_keywords:
- per-user redirection
- Linker property pages
ms.assetid: 7e7671e5-a35a-4e67-9bdb-661d75c4d11e
ms.openlocfilehash: 1412531ae0ca9c0f5270df6df7b79ddc9be425ad
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823640"
---
# <a name="linker-property-pages"></a>Strony właściwości konsolidatora

W tym temacie omówiono następujące właściwości na **ogólne** strony właściwości konsolidatora. Wersja systemu Linux na tej stronie, zobacz [właściwości konsolidatora (Linux C++)](../../linux/prop-pages/linker-linux.md).

## <a name="general-page-properties"></a>Ogólna strona właściwości

### <a name="ignore-import-library"></a>Ignoruj biblioteki importowane

Ta właściwość informuje konsolidator, nie można połączyć żadnych plików wyjściowych .lib generowany na podstawie tej kompilacji z żadnym zależnym projektem. Dzięki temu system projektu może obsługiwać pliki .dll, które podczas kompilacji nie tworzą pliku .lib. Jeśli projekt zależy od innego projektu, który tworzy bibliotekę DLL, system projektu automatycznie łączy plik .lib generowany przez ten projekt podrzędny. Może to być niepotrzebne w projektach generujących pliki COM DLL lub pliki DLL z samymi zasobami, ponieważ te pliki DLL nie eksportują żadnych istotnych danych. Jeśli biblioteka DLL nie eksportuje żadnych danych, konsolidator nie generuje pliku. lib. Nie pliku .lib eksportu jest obecny na dysku, a system projektu nakaże konsolidatorowi nawiązanie połączenia z tym (brakującym) plikiem DLL, łącze nie powiedzie się. Użyj **Ignoruj biblioteki importowane** właściwości, aby rozwiązać ten problem. Po ustawieniu **tak**, system projektu ignoruje obecność lub brak takiego pliku .lib i powoduje, że żaden projekt zależny od tego projektu nie łączy się z nieistniejącej pożądane.

Aby programowo uzyskać dostęp do tej właściwości, zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreImportLibrary%2A>.

### <a name="register-output"></a>Rejestruj produkt wyjściowy

Przebiegi `regsvr32.exe /s $(TargetPath)` na dane wyjściowe kompilacji, który jest prawidłowy tylko wobec projektów bibliotek .dll. W projektach plików .exe właściwość jest ignorowana. Aby zarejestrować dane wyjściowe .exe, należy ustawić zdarzenie po kompilacji na konfigurację niestandardową rejestrację, który jest zawsze wymagany rejestrowaniu plików .exe.

Aby programowo uzyskać dostęp do tej właściwości, zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.RegisterOutput%2A>.

### <a name="per-user-redirection"></a>Przekierowanie na użytkownika

Rejestracja w programie Visual Studio była tradycyjnie wykonywana w kluczu HKEY_CLASSES_ROOT (HKCR). Windows Vista i nowszych systemach operacyjnych dostęp do klucza HKCR należy uruchomić program Visual Studio w trybie podniesionych uprawnień. Deweloperzy nie zawsze chcą pracować w trybie podwyższonych uprawnień, a mimo to muszą dokonywać rejestracji. Przekierowanie na użytkownika umożliwia rejestrowanie bez konieczności pracy w tym trybie.

Przekierowanie na użytkownika wymusza na wszelkie operacje zapisu do klucza HKCR były przekierowywane do HKEY\_bieżącego\_użytkownika (HKCU). Jeśli przekierowanie na użytkownika jest wyłączona, może to spowodować [błąd kompilacji projektu PRJ0050](../../error-messages/tool-errors/project-build-error-prj0050.md) gdy program próbuje zapisać do klucza HKCR.

### <a name="link-library-dependencies"></a>Połącz zależności biblioteki

Określa, czy łączenie plików .lib generowanych przez zależne projekty. Zazwyczaj który chcesz połączyć z plików .lib, ale to może nie być w przypadku niektórych bibliotek DLL.

Plik .obj można również określić, podając nazwę pliku i ścieżki względnej, na przykład "... \\.. \MyLibProject\MyObjFile.obj". Jeśli kod źródłowy pliku .obj #includes wstępnie skompilowany nagłówek, np. pch.h, plik pch.obj znajduje się w tym samym folderze co MyObjFile.obj i pch.obj należy również dodać jako dodatkową zależność.

### <a name="use-library-dependency-inputs"></a>Używaj wejść biblioteki zależności

W dużym projekcie, gdy projekt zależny tworzy plik .lib, łączenie przyrostowe jest wyłączone. Jeśli istnieje wiele projektów zależnych generujących pliki .lib, kompilowanie aplikacji może trwać długo. Jeśli ta właściwość jest równa **tak**, system projektu łączy pliki .obj dla plików .libs tworzonych produkowane przez projekty zależne, umożliwiając w ten sposób łączenie przyrostowe.

Aby uzyskać informacje o tym, jak uzyskać dostęp do **ogólne** strony właściwości konsolidatora, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

## <a name="see-also"></a>Zobacz także

[Ustawienia projektu VC++, Projekty i rozwiązania, Opcje — okno dialogowe](/visualstudio/ide/reference/vcpp-project-settings-projects-and-solutions-options-dialog-box)<br>
[Dokumentacja strony właściwości projektu C++](property-pages-visual-cpp.md)