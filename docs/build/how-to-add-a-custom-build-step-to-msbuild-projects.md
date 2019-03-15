---
title: 'Instrukcje: Dodawanie niestandardowego kroku kompilacji do projektów MSBuild'
ms.date: 11/04/2016
f1_keywords:
- msbuild.cpp.howto.addcustombuildstep
helpviewer_keywords:
- 'msbuild (c++), howto: add a custom build step'
ms.assetid: a20a0c47-4df4-4754-a1f0-a94a99958916
ms.openlocfilehash: 4c64c6875d82000d6a0ac880b103b5e220015cb3
ms.sourcegitcommit: faa42c8a051e746d99dcebe70fd4bbaf3b023ace
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2019
ms.locfileid: "57814010"
---
# <a name="how-to-add-a-custom-build-step-to-msbuild-projects"></a>Instrukcje: Dodawanie niestandardowego kroku kompilacji do projektów MSBuild

Krok niestandardowej kompilacji jest krokiem zdefiniowanych przez użytkownika w kompilacji. Niestandardowy krok kompilacji, który zachowuje się jak każdy inny *narzędzia poleceń* kroku, takie jak standardowy kroku narzędzie kompilacji lub łącza.

Określ niestandardowego kroku kompilacji w pliku projektu (.vcxproj). Ten krok można określić w wierszu polecenia wykonaj wszelkie dodatkowe dane wejściowe lub wyjściowe pliki i komunikat do wyświetlenia. Jeśli **MSBuild** Określa, że Twoje pliki wyjściowe są nieaktualne w odniesieniu do plików wejściowych, wyświetla komunikat i wykonuje polecenie.

Aby określić lokalizację kompilacji niestandardowej krok w sekwencji obiektów docelowych kompilacji, użyj jedną lub obie `CustomBuildAfterTargets` i `CustomBuildBeforeTargets` elementy XML w pliku projektu. Można na przykład określić, czy wykonywania kroku niestandardowej kompilacji, po cel narzędzia łącza, a przed docelowej narzędzia manifestu. Rzeczywisty zestaw dostępnych elementów docelowych zależy od konkretnej kompilacji.

Określ `CustomBuildBeforeTargets` elementu, aby wykonać krok niestandardowej kompilacji, przed uruchomieniem określonego celu, `CustomBuildAfterTargets` element do wykonania kroku po uruchomieniu dany element docelowy lub oba te elementy, które można wykonać kroku między dwa sąsiadujące elementy docelowe. Jeśli element nie jest określony, narzędzie niestandardowej kompilacji wykonuje w domyślnej lokalizacji, czyli po **łącze** docelowej.

Niestandardowych krokach budowania lub niestandardowych narzędzi kompilacji udostępnianie informacji określonych w `CustomBuildBeforeTargets` i `CustomBuildAfterTargets` elementów XML. W związku z tym określanie elementów docelowych tylko jeden raz w pliku projektu.

### <a name="to-define-what-is-executed-by-the-custom-build-step"></a>Aby zdefiniować, co to jest wykonywane przez krok niestandardowej kompilacji

1. Dodaj grupy właściwości do pliku projektu. W tej grupie właściwości określ polecenie, jego danych wejściowych i danych wyjściowych oraz wiadomość, jak pokazano w poniższym przykładzie. W tym przykładzie tworzy plik cab z pliku main.cpp został utworzony w [instruktażu: Korzystanie z MSBuild do tworzenia projektu Visual C++](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md).

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

## <a name="see-also"></a>Zobacz także

[Przewodnik: korzystanie z MSBuild do tworzenia projektu Visual C++](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)<br/>
[Instrukcje: korzystanie ze zdarzeń kompilacji w projektach MSBuild](how-to-use-build-events-in-msbuild-projects.md)<br/>
[Instrukcje: dodawanie niestandardowych narzędzi kompilacji do projektów MSBuild](how-to-add-custom-build-tools-to-msbuild-projects.md)
