---
title: Ogólne informacje o niestandardowych krokach kompilacji lub zdarzeniach kompilacji
ms.date: 11/04/2016
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
ms.openlocfilehash: fc12689148e3bf23c233e4656249625d1156f9a7
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59028509"
---
# <a name="understanding-custom-build-steps-and-build-events"></a>Ogólne informacje o niestandardowych krokach kompilacji lub zdarzeniach kompilacji

W środowisku programistycznym Visual C++, istnieją trzy podstawowe sposoby dostosowywania procesu kompilacji:

- **Niestandardowych kroków kompilacji**

   Krok niestandardowej kompilacji jest reguła kompilacji skojarzonej z projektem. Niestandardowy krok kompilacji, można określić w wierszu polecenia wykonaj wszelkie dodatkowe dane wejściowe lub wyjściowe pliki i komunikat do wyświetlenia. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie niestandardowego kroku kompilacji do projektów MSBuild](how-to-add-a-custom-build-step-to-msbuild-projects.md).

- **Custom Build Tools**

   Niestandardowego narzędzia kompilacji jest reguła kompilacji skojarzony z co najmniej jeden plik. Niestandardowy krok kompilacji można przekazać pliki wejściowe do niestandardowego narzędzia kompilacji, co skutkuje jeden lub więcej plików wyjściowych. Na przykład pliki pomocy w aplikacji MFC są tworzone za pomocą narzędzia kompilacji niestandardowej. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie niestandardowych narzędzi kompilacji do projektów MSBuild](how-to-add-custom-build-tools-to-msbuild-projects.md) i [Określanie niestandardowego narzędzia kompilacji](specifying-custom-build-tools.md).

- **Zdarzenia kompilacji**

   Zdarzenia kompilacji umożliwiają dostosowywanie kompilacji projektu. Istnieją trzy zdarzenia kompilacji: *prekompilacji*, *prekonsolidacyjnego*, i *postkompilacyjnego*. To zdarzenie kompilacji pozwala określić, aby dana akcja występowała w określonym czasie w procesie kompilacji. Na przykład można użyć zdarzenia kompilacji można zarejestrować plik z **regsvr32.exe** po projekcie zakończeniu kompilowania. Aby uzyskać więcej informacji, zobacz [określanie zdarzeń kompilacji](specifying-build-events.md).

[Rozwiązywanie problemów z dostosowaniami kompilacji](troubleshooting-build-customizations.md) może pomóc upewnić się, że Twoje niestandardowych kroków kompilacji i tworzyć zdarzenia, które działają zgodnie z oczekiwaniami.

Format danych wyjściowych niestandardowy krok kompilacji lub zdarzenia kompilacji można również zwiększyć użyteczność narzędzie. Aby uzyskać więcej informacji, zobacz [formatowanie danych wyjściowych niestandardowy krok budowania lub zdarzenia kompilacji](formatting-the-output-of-a-custom-build-step-or-build-event.md).

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

## <a name="in-this-section"></a>W tej sekcji

[Określanie niestandardowych narzędzi kompilacji](specifying-custom-build-tools.md)<br/>
[Określanie zdarzeń kompilacji](specifying-build-events.md)<br/>
[Rozwiązywanie problemów z dostosowaniami kompilacji](troubleshooting-build-customizations.md)<br/>
[Formatowanie danych wyjściowych niestandardowego kroku kompilacji lub zdarzenia kompilacji](formatting-the-output-of-a-custom-build-step-or-build-event.md)<br/>

## <a name="see-also"></a>Zobacz także

[Projekty programu Visual Studio — C++](creating-and-managing-visual-cpp-projects.md)<br>
[Typowe makra dla właściwości i poleceń kompilacji](reference/common-macros-for-build-commands-and-properties.md)
