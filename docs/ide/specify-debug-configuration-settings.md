---
title: Nowy projekt z istniejących źródeł debugowania ustawienie (Visual C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.appwiz.importwiz.debugsettings
dev_langs:
- C++
ms.assetid: 607339a8-9d33-458b-8095-dc73f374e29d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b40bafe817ebf1dd25cc40115635b895502e0df8
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "33335045"
---
# <a name="specify-debug-configuration-settings-create-new-project-from-existing-code-files-wizard"></a>Określ ustawienia konfiguracji debugowania, Kreator Utwórz nowy projekt z istniejących plików z kodem
Ta strona kreatora Utwórz nowy projekt z istniejących plików kodu do określania ustawień projektu konfiguracji debugowania.  
  
## <a name="task-list"></a>Lista zadań  
 [Instrukcje: tworzenie projektu C++ z istniejącego kodu](../ide/how-to-create-a-cpp-project-from-existing-code.md)  
  
## <a name="uielement-list"></a>Lista elementów UI  
 **Wiersz polecenia kompilacji**  
 Określa wiersz polecenia, która tworzy nowy projekt. Na przykład, wprowadź nazwę kompilator (oraz wszystkie przełączniki i argumenty) lub skrypty kompilacji chcesz wykorzystać do tworzenia nowego projektu. Ta opcja jest włączona po **Użyj zewnętrznego systemu kompilacji** jest zaznaczona opcja **Określ ustawienia projektu** strony; w przeciwnym razie jest ona niedostępna.  
  
 **Odbuduj wiersza polecenia**  
 Określa wiersz polecenia, który odtwarza nowy projekt. Ta opcja jest włączona po **Użyj zewnętrznego systemu kompilacji** jest zaznaczona opcja **Określ ustawienia projektu** strony; w przeciwnym razie jest ona niedostępna.  
  
 **Wiersz poleceń oczyszczenia**  
 Określa wiersz polecenia, aby usunąć pliki obsługi wygenerowane za pomocą narzędzi kompilacji dla nowego projektu. Ta opcja jest włączona po **Użyj zewnętrznego systemu kompilacji** jest zaznaczona opcja **Określ ustawienia projektu** strony; w przeciwnym razie jest ona niedostępna.  
  
 **Dane wyjściowe (dla debugowania)**  
 Określa ścieżkę katalogu plików wyjściowych dla konfiguracji debugowania nowego projektu. Ta opcja jest włączona po **Użyj zewnętrznego systemu kompilacji** jest zaznaczona opcja **Określ ustawienia projektu** strony; w przeciwnym razie jest ona niedostępna.  
  
 **Definicje preprocesora (/ D)**  
 Definiuje symbole preprocesora dla nowego projektu. Aby uzyskać więcej informacji, zobacz [/D (definicje preprocesora)](../build/reference/d-preprocessor-definitions.md).  
  
 **Ścieżki wyszukiwania załączania (/ I)**  
 Określa ścieżki katalogów do dodania do listy katalogów, które kompilator będzie wyszukiwać można rozpoznać odwołania do pliku przekazany do dyrektywy preprocesora w nowym projekcie. Aby uzyskać więcej informacji, zobacz [/I (dodatkowe katalogi dołączenia)](../build/reference/i-additional-include-directories.md).  
  
 **Wymuszone załączone pliki (FI)**  
 Określa pliki nagłówkowe do przetworzenia podczas tworzenia nowego projektu. Aby uzyskać więcej informacji, zobacz [/FI (nazwij wymuszone obejmują plik)](../build/reference/fi-name-forced-include-file.md).  
  
 **Ścieżki wyszukiwania zestawu .NET (/ AI)**  
 Określa ścieżki katalogu, które kompilator będzie wyszukiwać można rozpoznać odwołania do zestawu .NET przekazany do dyrektywy preprocesora w nowym projekcie. Aby uzyskać więcej informacji, zobacz [/AI (Określ katalogi metadanych)](../build/reference/ai-specify-metadata-directories.md).  
  
 **Wymuszone używanie zestawów platformy .NET (/ FU)**  
 Określa zestawów platformy .NET do przetworzenia podczas tworzenia nowego projektu. Aby uzyskać więcej informacji, zobacz [/FU (nazwij wymuszone #using)](../build/reference/fu-name-forced-hash-using-file.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Określanie ustawień projektu, Kreator Utwórz nowy projekt z istniejących plików z kodem](../ide/specify-project-settings-create-new-project-from-existing-code-files-wizard.md)
