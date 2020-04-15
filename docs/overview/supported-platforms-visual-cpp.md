---
title: Obsługiwane platformy (Visual C++)
ms.date: 12/02/2019
ms.technology: cpp-tools
helpviewer_keywords:
- Visual C++, platforms supported
- platforms [C++]
ms.assetid: 0d893056-4008-411a-b3d1-5f57fd7da95c
ms.openlocfilehash: 049b28d23c7f5f5f023f3b2964577b75992c2998
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "75793833"
---
# <a name="supported-platforms-visual-c"></a>Obsługiwane platformy (Visual C++)

Aplikacje utworzone przy użyciu programu Visual Studio mogą być kierowane do różnych platform, w następujący sposób.

|System operacyjny|x86|x64|ARM|ARM64 ( ARM64 )\*\*\*\*|
|----------------------|---------|---------|---------|---------|
|Windows XP|X\*|X\*|||
|Windows Server 2003|X\*|X\*|||
|Windows Vista|X|X|||
|Windows Server 2008|X|X|||
|Windows 7|X|X|||
|Windows Server 2012 R2|X|X|||
|Windows 8|X|X|X||
|Windows 8.1|X|X|X||
|Windows 10|X|X|X|X|
|Android\*\*|X|X|X|X|
|Ios\*\*|X|X|X|X|
|Linux\*\*\*|X|X|X|X|

\*Do tworzenia projektów systemów Windows XP i Windows Server 2003 można użyć zestawu narzędzi platformy systemu Windows XP dołączonych do programu Visual Studio 2017, Visual Studio 2015, Visual Studio 2013 i Visual Studio 2012 Update 1. Aby uzyskać informacje na temat korzystania z tego zestawu narzędzi platformy, zobacz [Konfigurowanie programów dla systemu Windows XP](../build/configuring-programs-for-windows-xp.md). Aby uzyskać dodatkowe informacje na temat zmiany zestawu narzędzi platformy, zobacz [Jak: Zmodyfikować platformę docelową i platformę Toolset](../build/how-to-modify-the-target-framework-and-platform-toolset.md).

\*\*Program mobile development z obciążeniem **języka C++** można zainstalować w instalatorze programu Visual Studio 2017 i nowszych. W konfiguracji programu Visual Studio 2015 wybierz opcjonalny składnik **Visual C++ for Cross Platform Mobile Development,** który będzie przeznaczony dla platform systemu iOS lub Android. Aby uzyskać instrukcje, zobacz [Instalowanie języka Visual C++ for Cross-Platform Mobile Development](/visualstudio/cross-platform/install-visual-cpp-for-cross-platform-mobile-development). Aby utworzyć kod systemu iOS, musisz mieć komputer Mac i spełniać inne wymagania. Aby uzyskać listę wymagań wstępnych i instrukcje instalacji, zobacz [Instalowanie i konfigurowanie narzędzi do tworzenia przy użyciu systemu iOS](/visualstudio/cross-platform/install-and-configure-tools-to-build-using-ios). Można utworzyć kod x86 lub ARM, aby dopasować go do docelowego sprzętu. Użyj konfiguracji x86 do tworzenia dla symulatora systemu iOS, emulatora programu Microsoft Visual Studio dla systemu Android i niektórych urządzeń z systemem Android. Użyj konfiguracji ARM do tworzenia dla urządzeń z systemem iOS i większości urządzeń z systemem Android.

\*\*\*Programistyczne systemu Linux można zainstalować z obciążeniem **języka C++** w instalatorze programu Visual Studio 2017 i nowszych, aby kierować na platformy systemu Linux. Aby uzyskać instrukcje, zobacz [Pobieranie, instalowanie i konfigurowanie obciążenia systemu Linux](../linux/download-install-and-setup-the-linux-development-workload.md). Ten zestaw narzędzi kompiluje plik wykonywalny na komputerze docelowym, dzięki czemu można tworzyć dla dowolnej obsługiwanej architektury.

\*\*\*\*Obsługa arm64 jest dostępna w programie Visual Studio 2017 i nowszych.

Aby uzyskać informacje dotyczące ustawiania konfiguracji platformy docelowej, zobacz [Jak: Konfigurowanie projektów visual c++ do 64-bitowych platform x64](../build/how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md).

## <a name="see-also"></a>Zobacz też

- [Narzędzia i funkcje programu Visual C++ w wydaniach programu Visual Studio](visual-cpp-tools-and-features-in-visual-studio-editions.md)
- [Wprowadzenie](/visualstudio/ide/getting-started-with-cpp-in-visual-studio)
