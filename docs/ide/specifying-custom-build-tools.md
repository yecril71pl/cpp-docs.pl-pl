---
title: "Określanie niestandardowych narzędzi kompilacji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 12/28/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCustomBuildTool.CustomBuildToolBeforeTargets
- VC.Project.VCCustomBuildTool.Outputs
- VC.Project.VCCustomBuildTool.Command
- VC.Project.VCCustomBuildTool.CommandLine
- VC.Project.VCCustomBuildTool.AdditionalDependencies
- VC.Project.VCCustomBuildTool.Message
- VC.Project.VCCustomBuildTool.CustomBuildToolAfterTargets
- VC.Project.VCCustomBuildTool.Description
- VC.Project.VCCustomBuildTool.AdditionalInputs
dev_langs:
- C++
helpviewer_keywords:
- build tools (C++), specifying
- custom build tools (C++), specifying
- builds (C++), custom build tools
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4edd3b1fdb2b6d09be6f5fcd9a6c9d08ba7a6994
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2018
---
# <a name="specify-custom-build-tools"></a>Określ niestandardowe narzędzia kompilacji

A *niestandardowego narzędzia kompilacji* zapewnia system kompilacji potrzebnych do tworzenia plików wejściowych określonych informacji. Narzędzie niestandardowej kompilacji Określa polecenie do uruchomienia, listę plików wejściowych, lista plików wyjściowych, które są generowane przez polecenie i opcjonalny opis narzędzia.

Aby uzyskać ogólne informacje o niestandardowych narzędzi kompilacji i niestandardowe kroki procesu kompilacji, zobacz [niestandardowych krokach kompilacji zrozumienia i tworzenie zdarzenia](../ide/understanding-custom-build-steps-and-build-events.md).

### <a name="to-specify-a-custom-build-tool"></a>Aby określić niestandardowe narzędzie kompilacji

1. Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Ustawianie właściwości projektu Visual C++](../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** umożliwiające **konfiguracji** pole. W **konfiguracji** wybierz konfigurację, dla której ma zostać określone narzędzia kompilacji niestandardowej.

1. W **Eksploratora rozwiązań**, wybierz plik wejściowy dla niestandardowego narzędzia kompilacji.

   Jeśli **niestandardowe narzędzia kompilacji** folder nie jest wyświetlana, rozszerzenie pliku wybrany plik jest skojarzony z domyślnym narzędziem. Na przykład domyślnego narzędzia dla plików .c i .cpp jest kompilatora. Aby zastąpić domyślne ustawienie narzędzia w **właściwości konfiguracji** węzła w **ogólne** folderu w **typu elementu** właściwości, wybierz **niestandardowej kompilacji Narzędzie**. Wybierz **Zastosuj** i **niestandardowe narzędzia kompilacji** węzeł jest wyświetlany.

1. W **niestandardowe narzędzia kompilacji** węzła w **ogólne** folderu, określ właściwości skojarzone z niestandardowe narzędzie kompilacji:

   - W **dodatkowe zależności**, określ wszelkie dodatkowe pliki poza jednym, dla którego jest definiowany niestandardowego narzędzia kompilacji (pliku skojarzone z niestandardowego narzędzia kompilacji jest niejawnie uznane za dane wejściowe do narzędzia). O dodatkowe pliki wejściowe nie jest wymagane dla narzędzia kompilacji niestandardowej. Jeśli masz więcej niż jeden dodatkowych danych wejściowych, oddziel je średnikami.

      Jeśli **dodatkowe zależności** pliku Data jest późniejsza niż pliku wejściowego, a następnie uruchomienie narzędzia kompilacji niestandardowej. Jeśli wszystkie z **dodatkowe zależności** pliki są starsze niż pliku wejściowego i pliku wejściowego jest starsza niż **dane wyjściowe** właściwości pliku, a następnie niestandardowego narzędzia kompilacji nie zostało uruchomione.

      Załóżmy na przykład narzędzie niestandardowej kompilacji, która przyjmuje MyInput.x jako dane wejściowe i generuje MyInput.cpp i że MyInput.x zawiera plik nagłówka, MyHeader.h. MyHeader.h można określić jako zależność od MyInput.x wejściowych, a system kompilacji zostanie skompilowany MyInput.cpp, gdy jest nieaktualne względem MyInput.x lub MyHeader.h.

      Wejściowy zależności zapewni, że Twoje niestandardowe narzędzia kompilacji są uruchamiane w kolejności potrzebnych im. W powyższym przykładzie załóżmy, że MyHeader.h jest rzeczywiście dane wyjściowe narzędzia kompilacji niestandardowej. Ponieważ MyHeader.h zależność MyInput.x, system kompilacji najpierw utworzyć przed uruchomieniem tego narzędzia niestandardowej kompilacji na MyInput.x Myheader.h.

   - W **wiersza polecenia**, określić polecenie, tak jakby był on określenie w wierszu polecenia. Określ prawidłowy polecenia lub pliku wsadowego, a wszelkie wymagane dane wejściowe lub plików wyjściowych. Określ **wywołać** partii polecenia przed nazwą pliku wsadowego, aby zagwarantować, że wszystkie kolejne polecenia są wykonywane.

      Wiele plików wejściowych i wyjściowych można określić symbolicznie z makra programu MSBuild. Aby uzyskać informacje na temat sposobu Określ lokalizację plików lub nazw zestawów plików, zobacz [wspólnej makra dla poleceń kompilacji oraz właściwości](../ide/common-macros-for-build-commands-and-properties.md).

      Ponieważ znak "%" jest zarezerwowany przez program MSBuild, jeśli określisz zmienną środowiskową Zastąp każdego  **%**  ucieczki znaku o **% 25** szesnastkowa sekwencja unikowa. Na przykład zastąpić **% WINDIR %** z **25WINDIR % 25**. MSBuild zastępuje wszystkie **% 25** sekwencji z  **%**  znak przed uzyskuje dostęp do zmiennej środowiskowej.

   - W **opis**, wprowadź opisowy komunikat dotyczący tego narzędzia kompilacji niestandardowej. Komunikat jest drukowana **dane wyjściowe** okna, jeśli system kompilacji przetwarza tego narzędzia.

   - W **dane wyjściowe**, określ nazwę pliku wyjściowego. Jest to wymagane wpis; Narzędzie niestandardowej kompilacji bez wartości dla tej właściwości, nie będzie działać. Jeśli narzędzie niestandardowej kompilacji ma więcej niż jedno wyjście, Rozdziel nazwy plików średnikami.

      Nazwę pliku wyjściowego powinny być takie same, jak określono w **wiersza polecenia** właściwości. System kompilacji projektu Szukaj pliku, a następnie sprawdź daty. Jeśli plik wyjściowy jest nowszy niż plik wejściowy lub jeśli plik wyjściowy nie zostanie znaleziony, uruchomienie narzędzia kompilacji niestandardowej. Jeśli wszystkie z **dodatkowe zależności** pliki są starsze niż pliku wejściowego i pliku wejściowego jest starsza niż określona w pliku **dane wyjściowe** właściwości niestandardowego narzędzia kompilacji nie zostało uruchomione.

Jeśli chcesz, aby system kompilacji do działania na plik wyjściowy wygenerowany przez narzędzie niestandardowej kompilacji, użytkownik musi ręcznie dodać do projektu. Narzędzie niestandardowej kompilacji spowoduje zaktualizowanie pliku podczas kompilacji.

## <a name="example"></a>Przykład

Przyjęto założenie, że chcesz uwzględnić w pliku o nazwie parser.l w projekcie. Masz leksykalne analyzer **lexer.exe**, na ścieżce pliku wykonywalnego. Chcesz go używać do przetwarzania parser.l w celu utworzenia pliku .c, który ma taką samą nazwę podstawową (parser.c).

Najpierw dodaj parser.l i parser.c do projektu. Jeśli pliki jeszcze nie istnieją, Dodaj odwołanie do plików. Tworzenie niestandardowego narzędzia kompilacji dla parser.l i wprowadź następujące w **polecenia** właściwości:

> **lexer %(FullPath). \%.C (nazwa_pliku)**

To polecenie uruchamia leksykalne analizatora na parser.l i wyprowadza parser.c do katalogu projektu.

W **dane wyjściowe** właściwości, wprowadź następujące:

> **. \%.C (nazwa_pliku)**

Podczas kompilowania projektu system kompilacji porównuje sygnatury czasowe parser.l i parser.c. Jeśli parser.l jest nowsza, lub Jeśli parser.c nie istnieje, system kompilacji uruchamia wartość **wiersza polecenia** właściwości można wyświetlić parser.c aktualne. Ponieważ parser.c również został dodany do projektu, system kompilacji następnie kompiluje parser.c.

## <a name="see-also"></a>Zobacz także

[Typowe makra dla właściwości i poleceń kompilacji](../ide/common-macros-for-build-commands-and-properties.md)  
[Rozwiązywanie problemów z dostosowaniami kompilacji](../ide/troubleshooting-build-customizations.md)  
