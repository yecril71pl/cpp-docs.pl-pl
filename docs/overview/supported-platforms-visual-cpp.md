---
title: Obsługiwane platformy (Visual C++)
ms.date: 12/02/2019
ms.technology: cpp-tools
helpviewer_keywords:
- Visual C++, platforms supported
- platforms [C++]
ms.assetid: 0d893056-4008-411a-b3d1-5f57fd7da95c
author: mikeblome
ms.author: mblome
ms.openlocfilehash: eb2a258a73e69ef032576f5b42e8071fd27439a1
ms.sourcegitcommit: 8762a3f9b5476b4dee03f0ee8064ea606550986e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2019
ms.locfileid: "74810601"
---
# <a name="supported-platforms-visual-c"></a>Obsługiwane platformy (Visual C++)

Aplikacje utworzone za pomocą programu Visual Studio mogą być przeznaczone dla różnych platform w następujący sposób.

|System operacyjny|x86|X64|ARM|ARM64\*\*\*\*|
|----------------------|---------|---------|---------|---------|
|Windows XP|X\*|X\*|||
|Windows Server 2003|X\*|X\*|||
|Windows Vista|X|X|||
|Windows Server 2008|X|X|||
|Windows 7|X|X|||
|Windows Server 2012 z dodatkiem R2|X|X|||
|Windows 8|X|X|X||
|Windows 8.1|X|X|X||
|Windows 10|X|X|X|X|
|\* \*systemu Android|X|X|X|X|
|\* \*systemu iOS|X|X|X|X|
|\*\*systemu Linux \*|X|X|X|X|

\* można użyć zestawu narzędzi platformy systemu Windows XP zawartego w programie Visual Studio 2017, Visual Studio 2015, Visual Studio 2013 i Visual Studio 2012 Update 1 w celu utworzenia projektów systemu Windows XP i Windows Server 2003. Aby uzyskać informacje na temat korzystania z tego zestawu narzędzi platformy, zobacz [Konfigurowanie programów dla systemu Windows XP](../build/configuring-programs-for-windows-xp.md). Aby uzyskać dodatkowe informacje na temat zmiany zestawu narzędzi platformy, zobacz [How to: Modify The Target Framework and platform zestaw narzędzi](../build/how-to-modify-the-target-framework-and-platform-toolset.md).

\*\* można zainstalować **Programowanie aplikacji mobilnych przy użyciu C++**  obciążenia w Instalatorze programu Visual Studio 2017 i nowszych. W Instalatorze programu Visual Studio 2015 wybierz opcjonalną **wizualizację C++ dla wieloplatformowego programu do tworzenia aplikacji mobilnych** , która będzie ukierunkowana na platformy z systemem iOS lub Android. Aby uzyskać instrukcje, zobacz [Instalowanie C++ wizualizacji na potrzeby tworzenia aplikacji mobilnych na wiele platform](/visualstudio/cross-platform/install-visual-cpp-for-cross-platform-mobile-development). Aby skompilować kod dla systemu iOS, musisz mieć komputer Mac i spełnić inne wymagania. Aby uzyskać listę wymagań wstępnych i instrukcji instalacji, zobacz [Instalowanie i Konfigurowanie narzędzi do kompilowania przy użyciu systemu iOS](/visualstudio/cross-platform/install-and-configure-tools-to-build-using-ios). Można skompilować kod x86 lub ARM w celu dopasowania go do sprzętu docelowego. Użyj konfiguracji x86, aby skompilować symulatory systemu iOS, Microsoft Visual Studio Emulator for Android i niektóre urządzenia z systemem Android. Użyj konfiguracji usługi ARM do kompilowania urządzeń z systemem iOS i większości urządzeń z systemem Android.

\*\*\* można zainstalować Programowanie dla systemu **Linux przy C++ użyciu** obciążenia w Instalatorze programu Visual Studio 2017 lub nowszego dla docelowych platform systemu Linux. Aby uzyskać instrukcje, zobacz [pobieranie, Instalowanie i Konfigurowanie obciążenia systemu Linux](../linux/download-install-and-setup-the-linux-development-workload.md). Ten zestaw narzędzi kompiluje plik wykonywalny na komputerze docelowym, aby można było utworzyć dowolną obsługiwaną architekturę.

\*\*\*\* ARM64 jest dostępna w programie Visual Studio 2017 i nowszych.

Aby uzyskać informacje na temat sposobu ustawiania konfiguracji platformy docelowej, zobacz [How to: Configure Visual C++ projects to target 64-bit i x64 platform](../build/how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md).

## <a name="see-also"></a>Zobacz także

- [Narzędzia i funkcje programu Visual C++ w wydaniach programu Visual Studio](visual-cpp-tools-and-features-in-visual-studio-editions.md)
- [Wprowadzenie](/visualstudio/ide/getting-started-with-cpp-in-visual-studio)
