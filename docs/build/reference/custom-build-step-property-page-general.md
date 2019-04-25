---
title: 'Strona niestandardowy krok budowania właściwości: Ogólne'
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCustomBuildStep.AdditionalInputs
- VC.Project.VCCustomBuildStep.CustomBuildAfterTargets
- VC.Project.VCCustomBuildStep.CustomBuildBeforeTargets
- VC.Project.VCCustomBuildStep.Outputs
- VC.Project.VCCustomBuildStep.Message
- VC.Project.VCCustomBuildStep.Command
helpviewer_keywords:
- project properties, custom build step
- custom build step (general)
ms.assetid: bd319741-0491-46c4-a428-7c61b4b46a02
ms.openlocfilehash: 329923140cf5a8f05e5c032ddb9e25c0ea45ec2a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273082"
---
# <a name="custom-build-step-property-page-general"></a>Strona niestandardowy krok budowania właściwości: Ogólne

Dla każdej kombinacji konfiguracji projektu i platformy docelowej w projekcie można określić niestandardowy krok wykonywany podczas kompilacji projektu.

Wersja systemu Linux na tej stronie, zobacz [właściwości kroku kompilacji niestandardowy (Linux C++)](../../linux/prop-pages/custom-build-step-linux.md).

## <a name="uielement-list"></a>Lista elementów UI

- **Wiersz polecenia**

   Polecenie wykonywane przez krok niestandardowej kompilacji.

- **Opis**

   Komunikat, który jest wyświetlany podczas wykonywania kroku niestandardowej kompilacji.

- **Dane wyjściowe**

   Plik wyjściowy, generowany przez krok niestandardowej kompilacji. To ustawienie jest wymagane, aby kompilacje przyrostowe działały poprawnie.

- **Dodatkowe zależności**

   Rozdzielana średnikami lista wszelkich dodatkowych plików wejściowych dla kroku niestandardowej kompilacji.

- **Wykonaj po i wykonaj przed**

   Te opcje definiują, kiedy krok niestandardowej kompilacji jest uruchamiany w procesie kompilacji w stosunku do wymienionych celów. Najczęściej wymienione cele to BuildGenerateSources, BuildCompile i BuildLink, ponieważ stanowią one najważniejsze kroki procesu kompilacji. Inne często wymienione cele to Midl, CLCompile i Link.

- **Traktuj produkty wyjściowe jako zawartość**

   Ta opcja jest przydatna tylko dla aplikacji uniwersalnych platformy Windows lub Windows Phone, które obejmują wszystkie pliki zawartości w pakiecie .appx.

### <a name="to-specify-a-custom-build-step"></a>Aby określić krok niestandardowej kompilacji

1. Na pasku menu wybierz **projektu**, **właściwości**. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. W **stron właściwości** okno dialogowe, przejdź do **właściwości konfiguracji**, **niestandardowy krok budowania**, **ogólne** strony.

1. Zmodyfikuj ustawienia.

## <a name="see-also"></a>Zobacz także

[Dokumentacja strony właściwości projektu C++](property-pages-visual-cpp.md)
