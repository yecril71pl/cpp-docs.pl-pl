---
title: Określanie zdarzeń kompilacji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 12/28/2017
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.IVCEventTool.CommandLine
- VC.Project.IVCEventTool.ExcludedFromBuild
- VC.Project.IVCEventTool.Description
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dfdedf01c6203c483c1aa30d5d2934caa66e76d2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46375971"
---
# <a name="specifying-build-events"></a>Określanie zdarzeń kompilacji

Korzystanie ze zdarzeń kompilacji, aby określić polecenia uruchamiane przed rozpoczęciem kompilacji, zanim proces łącze lub po zakończeniu kompilacji.

Zdarzenia kompilacji są wykonywane tylko wtedy, gdy kompilacja pomyślnie osiągnie tych punktów w procesie kompilacji. W przypadku wystąpienia błędu w kompilacji, *postkompilacyjnego* zdarzenie nie występuje; Jeśli ten błąd występuje przed fazy połączeń ani *prekonsolidacyjnego* ani *po kompilacji* zdarzeń występuje. Ponadto, jeśli żadne pliki nie muszą być połączone *prekonsolidacyjnego* zdarzenie nie występuje. *Prekonsolidacyjnego* również zdarzenie nie jest dostępne w projektach, które nie zawierają krokiem link.

Jeśli żadne pliki nie muszą zostać skompilowane, występować żadne zdarzenia kompilacji.

Aby uzyskać ogólne informacje na temat zdarzeń kompilacji, zobacz [kroki tworzenia niestandardowych interpretacji i zdarzenia kompilacji](../ide/understanding-custom-build-steps-and-build-events.md).

### <a name="to-specify-a-build-event"></a>Aby określić zdarzenia kompilacji

1. W **Eksploratora rozwiązań**, wybierz projekt, dla którego chcesz określić zdarzeń kompilacji.

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../ide/working-with-project-properties.md).

1. W **zdarzenia kompilacji** folderu, wybierz stronę właściwości zdarzenia kompilacji.

1. Określ właściwości skojarzonego ze zdarzeniem kompilacji:

   - W **wiersza polecenia**, określ polecenie tak, jakby były określając ją w wierszu polecenia. Określ Prawidłowe polecenie lub pliku wsadowego i dowolne wymagane dane wejściowe lub wyjściowe pliki. Określ **wywołania** polecenia przed nazwą pliku wsadowego, aby zagwarantować, że wykonywane są wszystkie kolejne polecenia batch.

      Wiele plików wejściowych i wyjściowych można określić symbolicznie za pomocą makra programu MSBuild. Aby uzyskać informacje na temat sposobu określenia lokalizacji plików lub nazw zestawów plików, zobacz [typowe makra dla poleceń i właściwości kompilacji](../ide/common-macros-for-build-commands-and-properties.md).

      Ponieważ znak "%" jest zarezerwowany przez program MSBuild, jeśli określisz zmienną środowiskową, Zastąp każde **%** znakiem ucieczki **% 25** szesnastkowa sekwencja unikowa. Na przykład Zastąp ciąg **% WINDIR %** z **25WINDIR % 25**. Program MSBuild zastępuje każdy **% 25** sekwencji z **%** znak przed uzyskuje dostęp do zmiennej środowiskowej.

   - W **opis**, wpisz opis tego zdarzenia. Opis zostanie wydrukowany do **dane wyjściowe** okna tego zdarzenia.

   - W **wyłączone z kompilacji**, określ **tak** Jeśli nie chcesz, aby zdarzenia umożliwia uruchamianie.

## <a name="see-also"></a>Zobacz także

[Ogólne informacje o niestandardowych krokach budowania lub zdarzeniach kompilacji](../ide/understanding-custom-build-steps-and-build-events.md)<br>
[Typowe makra dla właściwości i poleceń kompilacji](../ide/common-macros-for-build-commands-and-properties.md)<br>
[Rozwiązywanie problemów z dostosowaniami kompilacji](../ide/troubleshooting-build-customizations.md)
