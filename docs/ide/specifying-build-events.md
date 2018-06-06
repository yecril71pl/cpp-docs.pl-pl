---
title: Określanie zdarzenia kompilacji | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 5940f0d6efaec402a4a85ed659f42d7eab1bf91d
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "33334967"
---
# <a name="specifying-build-events"></a>Określanie zdarzeń kompilacji

Można użyć kompilacji zdarzeń, aby określić polecenia uruchamiane przed rozpoczęciem kompilacji, zanim proces łącze lub po zakończeniu kompilacji.

Zdarzenia kompilacji są wykonywane tylko wtedy, gdy kompilacja pomyślnie osiągnie tych punktów w procesie kompilacji. W przypadku wystąpienia błędu w kompilacji, *postkompilacyjnego* zdarzenie nie występuje; Jeśli błąd pojawia się przed fazy połączeń ani *prekonsolidacyjnego* ani *postkompilacyjnego* zdarzeń występuje. Ponadto, jeśli nie pliki muszą być połączone *prekonsolidacyjnego* zdarzenie nie występuje. *Prekonsolidacyjnego* również zdarzenie nie jest dostępna w projektach, które nie zawierają krok łącza.

Jeśli żadne pliki nie muszą zostać skompilowane, występować żadne zdarzenia kompilacji.

Aby uzyskać ogólne informacje dotyczące zdarzeń kompilacji, zobacz [kroki tworzenia niestandardowej opis i tworzenie zdarzenia](../ide/understanding-custom-build-steps-and-build-events.md).

### <a name="to-specify-a-build-event"></a>Aby określić zdarzenia kompilacji

1. W **Eksploratora rozwiązań**, wybierz projekt, dla którego ma zostać określone zdarzenie kompilacji.

1. Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../ide/working-with-project-properties.md).

1. W **zdarzeń kompilacji** folderu, wybierz stronę właściwości zdarzeń kompilacji.

1. Określ właściwości skojarzone ze zdarzeniem kompilacji:

   - W **wiersza polecenia**, określić polecenie, tak jakby był on określenie w wierszu polecenia. Określ prawidłowy polecenia lub pliku wsadowego, a wszelkie wymagane dane wejściowe lub plików wyjściowych. Określ **wywołać** partii polecenia przed nazwą pliku wsadowego, aby zagwarantować, że wszystkie kolejne polecenia są wykonywane.

      Wiele plików wejściowych i wyjściowych można określić symbolicznie z makra programu MSBuild. Aby uzyskać informacje na temat sposobu Określ lokalizację plików lub nazw zestawów plików, zobacz [wspólnej makra dla poleceń kompilacji oraz właściwości](../ide/common-macros-for-build-commands-and-properties.md).

      Ponieważ znak "%" jest zarezerwowany przez program MSBuild, jeśli określisz zmienną środowiskową Zastąp każdego **%** ucieczki znaku o **% 25** szesnastkowa sekwencja unikowa. Na przykład zastąpić **% WINDIR %** z **25WINDIR % 25**. MSBuild zastępuje wszystkie **% 25** sekwencji z **%** znak przed uzyskuje dostęp do zmiennej środowiskowej.

   - W **opis**, wpisz opis dla tego zdarzenia. Opis drukowania na **dane wyjściowe** okna po wystąpieniu tego zdarzenia.

   - W **wyłączone z kompilacji**, określ **tak** , jeśli nie chcesz, aby zdarzenia umożliwia uruchamianie.

## <a name="see-also"></a>Zobacz także

[Ogólne informacje o niestandardowych krokach budowania lub zdarzeniach kompilacji](../ide/understanding-custom-build-steps-and-build-events.md)  
[Typowe makra dla właściwości i poleceń kompilacji](../ide/common-macros-for-build-commands-and-properties.md)  
[Rozwiązywanie problemów z dostosowaniami kompilacji](../ide/troubleshooting-build-customizations.md)  
