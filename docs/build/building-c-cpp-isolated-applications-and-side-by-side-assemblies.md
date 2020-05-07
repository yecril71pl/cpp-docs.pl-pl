---
title: Kompilowanie aplikacji izolowanych C/C++ oraz aplikacji wykonywanych równocześnie
ms.date: 05/06/2019
helpviewer_keywords:
- isolated applications [C++]
- WinSxS [C++]
- native assembly cache [C++]
- builds [C++], isolated applications
- side-by-side applications [C++]
- builds [C++], side-by-side assemblies
ms.assetid: 9465904e-76f7-48bd-bb3f-c55d8f1699b6
ms.openlocfilehash: db2978c054362b6c329fb786d0f7da322d4c9201
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169880"
---
# <a name="building-cc-isolated-applications-and-side-by-side-assemblies"></a>Kompilowanie aplikacji izolowanych C/C++ oraz aplikacji wykonywanych równocześnie

Program Visual Studio obsługuje model wdrażania dla aplikacji klienckich systemu Windows oparty na koncepcji [izolowanych aplikacji](/windows/win32/SbsCs/isolated-applications) i [zestawów równoległych](/windows/win32/SbsCs/about-side-by-side-assemblies-). Domyślnie program Visual Studio kompiluje wszystkie natywne aplikacje C/C++ jako izolowane aplikacje, które używają [manifestów](/windows/win32/sbscs/manifests) do opisywania zależności od bibliotek Visual C++.

Kompilowanie programów C/C++ jako aplikacji izolowanych przedstawia szereg zalet. Na przykład aplikacja izolowana nie ma zastosowania, gdy inne aplikacje C/C++ instalują lub odinstalują Visual C++ biblioteki. Biblioteki Visual C++ używane przez aplikacje izolowane mogą być nadal dystrybuowane w folderze lokalnym aplikacji lub przez instalację do natywnej pamięci podręcznej zestawów (WinSxS); Obsługa bibliotek Visual C++ dla już wdrożonych aplikacji może być jednak uproszczona przy użyciu [pliku konfiguracji wydawcy](/windows/win32/SbsCs/publisher-configuration). Model wdrażania izolowanych aplikacji ułatwia zapewnienie, że aplikacje C/C++, które są uruchomione na określonym komputerze, używają najnowszej wersji bibliotek Visual C++ i nadal opuszczają możliwości administratorów systemu i autorów aplikacji w celu kontrolowania jawnych powiązań wersji aplikacji z ich zależnymi bibliotekami DLL.

W tej sekcji omówiono, jak można skompilować aplikację C/C++ jako izolowaną aplikację i upewnić się, że jest ona powiązana z bibliotekami Visual C++ przy użyciu manifestu. Informacje zawarte w tej sekcji dotyczą głównie natywnych lub niezarządzanych aplikacji C++. Aby uzyskać informacje na temat wdrażania natywnych aplikacji C++ skompilowanych przy użyciu programu Visual Studio, zobacz [Redystrybuowanie plików Visual C++](../windows/redistributing-visual-cpp-files.md).

## <a name="in-this-section"></a>W tej sekcji

[Pojęcia związane z aplikacjami izolowanymi oraz aplikacjami wykonywanymi równocześnie](concepts-of-isolated-applications-and-side-by-side-assemblies.md)

[Kompilowanie izolowanych kompilacji C/C++](building-c-cpp-isolated-applications.md)

[Kompilowanie wykonywanych jednocześnie aplikacji C/C++](building-c-cpp-side-by-side-assemblies.md)

[Porady: kompilowanie komponentów COM bez rejestrowania](how-to-build-registration-free-com-components.md)

[Porady: kompilowanie izolowanych aplikacji korzystających ze składników COM](how-to-build-isolated-applications-to-consume-com-components.md)

[Ogólne informacje o tworzeniu manifestu dla programów C/C++](understanding-manifest-generation-for-c-cpp-programs.md)

[Rozwiązywanie problemów związanych z aplikacjami izolowanymi C/C++ oraz aplikacjami wykonywanymi równocześnie](troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md)

## <a name="related-sections"></a>Sekcje pokrewne

[Aplikacje izolowane i zestawy równoległe](/windows/win32/SbsCs/isolated-applications-and-side-by-side-assemblies-portal)

[Wdrażanie aplikacji klasycznych](../windows/deploying-native-desktop-applications-visual-cpp.md)
