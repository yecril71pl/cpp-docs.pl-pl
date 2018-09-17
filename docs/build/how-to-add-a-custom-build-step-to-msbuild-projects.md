---
title: 'Porady: Dodawanie niestandardowego kroku kompilacji do projektów MSBuild | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- msbuild.cpp.howto.addcustombuildstep
dev_langs:
- C++
helpviewer_keywords:
- 'msbuild (c++), howto: add a custom build step'
ms.assetid: a20a0c47-4df4-4754-a1f0-a94a99958916
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ca8206024f4fbaf38b8161a9e12672782551db83
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45712182"
---
# <a name="how-to-add-a-custom-build-step-to-msbuild-projects"></a>Porady: dodawanie niestandardowego kroku kompilacji do projektów MSBuild

Krok niestandardowej kompilacji jest krokiem zdefiniowanych przez użytkownika w kompilacji. Niestandardowy krok kompilacji, który zachowuje się jak każdy inny *narzędzia poleceń* kroku, takie jak standardowy kroku narzędzie kompilacji lub łącza.

Określ niestandardowego kroku kompilacji w pliku projektu (.vcxproj). Ten krok można określić w wierszu polecenia wykonaj wszelkie dodatkowe dane wejściowe lub wyjściowe pliki i komunikat do wyświetlenia. Jeśli **MSBuild** Określa, że Twoje pliki wyjściowe są nieaktualne w odniesieniu do plików wejściowych, wyświetla komunikat i wykonuje polecenie.

Aby określić lokalizację kompilacji niestandardowej krok w sekwencji obiektów docelowych kompilacji, użyj jedną lub obie `CustomBuildAfterTargets` i `CustomBuildBeforeTargets` elementy XML w pliku projektu. Można na przykład określić, czy wykonywania kroku niestandardowej kompilacji, po cel narzędzia łącza, a przed docelowej narzędzia manifestu. Rzeczywisty zestaw dostępnych elementów docelowych zależy od konkretnej kompilacji.

Określ `CustomBuildBeforeTargets` elementu, aby wykonać krok niestandardowej kompilacji, przed uruchomieniem określonego celu, `CustomBuildAfterTargets` element do wykonania kroku po uruchomieniu dany element docelowy lub oba te elementy, które można wykonać kroku między dwa sąsiadujące elementy docelowe. Jeśli element nie jest określony, narzędzie niestandardowej kompilacji wykonuje w domyślnej lokalizacji, czyli po **łącze** docelowej.

Niestandardowych krokach budowania lub niestandardowych narzędzi kompilacji udostępnianie informacji określonych w `CustomBuildBeforeTargets` i `CustomBuildAfterTargets` elementów XML. W związku z tym określanie elementów docelowych tylko jeden raz w pliku projektu.

### <a name="to-define-what-is-executed-by-the-custom-build-step"></a>Aby zdefiniować, co to jest wykonywane przez krok niestandardowej kompilacji

1. Dodaj grupy właściwości do pliku projektu. W tej grupie właściwości określ polecenie, jego danych wejściowych i danych wyjściowych oraz wiadomość, jak pokazano w poniższym przykładzie. W tym przykładzie tworzy plik cab z pliku main.cpp został utworzony w [Instruktaż: przy użyciu programu MSBuild do tworzenia projektu Visual C++](../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md).

    ```
    <ItemDefinitionGroup>
      <CustomBuildStep>
        <Command>makecab.exe $(ProjectDir)main.cpp $(TargetName).cab</Command>
        <Outputs>$(TargetName).cab</Outputs>
        <Inputs>$(TargetFileName)</Inputs>
      </CustomBuildStep>
    </ItemDefinitionGroup>
    ```

### <a name="to-define-where-in-the-build-the-custom-build-step-will-execute"></a>Aby zdefiniować, gdzie w kompilacji niestandardowy krok kompilacji będzie wykonywał

1. Dodaj następujące grupy właściwości do pliku projektu. Można określić obu elementów docelowych, lub możesz jednym pominąć, jeśli po prostu chcesz niestandardowy krok do wykonania przed lub po określonej lokalizacji docelowej. W tym przykładzie informuje **MSBuild** przeprowadzić niestandardowy krok po kroku kompilacji, ale przed krokiem link.

    ```
    <PropertyGroup>
      <CustomBuildAfterTargets>ClCompile</CustomBuildAfterTargets>
      <CustomBuildBeforeTargets>Link</CustomBuildBeforeTargets>
    </PropertyGroup>
    ```

## <a name="see-also"></a>Zobacz też

[Przewodnik: Korzystanie z MSBuild do tworzenia projektu Visual C++](../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)<br/>
[Instrukcje: korzystanie ze zdarzeń kompilacji w projektach MSBuild](../build/how-to-use-build-events-in-msbuild-projects.md)<br/>
[Instrukcje: dodawanie niestandardowych narzędzi kompilacji do projektów MSBuild](../build/how-to-add-custom-build-tools-to-msbuild-projects.md)