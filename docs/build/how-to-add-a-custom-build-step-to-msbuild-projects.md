---
title: "Porady: Dodawanie niestandardowego kroku kompilacji do projektów MSBuild | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: msbuild.cpp.howto.addcustombuildstep
dev_langs: C++
helpviewer_keywords: 'msbuild (c++), howto: add a custom build step'
ms.assetid: a20a0c47-4df4-4754-a1f0-a94a99958916
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 436c4a7d2eb8c0b75891d7df670a7f30e900bd97
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-add-a-custom-build-step-to-msbuild-projects"></a>Porady: dodawanie niestandardowego kroku kompilacji do projektów MSBuild
Niestandardowego kroku kompilacji jest zdefiniowane przez użytkownika kroku kompilacji. Niestandardowego kroku kompilacji zachowuje się jak każdy inny *narzędzia polecenia* kroku, takie jak standardowe kroku narzędzie kompilacji lub łącza.  
  
 Określ niestandardowego kroku kompilacji w pliku projektu (.vcxproj). Krok można określić wiersza polecenia do wykonania żadnych dodatkowych danych lub plików wyjściowych i komunikat do wyświetlenia. Jeśli **MSBuild** Określa, że Twoje pliki wyjściowe są nieaktualne względem pliki danych wejściowych, wyświetli komunikat i wykonuje polecenie.  
  
 Aby określić lokalizację niestandardowej kompilacji kroku w sekwencji obiekty docelowe kompilacji, użyj jednej lub obu z `CustomBuildAfterTargets` i `CustomBuildBeforeTargets` elementów XML w pliku projektu. Na przykład można określić, czy niestandardowy krok kompilacji jest uruchamiana po elemencie docelowym narzędzie łącze i przed elementem docelowym narzędzia manifestu. Rzeczywisty zestaw dostępnych elementów docelowych zależy od określonej kompilacji.  
  
 Określ `CustomBuildBeforeTargets` elementu, aby wykonać niestandardowy krok kompilacji przed uruchomieniem określonej lokalizacji docelowej, `CustomBuildAfterTargets` elementu do wykonania tego kroku po uruchomieniu określonego elementu docelowego lub obu elementów do wykonania kroku między dwóch sąsiadujących ze sobą obiektów docelowych. Jeśli element nie jest określony, narzędzie niestandardowej kompilacji wykonuje się w lokalizacji domyślnej, czyli po **łącze** docelowej.  
  
 Niestandardowe kroki procesu kompilacji i niestandardowych narzędzi kompilacji współużytkują informacje określone w `CustomBuildBeforeTargets` i `CustomBuildAfterTargets` elementów XML. W związku z tym określanie elementów docelowych tylko raz w pliku projektu.  
  
### <a name="to-define-what-is-executed-by-the-custom-build-step"></a>Aby zdefiniować, co jest wykonywane przez niestandardowy krok kompilacji  
  
1.  Dodaj grupę właściwości do pliku projektu. W tej grupie właściwości określić polecenie, wejścia i wyjścia i komunikat, jak pokazano w poniższym przykładzie. W tym przykładzie tworzy plik cab z utworzonego w pliku main.cpp [wskazówki: przy użyciu programu MSBuild do tworzenia projektu Visual C++](../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md).  
  
    ```  
    <ItemDefinitionGroup>  
      <CustomBuildStep>  
        <Command>makecab.exe $(ProjectDir)main.cpp $(TargetName).cab</Command>  
        <Outputs>$(TargetName).cab</Outputs>  
        <Inputs>$(TargetFileName)</Inputs>  
      </CustomBuildStep>  
    </ItemDefinitionGroup>  
    ```  
  
### <a name="to-define-where-in-the-build-the-custom-build-step-will-execute"></a>Aby określić, gdzie w kompilacji niestandardowy krok kompilacji będzie wykonywał  
  
1.  Dodaj następujące grupy właściwości do pliku projektu. Można określić zarówno elementy docelowe, lub można pominąć jedną, jeśli chcesz niestandardowy krok do wykonania przed lub po określonej lokalizacji docelowej. Określa, że w tym przykładzie **MSBuild** przeprowadzić niestandardowy krok po kroku kompilacji, ale przed wykonaniem kroku łącza.  
  
    ```  
    <PropertyGroup>  
      <CustomBuildAfterTargets>ClCompile</CustomBuildAfterTargets>  
      <CustomBuildBeforeTargets>Link</CustomBuildBeforeTargets>  
    </PropertyGroup>  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki: Korzystanie z MSBuild do tworzenia projektu Visual C++](../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)   
 [Porady: Korzystanie ze zdarzeń kompilacji w projektach MSBuild](../build/how-to-use-build-events-in-msbuild-projects.md)   
 [Porady: Dodawanie niestandardowych narzędzi kompilacji do projektów MSBuild](../build/how-to-add-custom-build-tools-to-msbuild-projects.md)