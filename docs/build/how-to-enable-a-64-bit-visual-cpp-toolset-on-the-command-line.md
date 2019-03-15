---
title: 'Instrukcje: Włączanie MSVC 64-bitowego zestawu narzędzi w wierszu polecenia'
ms.date: 03/29/2018
helpviewer_keywords:
- x64 [C++]
- 64-bit compiler [C++], command line usage
- 64-bit compiler [C++], toolset enabling at command line
- command line [C++], 64-bit compiler
- Itanium [C++], command-line compiler
- IPF
- Itanium [C++]
- IPF, command-line compiler
- x64 [C++], command-line compiler
ms.assetid: 4da93a19-e20d-4778-902a-5eee9a6a90b5
ms.openlocfilehash: b30b831522016ce61f138f7e0521c42ff44e04d9
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57809772"
---
# <a name="how-to-enable-a-64-bit-x64-hosted-msvc-toolset-on-the-command-line"></a>Instrukcje: Włączanie 64-bitowego, x64 hostowany zestaw narzędzi MSVC w wierszu polecenia

Program Visual Studio obejmuje kompilatory języków C++, wiązania i inne narzędzia, które służy do tworzenia wersji specyficzne dla platformy aplikacji, które można uruchomić w 32-bitowych, 64-bitowe lub oparte na ARM systemów operacyjnych Windows. Inne opcjonalne obciążenia programu Visual Studio pozwalają na innych platformach, takich jak iOS, Android i Linux przy użyciu narzędzi języka C++. Architektura kompilacji domyślne korzysta z 32-bitowe, obsługiwane x86 narzędzi do kompilowania kodu Windows 32-bitowy, macierzysty x86. Jednak prawdopodobnie masz komputer 64-bitowych. Korzystać z zalet procesora i pamięci miejsce dostępne dla kodu 64-bitowego, przy użyciu zestawu narzędzi 64-bitowe, obsługiwane x64 podczas kompilowania kodu x86, x64 lub procesorów ARM.

> [!NOTE]
> Aby uzyskać informacje o określonych narzędziach, które są dołączone do każdej wersji programu Visual Studio, zobacz [Visual C++ Tools i funkcje w wersji programu Visual Studio](../ide/visual-cpp-tools-and-features-in-visual-studio-editions.md).
>
> Aby uzyskać informacje o tym, jak używać programu Visual Studio IDE do tworzenia aplikacji 64-bitowych, zobacz [jak: Konfigurowanie projektów Visual C++ pod kątem 64-bitowy, x64 platform](how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md).

Po zainstalowaniu obciążenia języka C++ w Instalatorze programu Visual Studio zawsze powoduje zainstalowanie 32-bitowe, obsługiwane x86, natywnej i cross kompilator narzędzia do kompilowania kodu x86 i x64. Jeśli dodasz obciążenia Universal Windows Platform, instaluje też hostowanych x86 kompilatorem krzyżowym narzędzia do kompilowania kodu ARM. Jeśli musisz zainstalować te obciążenia na systemem x64 64-bitowy procesor, możesz również uzyskać natywne 64-bitowe i wieloplatformowych narzędzi kompilatora się x86 x 64, ARM kodu. 32-bitowych i 64-bitowego narzędzia generują identyczny kod, ale narzędzia 64-bitowe obsługują więcej pamięci dla symboli nagłówków prekompilowanych i optymalizacji całego programu ([/GL](reference/gl-whole-program-optimization.md) i [opcję/LTCG](reference/ltcg-link-time-code-generation.md)) opcji. Jeśli napotkasz limity pamięci podczas korzystania z narzędzi 32-bitowych, spróbuj narzędzi 64-bitowych.

## <a name="use-a-64-bit-hosted-developer-command-prompt-shortcut"></a>Użyj skrót do wiersza polecenia dewelopera hostowanej 64-bitowych

Po zainstalowaniu programu Visual Studio na 64-bitowym systemie operacyjnym Windows dostępne są skróty wiersza polecenia dewelopera dodatkowe natywnych 64-bitowe, obsługiwane x64 i kompilatorów skrośnych. Dostęp do tych wierszy poleceń w systemie Windows 10 w **Start** menu, otwórz folder dla używanej wersji programu Visual Studio, na przykład **programu Visual Studio 2017**, a następnie wybierz jedno z x64 natywnej lub cross-tool Wiersz polecenia dla deweloperów. Dostęp do tych wierszy poleceń w systemie Windows 8 w **Start** otwartym ekranem **wszystkie aplikacje**. Pod nagłówkiem dla zainstalowanej wersji programu Visual Studio, otwórz **programu Visual Studio** folder (w starszych wersjach programu Visual Studio może nosić **Visual Studio Tools**). We wcześniejszych wersjach systemu Windows, wybierz **Start**, rozwiń węzeł **wszystkie programy**, folder dla używanej wersji programu **programu Visual Studio** (i starszych wersji programu Visual Studio  **Narzędzia programu Visual Studio**). Aby uzyskać więcej informacji, zobacz [skróty wiersza polecenia dla deweloperów](building-on-the-command-line.md#developer_command_prompt_shortcuts).

## <a name="use-vcvarsallbat-to-set-a-64-bit-hosted-build-architecture"></a>Vcvarsall.bat umożliwia ustawianie architekturę 64-bitowych hostowanej kompilacji

Plik wszystkie macierzyste lub cross kompilator narzędzia, konfiguracje kompilacji mogą być używane w wierszu polecenia, uruchamiając vcvarsall.bat poleceń. Ten plik polecenia konfiguruje ścieżki i zmiennych środowiskowych, które umożliwiają określonego tworzenie architektury w istniejącym oknie wiersza polecenia. Aby uzyskać szczegółowe instrukcje, zobacz [lokalizacji plików poleceń dewelopera](building-on-the-command-line.md#developer_command_file_locations).

## <a name="see-also"></a>Zobacz także

[Konfigurowanie projektów w języku C++ x64 64-bitowy, obiektów docelowych](configuring-programs-for-64-bit-visual-cpp.md)<br/>
