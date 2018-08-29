---
title: Obsługiwane platformy (Visual C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Visual C++, platforms supported
- platforms [C++]
ms.assetid: 0d893056-4008-411a-b3d1-5f57fd7da95c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 521e08b22abb40b6e1b1fedce2375a6e33cc7e73
ms.sourcegitcommit: f7703076b850c717c33d72fb0755fbb2215c5ddc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2018
ms.locfileid: "43130787"
---
# <a name="supported-platforms-visual-c"></a>Obsługiwane platformy (Visual C++)

Aplikacje utworzone przy użyciu programu Visual Studio mogą być kierowane do różnych platform, w następujący sposób.

|System operacyjny|x86|X64|ARM|
|----------------------|---------|---------|---------|
|Windows XP|X *|X *||
|Windows Server 2003|X *|X *||
|Windows Vista|X|X||
|Windows Server 2008|X|X||
|Windows 7|X|X||
|Windows Server 2012 z dodatkiem R2|X|X||
|Windows 8|X|X|X|
|Windows 8.1|X|X|X|
|Windows 10|X|X|X|
|Android **|X|X|X|
|iOS **|X|X|X|
|Linux ***|X|X|X|

\* Możesz użyć zestawu narzędzi platformy Windows XP, które zostały zawarte w Visual Studio 2017, Visual Studio 2015, Visual Studio 2013 i Visual Studio 2012 Update 1 lub nowszej, aby kompilować projekty Windows XP i Windows Server 2003. Aby uzyskać informacje na temat korzystania z tego zestawu narzędzi platformy, zobacz [Konfigurowanie programów systemu Windows XP](build/configuring-programs-for-windows-xp.md). Aby uzyskać dodatkowe informacje na temat Zmiana zestawu narzędzi platformy, zobacz [porady: modyfikowanie platformy docelowej i zestawu narzędzi platformy](build/how-to-modify-the-target-framework-and-platform-toolset.md).

\*\* Możesz zainstalować **opracowywania aplikacji mobilnych w języku C++** obciążeniem w Instalatorze programu Visual Studio 2017 (lub opcjonalnego **Visual C++ for Cross Platform Mobile Development** składnika w Instalatorze programu Visual Studio 2015) do docelowej platformy iOS lub Android. Aby uzyskać instrukcje, zobacz [zainstalować Visual C++ for Cross-Platform Mobile Development](/visualstudio/cross-platform/install-visual-cpp-for-cross-platform-mobile-development). Aby utworzyć kod dla systemu iOS, konieczne jest posiadanie komputera Mac oraz on spełniać inne wymagania. Aby uzyskać listę wymagań wstępnych i instrukcje dotyczące instalacji, zobacz [Instalowanie i Konfigurowanie narzędzi do kompilacji przy użyciu systemu iOS](/visualstudio/cross-platform/install-and-configure-tools-to-build-using-ios). Możesz tworzyć x86 lub kodu ARM, aby dopasować sprzętu docelowego. Użyj x86 konfiguracje do skompilowania symulatora systemu iOS, programu Microsoft Visual Studio Emulator for Android i niektóre urządzenia z systemem Android. Użyj konfiguracji ARM, aby tworzyć dla urządzeń z systemem iOS i większość urządzeń z systemem Android.

\*\*\* Możesz zainstalować **programowanie dla systemu Linux przy użyciu języka C++** obciążeniem w Instalatorze programu Visual Studio 2017 do platform firmy Microsoft w systemie Linux. Aby uzyskać instrukcje, zobacz [pobieranie, instalowanie i konfigurowanie obciążenia Linux](linux/download-install-and-setup-the-linux-development-workload.md). Ten zestaw narzędzi kompiluje plik wykonywalny na komputerze docelowym, dzięki czemu można tworzyć dla dowolnej obsługiwanej architektury.

Aby uzyskać informacje o tym, jak ustawić konfigurację platformy docelowej, zobacz [jak: Konfigurowanie projektów Visual C++ do docelowego 64-bitowej, x64 platform](build/how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md).

## <a name="see-also"></a>Zobacz także

- [Narzędzia i funkcje programu Visual C++ w wydaniach programu Visual Studio](ide/visual-cpp-tools-and-features-in-visual-studio-editions.md)
- [Wprowadzenie](/visualstudio/ide/getting-started-with-visual-cpp-in-visual-studio)