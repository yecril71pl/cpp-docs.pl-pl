---
title: "Określanie zdarzenia kompilacji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.IVCEventTool.CommandLine
- VC.Project.IVCEventTool.ExcludedFromBuild
- VC.Project.IVCEventTool.Description
dev_langs: C++
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
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 43f12e28487a4e162a88eaf0881ac9e50391e1f4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="specifying-build-events"></a>Określanie zdarzeń kompilacji
Można użyć kompilacji zdarzeń, aby określić polecenia uruchamiane przed rozpoczęciem kompilacji, zanim proces łącze lub po zakończeniu kompilacji.  
  
 Zdarzenia kompilacji są wykonywane tylko wtedy, gdy kompilacja pomyślnie osiągnie tych punktów w procesie kompilacji. W przypadku wystąpienia błędu w kompilacji, *postkompilacyjnego* zdarzeń nie nastąpi; Jeśli błąd pojawia się przed fazy połączeń nie *prekonsolidacyjnego* ani *postkompilacyjnego* zdarzeń będzie wystąpić. Ponadto, jeśli nie pliki muszą być połączone *prekonsolidacyjnego* nie wystąpi zdarzenie. *Prekonsolidacyjnego* również zdarzenie nie jest dostępna w projektach, które nie zawierają krok łącza.  
  
 Jeśli żadne pliki nie muszą zostać skompilowane, Brak zdarzeń kompilacji zostanie przeprowadzona.  
  
 Aby uzyskać ogólne informacje dotyczące zdarzeń kompilacji, zobacz [kroki tworzenia niestandardowej opis i tworzenie zdarzenia](../ide/understanding-custom-build-steps-and-build-events.md).  
  
### <a name="to-specify-a-build-event"></a>Aby określić zdarzenia kompilacji  
  
1.  W **Eksploratora rozwiązań**, wybierz projekt, dla którego ma zostać określone zdarzenie kompilacji.  
  
2.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../ide/working-with-project-properties.md).  
  
3.  W **zdarzeń kompilacji** folderu, wybierz stronę właściwości zdarzeń kompilacji.  
  
4.  Określ właściwości skojarzone ze zdarzeniem kompilacji:  
  
    -   W **wiersza polecenia**, określić polecenie, tak jakby był on określenie w wierszu polecenia. Określ prawidłowy polecenia lub pliku wsadowego, a wszelkie wymagane dane wejściowe lub plików wyjściowych. Określ **wywołać** partii polecenia przed nazwą pliku wsadowego, aby zagwarantować, że wszystkie kolejne polecenia są wykonywane.  
  
         Wiele plików wejściowych i wyjściowych można określić symbolicznie z makra programu MSBuild. [!INCLUDE[crabout](../build/reference/includes/crabout_md.md)]Określanie lokalizacji plików lub nazw zestawów plików, zobacz [wspólnej makra dla poleceń kompilacji oraz właściwości](../ide/common-macros-for-build-commands-and-properties.md).  
  
         Ponieważ znak "%" jest zarezerwowany przez program MSBuild, jeśli określisz zmienną środowiskową Zastąp każdego  **%**  ucieczki znaku o **% 25** szesnastkowa sekwencja unikowa. Na przykład zastąpić **% WINDIR %** z **25WINDIR % 25**. MSBuild zastępuje wszystkie **% 25** sekwencji z  **%**  znak przed uzyskuje dostęp do zmiennej środowiskowej.  
  
    -   W **opis**, wpisz opis dla tego zdarzenia. Opis będą wypisywane w **dane wyjściowe** okna po wystąpieniu tego zdarzenia.  
  
    -   W **wyłączone z kompilacji**, określ **tak** , jeśli nie chcesz, aby zdarzenia umożliwia uruchamianie.  
  
## <a name="see-also"></a>Zobacz też  
 [Opis niestandardowe kroki procesu kompilacji lub zdarzeniach kompilacji](../ide/understanding-custom-build-steps-and-build-events.md)   
 [Typowe makra dla poleceń kompilacji oraz właściwości](../ide/common-macros-for-build-commands-and-properties.md)   
 [Rozwiązywanie problemów z dostosowaniami kompilacji](../ide/troubleshooting-build-customizations.md)