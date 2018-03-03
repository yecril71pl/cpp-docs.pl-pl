---
title: Opis niestandardowe kroki procesu kompilacji lub zdarzeniach kompilacji | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- builds [C++], events
- custom build steps [C++], customizing builds
- events [C++], build
- custom build steps [C++]
- build steps [C++]
- build events [C++], order of events and build steps
- build steps [C++], build events
- builds [C++], custom build steps
ms.assetid: beb2f017-3e9f-4b2c-9b57-2572fd2628e4
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9abb7ff0b9a39656999e7a53b476056f7a5b1558
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="understanding-custom-build-steps-and-build-events"></a>Ogólne informacje o niestandardowych krokach kompilacji lub zdarzeniach kompilacji
Od środowiska programistycznego Visual C++, istnieją trzy podstawowe sposoby dostosowania procesu kompilacji:  
  
 **Niestandardowe kroki procesu kompilacji**  
 Niestandardowego kroku kompilacji jest skojarzony z projektem reguły kompilacji. Niestandardowego kroku kompilacji można określić wiersza polecenia do wykonania żadnych dodatkowych danych lub plików wyjściowych i komunikat do wyświetlenia. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie niestandardowego kroku kompilacji do projektów MSBuild](../build/how-to-add-a-custom-build-step-to-msbuild-projects.md).  
  
 **Niestandardowe narzędzia kompilacji**  
 Narzędzie niestandardowej kompilacji jest skojarzony z co najmniej jeden plik reguły kompilacji. Niestandardowego kroku kompilacji można przekazać pliki wejściowe do narzędzia niestandardowej kompilacji, co prowadzi do jednego lub więcej plików wyjściowych. Na przykład pliki pomocy w aplikacji MFC są tworzone za pomocą narzędzia kompilacji niestandardowej. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie niestandardowych narzędzi Build Tools do projektów MSBuild](../build/how-to-add-custom-build-tools-to-msbuild-projects.md) i [określenie niestandardowego narzędzia kompilacji](../ide/specifying-custom-build-tools.md).  
  
 **Zdarzenia kompilacji**  
 Zdarzenia kompilacji umożliwiają dostosowanie kompilacji projektu. Istnieją trzy zdarzenia kompilacji: *prekompilacyjnego*, *prekonsolidacyjnego*, i *postkompilacyjnego*. Zdarzenia kompilacji umożliwia określenie akcji na określony czas w procesie kompilacji. Na przykład można użyć zdarzenia kompilacji zarejestrować plik z **regsvr32.exe** po zakończeniu projektu budynku. Aby uzyskać więcej informacji, zobacz [określanie zdarzeń kompilacji](../ide/specifying-build-events.md).  
  
 [Rozwiązywanie problemów z dostosowaniami kompilacji](../ide/troubleshooting-build-customizations.md) może pomóc upewnić się, że Twoje niestandardowe kroki procesu kompilacji i działają zgodnie z oczekiwaniami zdarzenia kompilacji.  
  
 Format danych wyjściowych niestandardowego kroku kompilacji lub zdarzenia kompilacji także może zwiększyć użyteczność narzędzia. Aby uzyskać więcej informacji, zobacz [formatowanie danych wyjściowych niestandardowego kroku kompilacji lub zdarzenia kompilacji](../ide/formatting-the-output-of-a-custom-build-step-or-build-event.md).  
  
 Zdarzenia kompilacji i niestandardowej kompilacji kroki, uruchom w następującej kolejności wraz z innymi kroki procesu kompilacji:  
  
1.  Zdarzenia Prekompilacyjnego  
  
2.  Niestandardowa kompilacji narzędzia dla poszczególnych plików  
  
3.  MIDL  
  
4.  Kompilator zasobów  
  
5.  Kompilator C/C++  
  
6.  Pre-Link - Zdarzenie  
  
7.  Konsolidatora lub Bibliotekarza (zależnie od potrzeb)  
  
8.  Narzędzie manifestu  
  
9. BSCMake  
  
10. Niestandardowy krok kompilacji projektu  
  
11. Zdarzenie mające miejsce po kompilacji  
  
 `custom build step on the project` i `post-build event` Uruchom sekwencyjnie po wszystkich innych kompilacji przetwarza Zakończ.  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilowanie projektów C++ w programie Visual Studio](../ide/building-cpp-projects-in-visual-studio.md)   
 [Typowe makra dla poleceń kompilacji oraz właściwości](../ide/common-macros-for-build-commands-and-properties.md)   
 [Okno dialogowe narzędzie kolejność kompilacji](http://msdn.microsoft.com/en-us/6204c5b1-7ce9-4948-9ff6-0268642ee14c)