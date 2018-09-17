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
ms.openlocfilehash: 4e06a2a545862c0fa9cfdcf6311334ecc86de2bf
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45714405"
---
# <a name="how-to-add-custom-build-tools-to-msbuild-projects"></a>Porady: dodawanie niestandardowych narzędzi kompilacji do projektów MSBuild

Niestandardowego narzędzia kompilacji jest narzędziem zdefiniowanych przez użytkownika, wiersz polecenia, który jest skojarzony z określonego pliku.

Dla danego pliku należy określić w pliku projektu (.vcxproj) w wierszu polecenia do wykonania, wszelkie dodatkowe dane wejściowe lub wyjściowe pliki i komunikat do wyświetlenia. Jeśli **MSBuild** Określa, że Twoje pliki wyjściowe są nieaktualne w odniesieniu do plików wejściowych, wyświetla komunikat o i uruchamia narzędzie wiersza polecenia.

Aby określić, kiedy wykonuje niestandardowego narzędzia kompilacji, użyj jedną lub obie `CustomBuildBeforeTargets` i `CustomBuildAfterTargets` elementy XML w pliku projektu. Na przykład określić, że Twojego niestandardowego narzędzia kompilacji uruchomienia po kompilator MIDL i przed kompilator C/C++. Określ `CustomBuildBeforeTargets` element do wykonania narzędzie przed uruchomieniem określonego celu; `CustomBuildAfterTargets` elementu do uruchomienia narzędzia po do określonego celu; lub oba te elementy, aby uruchomić narzędzie między wykonaniem dwa obiekty docelowe. Jeśli element nie jest określony, Twojego niestandardowego narzędzia kompilacji wykonuje się w lokalizacji domyślnej, czyli przed **MIDL** docelowej.

Niestandardowych krokach budowania lub niestandardowych narzędzi kompilacji udostępnianie informacji określonych w `CustomBuildBeforeTargets` i `CustomBuildAfterTargets` elementów XML. Określanie elementów docelowych jeden raz w pliku projektu.

### <a name="to-add-a-custom-build-tool"></a>Aby dodać niestandardowego narzędzia kompilacji

1. Dodaj grupy elementów do pliku projektu i Dodawanie elementu dla każdego pliku wejściowego. Określ polecenie, dodatkowe dane wejściowe, dane wyjściowe i wiadomość jako metadane elementu, jak pokazano poniżej. W tym przykładzie przyjęto założenie, że plik "faq.txt" istnieje w tym samym katalogu co projekt.

    ```
    <ItemGroup>
      <CustomBuild Include="faq.txt">
        <Message>Copying readme...</Message>
        <Command>copy %(Identity) $(OutDir)%(Identity)</Command>
        <Outputs>$(OutDir)%(Identity)</Outputs>
      </CustomBuild>
    </ItemGroup>
    ```

### <a name="to-define-where-in-the-build-the-custom-build-tools-will-execute"></a>Aby zdefiniować, gdzie w kompilacji niestandardowych narzędzi kompilacji będą wykonywane

1. Dodaj następujące grupy właściwości do pliku projektu. Należy określić co najmniej jednego obiektu docelowego, ale można pominąć drugi, jeśli interesuje Cię tylko o swojej krok kompilacji, wykonaj przed (lub po) określonego celu. W tym przykładzie przeprowadza się niestandardowy krok po kompilacji, ale przed połączeniem.

    ```
    <PropertyGroup>
      <CustomBuildAfterTargets>ClCompile</CustomBuildAfterTargets>
      <CustomBuildBeforeTargets>Link</CustomBuildBeforeTargets>
    </PropertyGroup>
    ```

## <a name="see-also"></a>Zobacz też

[Przewodnik: Korzystanie z MSBuild do tworzenia projektu Visual C++](../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)<br/>
[Instrukcje: korzystanie ze zdarzeń kompilacji w projektach MSBuild](../build/how-to-use-build-events-in-msbuild-projects.md)<br/>
[Instrukcje: dodawanie niestandardowego kroku kompilacji do projektów MSBuild](../build/how-to-add-a-custom-build-step-to-msbuild-projects.md)