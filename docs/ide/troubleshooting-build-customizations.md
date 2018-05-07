---
title: Rozwiązywanie problemów z kompilacji dostosowania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- build events [C++], troubleshooting
- builds [C++], build events
- troubleshooting [C++], builds
- build steps [C++], troubleshooting
- events [C++], build
- builds [C++], troubleshooting
- custom build steps [C++], troubleshooting
ms.assetid: e4ceb177-fbee-4ed3-a7d7-80f0d78c1d07
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d48e9f7bdcbf422a25fb0bdb40411e6c662fadc2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="troubleshooting-build-customizations"></a>Rozwiązywanie problemów z dostosowaniami kompilacji
Niestandardowe kroki procesu kompilacji lub zdarzenia nie zachowują się zgodnie z oczekiwaniami, istnieje kilka kwestii, które może wykonywać próby zrozumieć, co się dzieje niewłaściwy.  
  
-   Upewnij się, że pliki, które Generowanie Twoje niestandardowe kroki procesu kompilacji zgodne pliki, które należy zadeklarować jako dane wyjściowe.  
  
-   Jeśli Twoje niestandardowe kroki procesu kompilacji generować pliki, które są dane wejściowe lub zależności innych kompilacji czynności (niestandardowego lub innych), upewnij się, że te pliki zostaną dodane do projektu. I upewnij się, że narzędzia, które korzystają z tych plików są wykonywane po kroku kompilacji niestandardowej.  
  
-   Wyświetlane użytkownika niestandardowego kroku kompilacji faktycznie czynności, dodawać `@echo on` jako pierwsze polecenie. Zdarzenia kompilacji i kroki kompilacji są umieścić w pliku tymczasowego bat i uruchamiane po utworzeniu projektu. W związku z tym można dodać błąd sprawdzania zdarzenie kompilacji lub polecenia kroku kompilacji.  
  
-   Przeanalizuj dziennik kompilacji w katalogu plików pośrednich, aby sprawdzić, co faktycznie wykonywane. Ścieżka i nazwa dziennika kompilacji jest reprezentowana przez **MSBuild** wyrażeniu makra **$(IntDir)\\log $(MSBuildProjectName)**.  
  
-   Zmodyfikuj ustawienia projektu, aby zbierać więcej niż domyślna ilość informacji w dzienniku kompilacji. Na **narzędzia** menu, kliknij przycisk **opcje**. W **opcje** okno dialogowe, kliknij przycisk **projekty i rozwiązania** węzeł, a następnie kliknij przycisk **skompilować i uruchomić** węzła. Następnie w **szczegółowości dziennika kompilacji MSBuild projektu w pliku** kliknij **szczegółowy**.  
  
-   Sprawdź, czy wartości dowolnego pliku nazwę lub katalogu makra używanego. Makra można echo indywidualnie lub dodać `copy %0 command.bat` do uruchomienia z niestandardowego kroku kompilacji, który skopiuje poleceń użytkownika niestandardowego kroku kompilacji dla command.bat z wszystkie makra rozwinięty.  
  
-   Uruchom niestandardowe kroki procesu kompilacji i zdarzenia pojedynczo, aby sprawdzić ich zachowanie kompilacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Ogólne informacje o niestandardowych krokach budowania lub zdarzeniach kompilacji](../ide/understanding-custom-build-steps-and-build-events.md)