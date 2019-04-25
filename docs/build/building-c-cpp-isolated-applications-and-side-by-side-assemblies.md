---
title: Kompilowanie aplikacji izolowanych C/C++ oraz aplikacji wykonywanych równocześnie
ms.date: 11/04/2016
helpviewer_keywords:
- isolated applications [C++]
- WinSxS [C++]
- native assembly cache [C++]
- builds [C++], isolated applications
- side-by-side applications [C++]
- builds [C++], side-by-side assemblies
ms.assetid: 9465904e-76f7-48bd-bb3f-c55d8f1699b6
ms.openlocfilehash: b962796c3bf32bc312d3047535ae90a40a37094d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62196693"
---
# <a name="building-cc-isolated-applications-and-side-by-side-assemblies"></a>Kompilowanie aplikacji izolowanych C/C++ oraz aplikacji wykonywanych równocześnie

Visual C++ obsługuje model wdrażania dla aplikacji klienckich Windows oparte na pomysł [izolowanych](/windows/desktop/SbsCs/isolated-applications) i [zestawów side-by-side](/windows/desktop/SbsCs/about-side-by-side-assemblies-). Domyślnie program Visual C++ kompiluje wszystkich natywnych aplikacji C/C++ izolowana aplikacje, które używają [manifesty](/windows/desktop/sbscs/manifests) do opisania ich zależności bibliotek Visual C++.

Kompilowanie programów C/C++, które aplikacje izolowane przedstawia szereg korzyści. Na przykład aplikacji izolowanej jest nienaruszona, gdy innych aplikacji C/C++, instalowanie i odinstalowywanie bibliotek języka Visual C++. Biblioteki Visual C++, używane przez aplikacje izolowane nadal może być rozpowszechniany w lokalnym folderze w aplikacji lub za pomocą instalacji do pamięci podręcznej zestawu macierzystego (folderze WinSxS); jednak obsługa bibliotek języka Visual C++ dla już wdrożonej aplikacji można uprościć za pomocą [plik konfiguracyjny wydawcy](/windows/desktop/SbsCs/publisher-configuration). Model wdrażania aplikacji izolowanej ułatwia zapewnienie, że aplikacji C/C++, które są uruchomione na określonym komputerze używać najnowszą wersję bibliotek języka Visual C++, pozostawiając nadal otwarte możliwości dla administratorów systemów i autorzy aplikacji do sterowania wiązanie jawne wersji aplikacji w celu ich zależne biblioteki dll.

W tej sekcji omówiono sposób tworzenia aplikacji izolowanych aplikacji C/C++ i upewnij się, że wiąże bibliotek języka Visual C++ przy użyciu manifestu. Informacje przedstawione w tej sekcji dotyczą przede wszystkim natywnej lub niezarządzanych aplikacji Visual C++. Aby dowiedzieć się, jak wdrażanie natywnych aplikacji skompilowanej za pomocą języka Visual C++, zobacz [Redistributing Visual C++ Files](../windows/redistributing-visual-cpp-files.md).

## <a name="in-this-section"></a>W tej sekcji

[Pojęcia związane z aplikacjami izolowanymi oraz aplikacjami wykonywanymi równocześnie](concepts-of-isolated-applications-and-side-by-side-assemblies.md)

[Kompilowanie izolowanych aplikacji C/C++](building-c-cpp-isolated-applications.md)

[Kompilowanie wykonywanych jednocześnie aplikacji C/C++](building-c-cpp-side-by-side-assemblies.md)

[Instrukcje: kompilowanie komponentów COM bez rejestrowania](how-to-build-registration-free-com-components.md)

[Instrukcje: kompilowanie izolowanych aplikacji korzystających ze składników COM](how-to-build-isolated-applications-to-consume-com-components.md)

[Ogólne informacje o tworzeniu manifestu dla programów C/C++](understanding-manifest-generation-for-c-cpp-programs.md)

[Rozwiązywanie problemów związanych z aplikacjami izolowanymi C/C++ oraz aplikacjami wykonywanymi równocześnie](troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md)

## <a name="related-sections"></a>Sekcje pokrewne

[Aplikacje izolowane i zestawy Side-by-side](/windows/desktop/SbsCs/isolated-applications-and-side-by-side-assemblies-portal)

[Wdrażanie aplikacji komputerowych](../windows/deploying-native-desktop-applications-visual-cpp.md)