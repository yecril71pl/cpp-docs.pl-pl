---
title: Nowy projekt z istniejącego kodu debugowania ustawienie (Visual C++) | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: df50dfba79ad4160728e77b96d5814d6b03add1e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46440893"
---
# <a name="specify-debug-configuration-settings-create-new-project-from-existing-code-files-wizard"></a>Określ ustawienia konfiguracji debugowania, Kreator Utwórz nowy projekt z istniejących plików z kodem

Aby określić ustawienia projektu dla konfiguracji debugowania, należy użyć tej strony kreator Utwórz nowy projekt z istniejących plików kodu.

## <a name="task-list"></a>Lista zadań

[Instrukcje: tworzenie projektu C++ z istniejącego kodu](../ide/how-to-create-a-cpp-project-from-existing-code.md)

## <a name="uielement-list"></a>Lista elementów UI

- **Wiersz polecenia kompilacji**

   Określa wiersz polecenia, który tworzy nowy projekt. Na przykład wprowadź nazwę kompilator (oraz wszystkie przełączniki i argumenty) lub kompilacji skryptów, że chcesz użyć do utworzenia nowego projektu. Ta opcja jest włączona po **Użyj zewnętrznego systemu kompilacji** jest zaznaczona opcja **Określ ustawienia projektu** strony; w przeciwnym razie jest ona niedostępna.

- **Ponownie skompiluj wiersza polecenia**

   Określa wiersz polecenia, która odtwarza nowy projekt. Ta opcja jest włączona po **Użyj zewnętrznego systemu kompilacji** jest zaznaczona opcja **Określ ustawienia projektu** strony; w przeciwnym razie jest ona niedostępna.

- **Wiersz poleceń oczyszczenia**

   Określa wiersz polecenia, aby usunąć pliki obsługi, generowane przez narzędzia do kompilacji dla nowego projektu. Ta opcja jest włączona po **Użyj zewnętrznego systemu kompilacji** jest zaznaczona opcja **Określ ustawienia projektu** strony; w przeciwnym razie jest ona niedostępna.

- **Dane wyjściowe (na potrzeby debugowania)**

   Określa ścieżkę katalogu plików wyjściowych dla konfiguracji debugowania w nowym projekcie. Ta opcja jest włączona po **Użyj zewnętrznego systemu kompilacji** jest zaznaczona opcja **Określ ustawienia projektu** strony; w przeciwnym razie jest ona niedostępna.

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
