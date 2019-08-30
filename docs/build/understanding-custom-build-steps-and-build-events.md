---
title: Ogólne informacje o niestandardowych krokach kompilacji lub zdarzeniach kompilacji
ms.date: 08/29/2019
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
ms.openlocfilehash: 386a12213814e3825ece8a81d61ac251c6793f43
ms.sourcegitcommit: e10a5feea193c249ddc5a6faba48e7c6d8784e73
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2019
ms.locfileid: "70177314"
---
# <a name="understanding-custom-build-steps-and-build-events"></a>Ogólne informacje o niestandardowych krokach kompilacji lub zdarzeniach kompilacji

W środowisku deweloperskim C++ wizualizacji istnieją trzy podstawowe sposoby dostosowywania procesu kompilacji:

- **Niestandardowe kroki kompilacji**

   Niestandardowy krok kompilacji jest regułą kompilacji skojarzoną z projektem. Niestandardowy krok kompilacji może określać wiersz poleceń do wykonania, wszelkie dodatkowe pliki wejściowe lub wyjściowe oraz komunikat do wyświetlenia. Aby uzyskać więcej informacji, zobacz [jak: Dodaj niestandardowy krok kompilacji do projektów](how-to-add-a-custom-build-step-to-msbuild-projects.md)MSBuild.

- **Niestandardowe narzędzia kompilacji**

   Niestandardowe narzędzie kompilacji jest regułą kompilacji skojarzoną z co najmniej jednym plikami. Niestandardowy krok kompilacji umożliwia przekazywanie plików wejściowych do niestandardowego narzędzia kompilacji, co powoduje utworzenie co najmniej jednego pliku wyjściowego. Na przykład pliki pomocy w aplikacji MFC są kompilowane za pomocą niestandardowego narzędzia kompilacji. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie niestandardowych narzędzi kompilacji do projektów](how-to-add-custom-build-tools-to-msbuild-projects.md) programu MSBuild i [Określanie niestandardowych narzędzi kompilacji](specifying-custom-build-tools.md).

- **Zdarzenia kompilacji**

   Zdarzenia kompilacji pozwalają dostosować kompilację projektu. Istnieją trzy zdarzenia kompilacji: *przed kompilacją*, *przed połączeniem*i *po kompilacji*. Zdarzenie kompilacji pozwala określić akcję, która ma być wykonywana w określonym czasie w procesie kompilacji. Można na przykład użyć zdarzenia kompilacji do zarejestrowania pliku z **regsvr32. exe** po zakończeniu kompilowania projektu. Aby uzyskać więcej informacji, zobacz [Określanie zdarzeń kompilacji](specifying-build-events.md).

[Rozwiązania do rozwiązywania problemów z dostosowywaniem kompilacji](troubleshooting-build-customizations.md) mogą pomóc w upewnieniu się, że niestandardowe kroki kompilacji i zdarzenia kompilacji działają zgodnie z oczekiwaniami.

Format danych wyjściowych niestandardowego kroku kompilacji lub zdarzenia kompilacji może również zwiększyć użyteczność narzędzia. Aby uzyskać więcej informacji, zobacz [Formatowanie danych wyjściowych niestandardowego kroku kompilacji lub zdarzenia kompilacji](formatting-the-output-of-a-custom-build-step-or-build-event.md).

Dla każdego projektu w rozwiązaniu zdarzenia kompilacji i niestandardowe kroki kompilacji działają w następującej kolejności oraz w innych krokach kompilacji:

1. Zdarzenie sprzed kompilacji

2. Niestandardowe narzędzia kompilacji dla pojedynczych plików

3. MIDL

4. Kompilator zasobów

5. Kompilator C/C++

6. Pre-Link - Zdarzenie

7. Konsolidator lub bibliotekarza (odpowiednio)

8. Narzędzie manifestu

9. BSCMake

10. Niestandardowy krok kompilacji w projekcie

11. Zdarzenie po kompilacji

I a a `post-build event` działa sekwencyjnie po zakończeniu wszystkich pozostałych procesów kompilacji. `custom build step on the project`

## <a name="in-this-section"></a>W tej sekcji

[Określanie niestandardowych narzędzi kompilacji](specifying-custom-build-tools.md)<br/>
[Określanie zdarzeń kompilacji](specifying-build-events.md)<br/>
[Rozwiązywanie problemów z dostosowaniami kompilacji](troubleshooting-build-customizations.md)<br/>
[Formatowanie danych wyjściowych niestandardowego kroku kompilacji lub zdarzenia kompilacji](formatting-the-output-of-a-custom-build-step-or-build-event.md)

## <a name="see-also"></a>Zobacz także

[Projekty programu Visual Studio — C++](creating-and-managing-visual-cpp-projects.md)<br>
[Typowe makra dla właściwości i poleceń kompilacji](reference/common-macros-for-build-commands-and-properties.md)
