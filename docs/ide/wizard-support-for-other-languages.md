---
title: Obsługa kreatora dla innych języków | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.appwiz.EastAsianLanguages
dev_langs:
- C++
helpviewer_keywords:
- wizards [C++], language support
- language support for MFC projects
- projects [C++], language support
ms.assetid: b653c673-0687-455c-885f-15d7e2f4149d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c33858e02fd8bad03e03a963e940f215d528157d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46395144"
---
# <a name="wizard-support-for-other-languages"></a>Obsługa kreatora dla innych języków

Podczas instalowania programu Visual Studio aplikacji Instalator wykrywa ustawień regionalnych, wymienione w systemie i instaluje odpowiedni język szablonu lub szablonów dla ustawień regionalnych. Na przykład dla ustawień regionalnych Europejskiego Western, Instalator instaluje, angielskim, francuskim, włoskim, hiszpańskim i niemieckim. Te języki są wyświetlane w **język zasobów** listy na [typ aplikacji](../mfc/reference/application-type-mfc-application-wizard.md) strony Kreatora aplikacji MFC.

## <a name="language-templates"></a>Szablony języka

Nie wszystkie szablony są zainstalowane we wszystkich systemach, ponieważ szablony są oparte kodowania ANSI, a nie wszystkie zasoby mogą być edytowane we wszystkich systemach. Na przykład domyślnie nie można edytować japoński zasobów w systemie francuskim.

Jeśli używasz Windows 2000 lub nowszym i chcesz utworzyć aplikację MFC w innym języku, następnie należy skopiować katalog szablonu dla odpowiedniego języka z nośnika Instalatora programu Visual Studio (dysk 1) do systemu.

> [!NOTE]
>  Aby edytować utworzony projekt, należy ustawić ustawienia regionalne systemu odpowiednich ustawień regionalnych dla wybranego języka.

Szablony są przypisane każdy folder w katalogu \Microsoft Visual Studio .NET 2003\Vc7\VCWizards\mfcappwiz\templates\ zgodnie z opisem w poniższej tabeli. Dostępu do żądanego języka szablonu, skopiuj odpowiedni folder w katalogu \mfcappwiz\templates\ na tym komputerze. Po skopiowaniu folder języka pojawi się w **język zasobów** listy na **typ aplikacji** strony Kreatora aplikacji MFC.

### <a name="language-templates-provided-in-visual-studio-net"></a>Szablony języka podany w programie Visual Studio .NET

|Język|Szablon|
|--------------|--------------|
|Chiński (tradycyjny)|1028|
|Chiński uproszczony|2052|
|Angielski|1033|
|Francuski|1036|
|niemiecki|1031|
|Włoski|1040|
|japoński|1041|
|koreański|1042|
|Hiszpański|3082|

## <a name="format-of-visual-c-wizard-generated-files"></a>Format Visual pliki generowane przez kreatora C++

Kreatorów Visual C++ wygeneruje projektów w formacie Unicode, gdy wersja zainstalowanego języka programu Visual Studio jest niezgodna z ustawień regionalnych systemu. Na przykład japońska wersja językowa programu Visual Studio jest zainstalowany na komputerze, na którym zainstalowano ustawienia regionalne ustawione do wszystkich języków innych niż japońska, kreatorów Visual C++ wygeneruje projektów obejmuje pliki Unicode. To jest typowe w przypadku maszyn z pakietów (MUI) wielojęzycznych Windows.

To zachowanie różni się od systemów, skonfigurować w taki sposób, że ustawienia regionalne systemu jest taka sama jak wersja językowa programu Visual Studio. W takim przypadku pliki projektu zostanie utworzony w formacie ANSI w stronie kodowej systemu.

## <a name="see-also"></a>Zobacz też

[Typy plików utworzonych dla projektów Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)<br>
[Tworzenie i zarządzanie projektami Visual C++](../ide/creating-and-managing-visual-cpp-projects.md)