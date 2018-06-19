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
ms.openlocfilehash: b0d857a65e0a08b105d54ba574553ab4a74fd3f9
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33858375"
---
# <a name="supported-platforms-visual-c"></a>Obsługiwane platformy (Visual C++)

Aplikacje przy użyciu [!INCLUDE[vsprvs](assembler/masm/includes/vsprvs_md.md)] można zastosować do różnych platform, w następujący sposób.

|System operacyjny|x86|X64|ARM|
|----------------------|---------|---------|---------|
|Windows XP|X *|X *||
|[!INCLUDE[WinXPSvr](build/includes/winxpsvr_md.md)]|X *|X *||
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

\* Korzystając z zestawu narzędzi platformy systemu Windows XP, które zostały uwzględnione w Visual Studio 2017, Visual Studio 2015, Visual Studio 2013 i Visual Studio 2012 Update 1 lub nowszej, aby kompilacji systemu Windows XP i [!INCLUDE[WinXPSvr](build/includes/winxpsvr_md.md)] projektów. Aby uzyskać informacje dotyczące sposobu używania tego zestawu narzędzi platformy, zobacz [Konfigurowanie programów dla systemu Windows XP](build/configuring-programs-for-windows-xp.md). Aby uzyskać dodatkowe informacje na temat zmieniania zestaw narzędzi platformy, zobacz [porady: modyfikowanie platformy docelowej i zestawu narzędzi platformy](build/how-to-modify-the-target-framework-and-platform-toolset.md).

\*\* Można zainstalować **Mobile development z C++** obciążenia w Instalatorze programu Visual Studio (lub opcjonalnego **Visual C++ for Cross Platform Mobile Development** składnika w Instalatorze programu Visual Studio 2015) do docelowy z systemem iOS lub Android platform. Aby uzyskać instrukcje, zobacz [zainstalować Visual C++ for Cross Platform Mobile Development](/visualstudio/cross-platform/install-visual-cpp-for-cross-platform-mobile-development). Do tworzenia kodu dla systemu iOS, należy na komputerze Mac i innych wymagań. Aby uzyskać listę wymagań wstępnych i instrukcje dotyczące instalacji, zobacz [Instalowanie i Konfigurowanie narzędzi do kompilacji przy użyciu systemu iOS](/visualstudio/cross-platform/install-and-configure-tools-to-build-using-ios). Można tworzyć x86 lub kodu ARM do dopasowania sprzętu docelowej. Użyj x86 konfiguracji kompilacji na symulatorze systemu iOS, Microsoft Visual Studio Emulator for Android i niektórych urządzeń z systemem Android. Konfiguracje ARM umożliwia tworzenie dla urządzeń z systemem iOS i większość urządzeń z systemem Android.

\*\*\* Można zainstalować **Linux Programowanie w języku C++** obciążenia w Instalatorze programu Visual Studio do docelowej platformy Linux. Aby uzyskać instrukcje, zobacz [pobrać, zainstalować i skonfigurować obciążenie systemu Linux](linux/download-install-and-setup-the-linux-development-workload.md). Ten zestaw narzędzi kompiluje pliku wykonywalnego na komputerze docelowym, można je tworzyć dla dowolnej obsługiwanej architektury.

Uzyskać informacji o sposobie konfiguracji platformy docelowej, zobacz [porady: Konfigurowanie projekty Visual C++ do docelowego 64-bitowej, x64 platform](build/how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md).

## <a name="see-also"></a>Zobacz także

- [Narzędzia i funkcje programu Visual C++ w wydaniach programu Visual Studio](ide/visual-cpp-tools-and-features-in-visual-studio-editions.md)
- [Wprowadzenie](/visualstudio/ide/getting-started-with-visual-cpp-in-visual-studio)