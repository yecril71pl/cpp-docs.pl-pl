---
title: 'Porady: Dodawanie niestandardowych narzędzi kompilacji do projektów MSBuild | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- msbuild.cpp.howto.addcustombuildtools
dev_langs:
- C++
helpviewer_keywords:
- 'msbuild (c++), howto: add custom build tools'
ms.assetid: de03899a-371d-4396-9bf9-34f45a65e909
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3793e4223d00f219cc4f1d7b09e67453901bd6d1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368333"
---
# <a name="how-to-add-custom-build-tools-to-msbuild-projects"></a>Porady: dodawanie niestandardowych narzędzi kompilacji do projektów MSBuild
Narzędzie niestandardowej kompilacji to narzędzie wiersza polecenia, zdefiniowane przez użytkownika skojarzonego z określonego pliku.  
  
 Dla określonego pliku należy określić w pliku projektu (.vcxproj) w wierszu polecenia do wykonania żadnych dodatkowych danych lub pliki wyjściowe, komunikat do wyświetlenia. Jeśli **MSBuild** Określa, że Twoje pliki wyjściowe są nieaktualne względem pliki danych wejściowych, wyświetli komunikat i uruchamia narzędzie wiersza polecenia.  
  
 Aby określić, kiedy wykonuje niestandardowego narzędzia kompilacji, użyj jednej lub obu `CustomBuildBeforeTargets` i `CustomBuildAfterTargets` elementów XML w pliku projektu. Na przykład określić, że narzędzie niestandardowej kompilacji uruchomienia po kompilatora MIDL i przed kompilatora C/C++. Określ `CustomBuildBeforeTargets` elementu, aby wykonać narzędzie przed uruchomieniem określonego elementu docelowego; `CustomBuildAfterTargets` elementu do uruchomienia narzędzia po określonej lokalizacji docelowej; lub obu elementów, aby uruchomić narzędzie między wykonywania dwóch elementów docelowych. Jeśli element nie jest określony, narzędzie niestandardowej kompilacji wykonuje się w lokalizacji domyślnej, czyli przed **MIDL** docelowej.  
  
 Niestandardowe kroki procesu kompilacji i niestandardowych narzędzi kompilacji współużytkują informacje określone w `CustomBuildBeforeTargets` i `CustomBuildAfterTargets` elementów XML. Określ cele jeden raz w pliku projektu.  
  
### <a name="to-add-a-custom-build-tool"></a>Aby dodać niestandardowe narzędzie kompilacji  
  
1.  Dodaj grupy elementów do pliku projektu i Dodawanie elementu, dla każdego pliku wejściowego. Określ polecenie, dodatkowe dane wejściowe, dane wyjściowe i komunikat jako metadane elementu w sposób pokazany poniżej. W tym przykładzie przyjęto założenie, że plik "faq.txt" istnieje w tym samym katalogu co projektu.  
  
    ```  
    <ItemGroup>  
      <CustomBuild Include="faq.txt">  
        <Message>Copying readme...</Message>  
        <Command>copy %(Identity) $(OutDir)%(Identity)</Command>  
        <Outputs>$(OutDir)%(Identity)</Outputs>  
      </CustomBuild>  
    </ItemGroup>  
    ```  
  
### <a name="to-define-where-in-the-build-the-custom-build-tools-will-execute"></a>Aby określić, gdzie w kompilacji narzędzia niestandardowej kompilacji będą wykonywane  
  
1.  Dodaj następujące grupy właściwości do pliku projektu. Należy określić co najmniej jeden z celów, ale można pominąć innych, jeśli interesuje Cię tylko z kroku kompilacji wykonać przed (lub po) o określonej lokalizacji docelowej. W tym przykładzie przeprowadza niestandardowy krok po kompilacji, ale przed połączeniem.  
  
    ```  
    <PropertyGroup>  
      <CustomBuildAfterTargets>ClCompile</CustomBuildAfterTargets>  
      <CustomBuildBeforeTargets>Link</CustomBuildBeforeTargets>  
    </PropertyGroup>  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki: Korzystanie z MSBuild do tworzenia projektu Visual C++](../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)   
 [Porady: Korzystanie ze zdarzeń kompilacji w projektach MSBuild](../build/how-to-use-build-events-in-msbuild-projects.md)   
 [Instrukcje: dodawanie niestandardowego kroku kompilacji do projektów MSBuild](../build/how-to-add-a-custom-build-step-to-msbuild-projects.md)