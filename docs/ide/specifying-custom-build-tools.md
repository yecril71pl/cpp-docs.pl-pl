---
title: Określanie niestandardowego narzędzia kompilacji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 06/05/2018
ms.technology:
- cpp-ide
ms.topic: conceptual
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
ms.workload:
- cplusplus
ms.openlocfilehash: 9e04cd1d5599663c878d7e9b06d9b0bd05a76242
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46433910"
---
# <a name="specify-custom-build-tools"></a>Określanie niestandardowych narzędzi kompilacji

A *niestandardowego narzędzia kompilacji* zapewnia system kompilacji przy użyciu informacji wymaganych do tworzenia określonych plików wejściowych. Niestandardowego narzędzia kompilacji Określa polecenie do uruchomienia, listę plików wejściowych, lista plików wyjściowych, które są generowane przez polecenie i opcjonalny opis tego narzędzia.

Aby uzyskać ogólne informacje o niestandardowych narzędzi kompilacji i niestandardowych kroków kompilacji, zobacz [niestandardowych krokach kompilacji zrozumienie i zdarzenia kompilacji](../ide/understanding-custom-build-steps-and-build-events.md).

### <a name="to-specify-a-custom-build-tool"></a>Aby określić niestandardowego narzędzia kompilacji

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [ustawienie właściwości projektu Visual C++](../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** umożliwiające **konfiguracji** pole. W **konfiguracji** wybierz konfigurację, dla którego chcesz określić niestandardowego narzędzia kompilacji.

1. W **Eksploratora rozwiązań**, wybierz plik danych wejściowych dla niestandardowego narzędzia kompilacji.

   Jeśli **niestandardowe narzędzia kompilacji** folder nie jest wyświetlana, rozszerzenie pliku wybrany plik jest skojarzony z narzędziem do domyślnego. Na przykład domyślnego narzędzia dla plików .c i .cpp to kompilator. Aby zastąpić domyślne ustawienie narzędzia w **właściwości konfiguracji** węzła w **ogólne** folder, w **typu elementu** właściwości, wybierz **niestandardowej kompilacji Narzędzie**. Wybierz **Zastosuj** i **niestandardowe narzędzia kompilacji** węzeł jest wyświetlany.

1. W **niestandardowego narzędzia kompilacji** węzła w **ogólne** folderu, określ właściwości skojarzone z się niestandardowe narzędzie kompilacji:

   - W **dodatkowe zależności**, określić żadnych dodatkowych plików innych niż ten, dla którego jest definiowany niestandardowego narzędzia kompilacji (plik skojarzony z niestandardowego narzędzia kompilacji jest niejawnie traktowane jako dane wejściowe do narzędzia). Masz dodatkowe pliki wejściowe nie jest wymagana dla niestandardowego narzędzia kompilacji. Jeśli masz więcej niż jeden dodatkowe dane wejściowe, rozdziel je średnikami.

      Jeśli **dodatkowe zależności** pliku Data jest późniejsza niż plik wejściowy, a następnie uruchomienie narzędzia kompilacji niestandardowej. Jeśli wszystkie z **dodatkowe zależności** pliki są starsze niż plik wejściowy i plik wejściowy jest starsza niż **dane wyjściowe** właściwości pliku, a następnie niestandardowego narzędzia kompilacji nie jest uruchamiany.

      Na przykład załóżmy, że masz narzędzie niestandardowej kompilacji, który przyjmuje MyInput.x jako dane wejściowe i generuje MyInput.cpp i że MyInput.x zawiera plik nagłówka, MyHeader.h. MyHeader.h można określić jako danych wejściowych zależności, aby MyInput.x, a system kompilacji zostanie skompilowany MyInput.cpp, gdy jest przestarzałe w odniesieniu do MyInput.x lub MyHeader.h.

      Zależności wejściowe może również zagwarantować, że Twoje niestandardowe narzędzia kompilacji uruchomione w kolejności, w której będą one potrzebne do. W powyższym przykładzie załóżmy, że MyHeader.h jest faktycznie danych wyjściowych niestandardowego narzędzia kompilacji. Ponieważ MyHeader.h zależność MyInput.x, system kompilacji najpierw utworzyć przed uruchomieniem tego narzędzia niestandardowej kompilacji na MyInput.x Myheader.h.

   - W **wiersza polecenia**, określ polecenie tak, jakby były określając ją w wierszu polecenia. Określ Prawidłowe polecenie lub pliku wsadowego i dowolne wymagane dane wejściowe lub wyjściowe pliki. Określ **wywołania** polecenia przed nazwą pliku wsadowego, aby zagwarantować, że wykonywane są wszystkie kolejne polecenia batch.

      Wiele plików wejściowych i wyjściowych można określić symbolicznie za pomocą makra programu MSBuild. Aby uzyskać informacje na temat sposobu określenia lokalizacji plików lub nazw zestawów plików, zobacz [typowe makra dla poleceń i właściwości kompilacji](../ide/common-macros-for-build-commands-and-properties.md).

      Ponieważ znak "%" jest zarezerwowany przez program MSBuild, jeśli określisz zmienną środowiskową, Zastąp każde **%** znakiem ucieczki **% 25** szesnastkowa sekwencja unikowa. Na przykład Zastąp ciąg **% WINDIR %** z **25WINDIR % 25**. Program MSBuild zastępuje każdy **% 25** sekwencji z **%** znak przed uzyskuje dostęp do zmiennej środowiskowej.

   - W **opis**, wprowadź opisowy komunikat dotyczący tego niestandardowego narzędzia kompilacji. Komunikat jest drukowany do **dane wyjściowe** okna, gdy system kompilacji przetwarza tego narzędzia.

   - W **dane wyjściowe**, określ nazwę pliku wyjściowego. Jest to wymagane zgłoszenia; niestandardowego narzędzia kompilacji nie będzie działać bez wartości dla tej właściwości. Jeśli narzędzie kompilacji niestandardowej ma więcej niż jedno wyjście, nazwy plików należy oddzielić średnikami.

      Nazwa pliku wyjściowego powinna być taka sama, jak określono w **wiersza polecenia** właściwości. System kompilacji projektu będzie szukać pliku i Sprawdź daty. Jeśli plik wyjściowy jest starszy niż plik wejściowy, lub jeśli plik wyjściowy nie zostanie znaleziony, jest uruchamiana niestandardowego narzędzia kompilacji. Jeśli wszystkie z **dodatkowe zależności** pliki są starsze niż plik wejściowy i plik wejściowy jest starszy niż plik określony w **dane wyjściowe** właściwości niestandardowego narzędzia kompilacji nie jest uruchamiane.

Jeśli chcesz, aby system kompilacji ma działać na plik wyjściowy, generowany przez narzędzie kompilacji niestandardowej, należy ręcznie dodać ją do projektu. Niestandardowego narzędzia kompilacji zaktualizuje pliku podczas kompilacji.

## <a name="example"></a>Przykład

Przyjęto założenie, czy chcesz dołączyć plik o nazwie parser.l w projekcie. Masz analizator leksykalny, **lexer.exe**, na ścieżka do pliku wykonywalnego. Chcesz jej używać do przetwarzania parser.l, aby wygenerować plik .c, który ma taką samą nazwę (parser.c).

Najpierw dodaj parser.l i parser.c do projektu. Jeśli pliki nie istnieją, należy dodać odwołanie do plików. Tworzenie niestandardowego narzędzia kompilacji dla parser.l, a następnie wprowadź następujące informacje w **polecenia** właściwości:

> **%(FullPath) leksera. \%.C (nazwa_pliku)**

To polecenie działa analizator leksykalny parser.l i generuje parser.c do katalogu projektu.

W **dane wyjściowe** właściwość, należy wprowadzić następujące czynności:

> **. \%.C (nazwa_pliku)**

Podczas kompilowania projektu systemu kompilacji porównuje sygnatury czasowe parser.l i parser.c. Jeśli parser.l jest nowsza, lub Jeśli parser.c nie istnieje, wartość jest uruchomiony system kompilacji **wiersza polecenia** właściwości, aby wyświetlić parser.c bądź na bieżąco. Ponieważ parser.c został również dodany do projektu, system kompilacji kompiluje następnie parser.c.

## <a name="see-also"></a>Zobacz także

[Typowe makra dla właściwości i poleceń kompilacji](../ide/common-macros-for-build-commands-and-properties.md)<br>
[Rozwiązywanie problemów z dostosowaniami kompilacji](../ide/troubleshooting-build-customizations.md)
