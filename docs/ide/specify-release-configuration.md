---
title: Nowy projekt z istniejącego kodu wersji konfiguracji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.appwiz.importwiz.releasesettings
dev_langs:
- C++
ms.assetid: 3e2fc73c-bdbd-4790-b2bd-d31731f0cece
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c4e7d5fb707c455aa7b7fb9f0e14dff95ee5633f
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45703365"
---
# <a name="specify-release-configuration-settings-create-new-project-from-existing-code-files-wizard"></a>Określ ustawienia konfiguracji wydania, Kreator Utwórz nowy projekt z istniejących plików z kodem
Aby określić ustawienia projektu dla konfiguracji wydania, należy użyć tej strony kreator Utwórz nowy projekt z istniejących plików kodu.  
  
## <a name="task-list"></a>Lista zadań  
 [Instrukcje: tworzenie projektu C++ z istniejącego kodu](../ide/how-to-create-a-cpp-project-from-existing-code.md)  
  
## <a name="uielement-list"></a>Lista elementów UI  
- **Takie same, jak konfiguracja debugowania**

   Określa, że kreator wygeneruje ustawienia konfiguracji wydania projektu identyczne do ustawienia projektu dla konfiguracji debugowania. Ta opcja jest zaznaczona domyślnie. Wszystkie inne opcje na tej stronie są nieaktywne, chyba że zaznaczenie tego pola wyboru.  
  
- **Wiersz polecenia kompilacji**

   Określa wiersz polecenia, który tworzy nowy projekt. Wprowadź nazwę kompilator oraz wszelkich przełączników lub argumentów, które chcesz użyć do utworzenia nowego projektu. Ta opcja jest włączona po **Użyj zewnętrznego systemu kompilacji** jest zaznaczona opcja **Określ ustawienia projektu** strony.  
  
- **Ponownie skompiluj wiersza polecenia**

   Określa wiersz polecenia, która odtwarza nowy projekt. Ta opcja jest włączona po **Użyj zewnętrznego systemu kompilacji** jest zaznaczona opcja **Określ ustawienia projektu** strony.  
  
- **Wiersz poleceń oczyszczenia**

   Określa wiersz polecenia, aby usunąć pliki obsługi, generowane przez narzędzia do kompilacji dla nowego projektu. Ta opcja jest włączona po **Użyj zewnętrznego systemu kompilacji** jest zaznaczona opcja **Określ ustawienia projektu** strony.  
  
- **Dane wyjściowe (na potrzeby debugowania)**

   Określa ścieżkę katalogu plików wyjściowych dla konfiguracji debugowania w nowym projekcie. Ta opcja jest włączona po **Użyj zewnętrznego systemu kompilacji** jest zaznaczona opcja **Określ ustawienia projektu** strony.  
  
- **Definicje preprocesora (/ D)**

   Definiuje symbole preprocesora dla nowego projektu. Aby uzyskać więcej informacji, zobacz [/D (definicje preprocesora)](../build/reference/d-preprocessor-definitions.md).  
  
- **Ścieżka wyszukiwania plików dołączanych (/ I)**

   Określa ścieżki katalogów do dodania do listy katalogów, które kompilator będzie przeszukiwał, aby rozwiązać odwołania do plików przekazywane do dyrektywy preprocesora w nowym projekcie. Aby uzyskać więcej informacji, zobacz [/I (dodatkowe katalogi dołączenia)](../build/reference/i-additional-include-directories.md).  
  
- **Wymuszone załączone pliki (/FI)**

   Określa pliki nagłówkowe przetwarzania podczas tworzenia nowego projektu. Aby uzyskać więcej informacji, zobacz [/FI (nazwij wymuszone obejmują plik)](../build/reference/fi-name-forced-include-file.md).  
  
- **Ścieżka wyszukiwania zestawu .NET (/ AI)**

   Określa ścieżki katalogu, które kompilator będzie przeszukiwał, aby rozwiązać odwołania do zestawów .NET przekazana do dyrektywy preprocesora w nowym projekcie. Aby uzyskać więcej informacji, zobacz [/AI (Określ katalogi metadanych)](../build/reference/ai-specify-metadata-directories.md).  
  
- **Wymuszone użycie zestawów .NET (/ FU)**

   Określa zestawy .NET do przetwarzania podczas tworzenia nowego projektu. Aby uzyskać więcej informacji, zobacz [/FU (nazwij wymuszone #using)](../build/reference/fu-name-forced-hash-using-file.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Określanie ustawień projektu, Kreator Utwórz nowy projekt z istniejących plików z kodem](../ide/specify-project-settings-create-new-project-from-existing-code-files-wizard.md)