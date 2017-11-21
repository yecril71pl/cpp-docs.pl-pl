---
title: "Właściwości konsolidatora (C++ systemu Linux) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 9/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a0243a94-8164-425b-b2fe-b84ff363d546
author: mikeblome
ms.author: mblome
manager: ghogen
f1_keywords:
- VC.Project.VCLinkerTool.OutputFile
- VC.Project.VCLinkerTool.ShowProgress
- VC.Project.VCLinkerTool.Version
- VC.Project.VCLinkerTool.VerboseOutput
- VC.Project.VCLinkerTool.UnresolvedReferences
- VC.Project.VCLinkerTool.OptimizeForMemory
- VC.Project.VCLinkerTool.SharedLibrarySearchPath
- VC.Project.VCLinkerTool.AdditionalLibraryDirectories
- VC.Project.VCConfiguration.BuildLogFile
- VC.Project.VCLinkerTool.IgnoreDefaultLibraryNames
- VC.Project.VCLinkerTool.ForceSymbolReferences
- VC.Project.VCLinkerTool.LibraryDependencies
- VC.Project.VCLinkerTool.ForceFileOutput
- VC.Project.VCLinkerTool.GenerateMapFile
- VC.Project.VCLinkerTool.Relocation
- VC.Project.VCLinkerTool.FunctionBinding
- VC.Project.VCLinkerTool.NoExecStackRequired
- VC.Project.WholeArchive
- VC.Project.AdditionalOptionsPage
- VC.Project.VCLinkerTool.AdditionalDependencies
ms.openlocfilehash: 963d73e73e42930f0245c0fef443da27bf451bc6
ms.sourcegitcommit: ca2f94dfd015e0098a6eaf5c793ec532f1c97de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="linker-properties-linux-c"></a>Właściwości konsolidatora (Linux C++)

## <a name="general"></a>Ogólne
Właściwość | Opis | Opcje
--- | ---| ---
Plik wyjściowy | Opcja przesłania domyślną nazwę i lokalizację programu tworzonego przez konsolidatora. (-o).
Pokaż postęp | Drukuje wiadomości dotyczące postępu konsolidatora.
Wersja | -Version — opcja nakazuje konsolidatorowi umieszczenie numeru wersji w nagłówku pliku wykonywalnego.
Włącz pełne dane wyjściowe | Verbose — opcja nakazuje konsolidatorowi wysyłanie pełnych komunikatów na potrzeby debugowania.
śledzenia | Śledzenia opcja informuje konsolidator, aby dane wyjściowe plików wejściowych, jak są przetwarzane.
Symbole śledzenia | Drukować listę plików, w których występuje symbol. (— symbol śledzenia = symboli)
Drukowanie mapy | Mapy drukowania opcja informuje konsolidator, aby dane wyjściowe mapy łącza.
Raport nierozpoznanych odwołań do symboli | Włączenie tej opcji będzie zgłaszać nierozpoznanych odwołań do symboli.
Optymalizuj pod kątem użycia pamięci | Optymalizuj pod kątem użycia pamięci przez ponowne odczytanie tabel symboli, jeśli to konieczne.
Ścieżka wyszukiwania biblioteki udostępnionej | Umożliwia użytkownikowi wypełnienie ścieżki wyszukiwania biblioteki udostępnionej. (link - rpath-= ścieżka)
Katalogi bibliotek dodatkowe | Umożliwia użytkownikowi przesłanianie ścieżki środowiskowej biblioteki. (-L folder).
Konsolidatora | Określa program do wywołania podczas łączenia lub ścieżka do konsolidatora w systemie zdalnym.
Limit czasu łącza | Zdalne połączenie limit czasu w milisekundach.
Kopiuj dane wyjściowe | Określa, czy można skopiować pliku danych wyjściowych kompilacji z systemu zdalnego na komputerze lokalnym.

## <a name="input"></a>Dane wejściowe
Właściwość | Opis | Opcje
--- | ---| ---
Ignoruj określone biblioteki domyślne | Określa jedną lub więcej nazw bibliotek domyślnych do zignorowania. (— Wyklucz biblioteki lib, lib)
Ignoruj biblioteki domyślne | Ignoruj biblioteki domyślne i wyszukiwanie tylko określone jawnie bibliotek.
Niezdefiniowany Symbol odwołań Force | Wymuś symbolu, które zostaną wprowadzone w pliku wyjściowym jako niezdefiniowanego symbolu. (- u symbol--niezdefiniowana = symboli)
Zależności biblioteki | Ta opcja umożliwia określenie dodatkowych bibliotek, które mają zostać dodane do wiersza polecenia konsolidatora. Dodatkowe biblioteki zostaną dodane na końcu wiersza polecenia konsolidatora prefiksem "lib" i kończyć się rozszerzeniem ".a".  (-lFILE)
Dodatkowe zależności | Określa dodatkowe elementy do dodania do wiersza polecenia konsolidacji.

## <a name="debugging"></a>Debugowanie
Właściwość | Opis | Opcje
--- | ---| ---
Informacje o symbolach debugera | Informacje o symbolach z pliku danych wyjściowych debugera. | **Uwzględnij wszystkie**<br>**Pomiń informacje o symbolach debugera tylko**<br>**Pomiń informacje o wszystkich symbolach**<br>
Nazwa pliku mapy | Opcja Map nakazuje konsolidatorowi utworzenie pliku mapy o nazwie określonej przez użytkownika. (-Mapy =)

## <a name="advanced"></a>Zaawansowane
Właściwość | Opis | Opcje
--- | ---| ---
Oznacz zmienne tylko do odczytu po relokacji | Ta opcja oznacza zmienne jako tylko do odczytu po relokacji.
Włącz natychmiastowe powiązanie funkcji | Ta opcja oznacza obiekt do natychmiastowego powiązania funkcji.
Nie wymagają stosu wykonywalnego | Ta opcja oznacza dane wyjściowe jako niewymagające stosu wykonywalnego.
Całe archiwum | Całe archiwum używa całego kodu ze źródeł i zależności dodatkowych.


## <a name="additional-options"></a>Dodatkowe opcje



