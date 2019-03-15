---
title: Rozwiązywanie problemów z dostosowaniami kompilacji
ms.date: 11/04/2016
helpviewer_keywords:
- build events [C++], troubleshooting
- builds [C++], build events
- troubleshooting [C++], builds
- build steps [C++], troubleshooting
- events [C++], build
- builds [C++], troubleshooting
- custom build steps [C++], troubleshooting
ms.assetid: e4ceb177-fbee-4ed3-a7d7-80f0d78c1d07
ms.openlocfilehash: 7a45b449dc9c3c4c81add37bbac0813c81133203
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823925"
---
# <a name="troubleshooting-build-customizations"></a>Rozwiązywanie problemów z dostosowaniami kompilacji

Jeśli niestandardowych kroków kompilacji lub zdarzenia nie zachowują się zgodnie z oczekiwaniami, istnieje kilka rzeczy, które można zrobić, aby zrozumieć, co się dzieje problem.

- Upewnij się, że pliki, które kroków kompilacji niestandardowej generować takie same jak pliki, zadeklarowanej jako dane wyjściowe.

- Jeśli Twoje niestandardowych kroków kompilacji wygenerowanie plików, które to dane wejściowe lub innych zależności kompilacji kroki (niestandardowego lub w inny sposób), upewnij się, że te pliki zostaną dodane do projektu. I upewnij się, że narzędzia, które korzystają z tych plików są wykonywane po krok niestandardowej kompilacji.

- Aby wyświetlić swoje niestandardowy krok kompilacji faktycznie działania, Dodaj `@echo on` jako pierwsze polecenie. Zdarzenia kompilacji i kroki kompilacji są umieścić w pliku tymczasowego bat i uruchamiany, gdy projekt jest kompilowany. W związku z tym można dodać błąd podczas sprawdzania do zdarzenia kompilacji, lub tworzenia poleceń kroku.

- W dzienniku kompilacji w katalogu plików pośrednich, aby zobaczyć, co faktycznie wykonywane. Ścieżka i nazwa dziennika kompilacji jest reprezentowany przez **MSBuild** wyrażeniu makra **$(IntDir)\\.log $(MSBuildProjectName)**.

- Zmodyfikuj ustawienia projektu, aby zebrać więcej niż domyślna ilość informacji w dzienniku kompilacji. Na **narzędzia** menu, kliknij przycisk **opcje**. W **opcje** okno dialogowe, kliknij przycisk **projekty i rozwiązania** węzeł, a następnie kliknij przycisk **kompilowanie i uruchamianie** węzła. Następnie w **poziom szczegółowości pliku dziennika MSBuild projektu kompilacji** kliknij **szczegółowe**.

- Sprawdź, czy wartości dowolnego pliku makra nazwa lub katalogu, którego używasz. Makra można echo osobno lub możesz dodać `copy %0 command.bat` na początku Twojego niestandardowego kroku kompilacji, który skopiuje poleceń Twoje krok niestandardowej kompilacji, aby command.bat z makrami wszystkie rozwinięte.

- Uruchomić kroki procesu kompilacji niestandardowej, a zdarzenia pojedynczo, aby sprawdzić ich zachowanie kompilacji.

## <a name="see-also"></a>Zobacz także

[Ogólne informacje o niestandardowych krokach budowania lub zdarzeniach kompilacji](understanding-custom-build-steps-and-build-events.md)