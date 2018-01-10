---
title: "Obsługa kreatora dla innych języków | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.appwiz.EastAsianLanguages
dev_langs: C++
helpviewer_keywords:
- wizards [C++], language support
- language support for MFC projects
- projects [C++], language support
ms.assetid: b653c673-0687-455c-885f-15d7e2f4149d
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8ef95c252621aa7f725098dfcd08c7b5b3620826
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="wizard-support-for-other-languages"></a>Obsługa kreatora dla innych języków
Po zainstalowaniu programu Visual Studio aplikacji Instalator wykrywa ustawień regionalnych systemu na liście i instaluje odpowiedni język szablonu lub szablonów dla ustawień regionalnych. Na przykład Western Europejskiego ustawień regionalnych, Instalator instaluje angielskim, francuskim, włoskim, hiszpańskim i niemieckim. Te języki są wyświetlane w **języka zasobu** listy na [typu aplikacji](../mfc/reference/application-type-mfc-application-wizard.md) Kreatora aplikacji MFC.  
  
## <a name="language-templates"></a>Szablony języka  
 Nie wszystkie szablony są zainstalowane we wszystkich systemach, ponieważ szablony są kodowania ANSI na podstawie, a nie wszystkie zasoby mogą być edytowane we wszystkich systemach. Na przykład domyślnie nie można edytować japońskiego zasobów w systemie francuskim.  
  
 Jeśli używasz systemu Windows 2000 lub nowszym i chcesz utworzyć aplikacji MFC w innym języku, następnie należy skopiować katalogu szablonów dla odpowiedniego języka z nośnika Instalatora programu Visual Studio (dysk 1) do systemu.  
  
> [!NOTE]
>  Aby edytować utworzony projekt, musisz ustawić ustawienia regionalne systemu na odpowiednie ustawienia regionalne dla wybranego języka.  
  
 Szablony są przypisane każdego folderu w katalogu \Microsoft Visual Studio .NET 2003\Vc7\VCWizards\mfcappwiz\templates\ wymienionych w poniższej tabeli. Dostępu do żądanego języka szablonu, skopiuj odpowiedni folder w katalogu \mfcappwiz\templates\ na komputerze. Po skopiowaniu folder języka będą wyświetlane w **języka zasobu** listy na **typu aplikacji** Kreatora aplikacji MFC.  
  
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
 Kreatorów Visual C++ wygeneruje projekty w formacie Unicode, gdy wersja językowa zainstalowanego programu Visual Studio jest niezgodny z ustawień regionalnych systemu. Na przykład japońska wersja językowa programu Visual Studio jest zainstalowany na komputerze, który ma ustawioną w dowolnym języku innym niż język japoński ustawienia regionalne, kreatorów Visual C++ wygeneruje projektów złożoną z plików Unicode. To jest typowe na maszynach z pakietów (MUI) wielu języków systemu Windows.  
  
 To zachowanie różni się od systemów skonfigurować w taki sposób, że ustawienia regionalne systemu jest taka sama jak wersja językowa programu Visual Studio. W takim przypadku pliki projektu zostaną utworzone w ANSI w stronie kodowej systemu.  
  
## <a name="see-also"></a>Zobacz też  
 [Typy plików utworzonych dla projektów Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)   
 [Tworzenie i zarządzanie projektami Visual C++](../ide/creating-and-managing-visual-cpp-projects.md)