---
title: 'Porady: Włączanie 64-bitowych Visual C++ narzędzi wiersza polecenia | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 03/29/2018
ms.technology:
- cpp-tools
ms.topic: article
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5b8c01feca58ecb900a3760b88bac230fcc82f9a
ms.sourcegitcommit: 78e5e5cdbafd29e2a6ccf68d4cce215136952907
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/03/2018
---
# <a name="how-to-enable-a-64-bit-x64-hosted-visual-c-toolset-on-the-command-line"></a>Porady: Włączanie 64-bitowego, x64 hostowany zestaw narzędzi Visual C++ w wierszu polecenia

Visual C++ obejmuje kompilatory, linkery i innych narzędzi, które umożliwia tworzenie aplikacji uruchamianych w systemach operacyjnych Windows 32-bitowych, 64-bitowe lub oparte na usłudze ARM wersji specyficzne dla platformy. Inne opcjonalne obciążenia programu Visual Studio umożliwiają używanie narzędzia C++ pod kątem innych platform, na przykład iOS, Android i Linux. Architektura kompilacji domyślne korzysta 32-bitowy, hostowana x86 narzędzia w celu skompilowania 32-bitowy, x86 natywnego kodu systemu Windows. Jednak prawdopodobnie 64-bitowym komputerze. Możliwość korzystania z procesora i pamięci miejsca do kodu 64-bitowego przy użyciu zestawu narzędzi 64-bitowe, hostowana x64 podczas kompilowania kodu x86, x64 lub procesorów ARM.

> [!NOTE]
> Aby uzyskać informacje o określone narzędzia, które są dołączone do każdej wersji programu Visual C++, zobacz [narzędzia Visual C++ i funkcji w programie Visual Studio wersje](../ide/visual-cpp-tools-and-features-in-visual-studio-editions.md).
>
> Informacje o używaniu środowiska IDE programu Visual Studio do tworzenia aplikacji 64-bitowych, zobacz [jak: Konfigurowanie projekty Visual C++ do docelowego 64-bitowej, x64 platformy](../build/how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md).

Po zainstalowaniu obciążenia C++ w Instalatorze programu Visual Studio, zawsze powoduje zainstalowanie 32-bitowy, hostowana x86, natywne i Międzyplatformowe kompilatora narzędzia umożliwiające tworzenie x86 i x64 kodu. Jeśli obciążenie platformy uniwersalnej systemu Windows, instaluje również hostowanej x86 krzyżowego kompilatora narzędzia do kompilowania kodu ARM. Jeśli musisz zainstalować te obciążenia na systemem x64 64-bitowy, procesora, także uzyskać native 64-bitowe i między kompilatora narzędzia do tworzenia x86 x 64 i ARM kodu. 32-bitowe i 64-bitowe narzędzia generowania kodu identyczne, ale narzędzia 64-bitowy obsługę większej ilości pamięci prekompilowanego nagłówka, symbole i całej optymalizacji programu ([/GL](../build/reference/gl-whole-program-optimization.md) i [opcję/LTCG](../build/reference/ltcg-link-time-code-generation.md)) opcje. Jeśli napotkasz limity pamięci podczas korzystania z narzędzi 32-bitowy, spróbuj narzędzia 64-bitowy.

## <a name="use-a-64-bit-hosted-developer-command-prompt-shortcut"></a>Użyj skrótu wiersza polecenia dewelopera hostowanej 64-bitowych

Po zainstalowaniu programu Visual Studio na 64-bitowym systemie operacyjnym Windows, skrótów wiersza polecenia dewelopera dodatkowe dla 64-bitowych, hostowana x64 natywnego i Międzyplatformowe kompilatory są dostępne. Dostępu do tych wierszy poleceń w systemie Windows 10 na **Start** menu, otwórz folder dla używanej wersji programu Visual Studio, na przykład **programu Visual Studio 2017**, a następnie wybierz jedną z x64 lokalny lub cross narzędzie Wiersz polecenia dla deweloperów. Aby uzyskać dostęp do tych wierszy poleceń w systemie Windows 8 na **Start** ekranu, otwórz **wszystkie aplikacje**. Pod nagłówkiem dla zainstalowanej wersji programu Visual Studio Otwórz **programu Visual Studio** folder (w starszych wersjach programu Visual Studio może nosić **programu Visual Studio Tools**). We wcześniejszych wersjach systemu Windows, wybierz **Start**, rozwiń węzeł **wszystkie programy**, folder dla używanej wersji programu **programu Visual Studio** (i starszych wersji programu Visual Studio  **Narzędzia Visual Studio**). Aby uzyskać więcej informacji, zobacz [skrótów wiersza polecenia dewelopera](../build/building-on-the-command-line.md#developer-command-prompt-shortcuts).

## <a name="use-vcvarsallbat-to-set-a-64-bit-hosted-build-architecture"></a>Użyj Vcvarsall.bat, aby ustawić Architektura 64-bitowych hostowanej kompilacji

Plik żadnego natywnego lub granic można konfiguracje kompilacji w wierszu polecenia, uruchamiając vcvarsall.bat narzędzia kompilatora poleceń. Ten plik polecenia konfiguruje ścieżki i zmiennych środowiskowych, które umożliwiają określonego kompilacji architektury w istniejących okno wiersza polecenia. Aby uzyskać szczegółowe instrukcje, zobacz [pliki poleceń deweloperów i lokalizacje](../build/building-on-the-command-line.md#developer-command-files-and-locations).

## <a name="see-also"></a>Zobacz także

[Konfigurowanie Visual C++ dla wersji 64-bitowych, platformy docelowe x64](../build/configuring-programs-for-64-bit-visual-cpp.md)<br/>
