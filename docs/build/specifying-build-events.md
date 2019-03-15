---
title: Określanie zdarzeń kompilacji
ms.date: 12/28/2017
f1_keywords:
- VC.Project.IVCEventTool.CommandLine
- VC.Project.IVCEventTool.ExcludedFromBuild
- VC.Project.IVCEventTool.Description
helpviewer_keywords:
- Pre-Link event
- build events [C++], specifying
- custom build steps [C++], build events
- builds [C++], events
- events [C++], build
- builds [C++], customizing C++
- build events [C++]
- post-build events
ms.assetid: 788a6c18-2dbe-4a49-8cd6-86c1ad7a95cc
ms.openlocfilehash: c8097e013f934c45b8e3860b8377bdb2bdb9d9a0
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823780"
---
# <a name="specifying-build-events"></a>Określanie zdarzeń kompilacji

Korzystanie ze zdarzeń kompilacji, aby określić polecenia uruchamiane przed rozpoczęciem kompilacji, zanim proces łącze lub po zakończeniu kompilacji.

Zdarzenia kompilacji są wykonywane tylko wtedy, gdy kompilacja pomyślnie osiągnie tych punktów w procesie kompilacji. W przypadku wystąpienia błędu w kompilacji, *postkompilacyjnego* zdarzenie nie występuje; Jeśli ten błąd występuje przed fazy połączeń ani *prekonsolidacyjnego* ani *po kompilacji* zdarzeń występuje. Ponadto, jeśli żadne pliki nie muszą być połączone *prekonsolidacyjnego* zdarzenie nie występuje. *Prekonsolidacyjnego* również zdarzenie nie jest dostępne w projektach, które nie zawierają krokiem link.

Jeśli żadne pliki nie muszą zostać skompilowane, występować żadne zdarzenia kompilacji.

Aby uzyskać ogólne informacje na temat zdarzeń kompilacji, zobacz [kroki tworzenia niestandardowych interpretacji i zdarzenia kompilacji](understanding-custom-build-steps-and-build-events.md).

### <a name="to-specify-a-build-event"></a>Aby określić zdarzenia kompilacji

1. W **Eksploratora rozwiązań**, wybierz projekt, dla którego chcesz określić zdarzeń kompilacji.

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](working-with-project-properties.md).

1. W **zdarzenia kompilacji** folderu, wybierz stronę właściwości zdarzenia kompilacji.

1. Określ właściwości skojarzonego ze zdarzeniem kompilacji:

   - W **wiersza polecenia**, określ polecenie tak, jakby były określając ją w wierszu polecenia. Określ Prawidłowe polecenie lub pliku wsadowego i dowolne wymagane dane wejściowe lub wyjściowe pliki. Określ **wywołania** polecenia przed nazwą pliku wsadowego, aby zagwarantować, że wykonywane są wszystkie kolejne polecenia batch.

      Wiele plików wejściowych i wyjściowych można określić symbolicznie za pomocą makra programu MSBuild. Aby uzyskać informacje na temat sposobu określenia lokalizacji plików lub nazw zestawów plików, zobacz [typowe makra dla kompilacji polecenia i właściwości](reference/common-macros-for-build-commands-and-properties.md).

      Ponieważ znak "%" jest zarezerwowany przez program MSBuild, jeśli określisz zmienną środowiskową, Zastąp każde **%** znakiem ucieczki **% 25** szesnastkowa sekwencja unikowa. Na przykład Zastąp ciąg **% WINDIR %** z **25WINDIR % 25**. Program MSBuild zastępuje każdy **% 25** sekwencji z **%** znak przed uzyskuje dostęp do zmiennej środowiskowej.

   - W **opis**, wpisz opis tego zdarzenia. Opis zostanie wydrukowany do **dane wyjściowe** okna tego zdarzenia.

   - W **wyłączone z kompilacji**, określ **tak** Jeśli nie chcesz, aby zdarzenia umożliwia uruchamianie.

## <a name="see-also"></a>Zobacz także

[Ogólne informacje o niestandardowych krokach budowania lub zdarzeniach kompilacji](understanding-custom-build-steps-and-build-events.md)<br>
[Typowe makra dla poleceń kompilacji oraz właściwości](reference/common-macros-for-build-commands-and-properties.md)<br>
[Rozwiązywanie problemów z dostosowaniami kompilacji](troubleshooting-build-customizations.md)
