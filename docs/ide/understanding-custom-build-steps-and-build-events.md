---
title: Informacje o niestandardowych krokach budowania lub zdarzeniach kompilacji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6ce2390ac6e687600a06cba17a99a954e36e66ee
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45704928"
---
# <a name="understanding-custom-build-steps-and-build-events"></a>Ogólne informacje o niestandardowych krokach kompilacji lub zdarzeniach kompilacji
W środowisku programistycznym Visual C++, istnieją trzy podstawowe sposoby dostosowywania procesu kompilacji:  
  
- **Niestandardowych kroków kompilacji**

   Krok niestandardowej kompilacji jest reguła kompilacji skojarzonej z projektem. Niestandardowy krok kompilacji, można określić w wierszu polecenia wykonaj wszelkie dodatkowe dane wejściowe lub wyjściowe pliki i komunikat do wyświetlenia. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie niestandardowego kroku kompilacji do projektów MSBuild](../build/how-to-add-a-custom-build-step-to-msbuild-projects.md).  
  
- **Niestandardowe narzędzia kompilacji**

   Niestandardowego narzędzia kompilacji jest reguła kompilacji skojarzony z co najmniej jeden plik. Niestandardowy krok kompilacji można przekazać pliki wejściowe do niestandardowego narzędzia kompilacji, co skutkuje jeden lub więcej plików wyjściowych. Na przykład pliki pomocy w aplikacji MFC są tworzone za pomocą narzędzia kompilacji niestandardowej. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie niestandardowych narzędzi Build Tools do projektów MSBuild](../build/how-to-add-custom-build-tools-to-msbuild-projects.md) i [Określanie niestandardowego narzędzia kompilacji](../ide/specifying-custom-build-tools.md).  
  
- **Zdarzenia kompilacji**

   Zdarzenia kompilacji umożliwiają dostosowywanie kompilacji projektu. Istnieją trzy zdarzenia kompilacji: *prekompilacji*, *prekonsolidacyjnego*, i *postkompilacyjnego*. To zdarzenie kompilacji pozwala określić, aby dana akcja występowała w określonym czasie w procesie kompilacji. Na przykład można użyć zdarzenia kompilacji można zarejestrować plik z **regsvr32.exe** po projekcie zakończeniu kompilowania. Aby uzyskać więcej informacji, zobacz [określanie zdarzeń kompilacji](../ide/specifying-build-events.md).  
  
[Rozwiązywanie problemów z dostosowaniami kompilacji](../ide/troubleshooting-build-customizations.md) może pomóc upewnić się, że Twoje niestandardowych kroków kompilacji i tworzyć zdarzenia, które działają zgodnie z oczekiwaniami.  
  
Format danych wyjściowych niestandardowy krok kompilacji lub zdarzenia kompilacji można również zwiększyć użyteczność narzędzie. Aby uzyskać więcej informacji, zobacz [formatowanie danych wyjściowych niestandardowy krok budowania lub zdarzenia kompilacji](../ide/formatting-the-output-of-a-custom-build-step-or-build-event.md).  
  
Zdarzenia kompilacji i niestandardowe tworzenie kroki uruchamiane w następującej kolejności wraz z innych kroków kompilacji:  
  
1. Zdarzenie sprzed kompilacji  
  
2. Narzędzia dla poszczególnych plików do kompilacji niestandardowe  
  
3. MIDL  
  
4. Kompilator zasobów  
  
5. Kompilator C/C++  
  
6. Pre-Link - Zdarzenie  
  
7. Konsolidator lub Bibliotekarza (odpowiednio)  
  
8. Narzędzie manifestu  
  
9. BSCMake  
  
10. Niestandardowy krok kompilacji projektu  
  
11. Zdarzenie po kompilacji  
  
`custom build step on the project` i `post-build event` wykonywania sekwencyjnego, po wszystkich innych kompilacji przetwarza Zakończ.  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilowanie projektów C++ w programie Visual Studio](../ide/building-cpp-projects-in-visual-studio.md)   
 [Typowe makra dla właściwości i poleceń kompilacji](../ide/common-macros-for-build-commands-and-properties.md)   
