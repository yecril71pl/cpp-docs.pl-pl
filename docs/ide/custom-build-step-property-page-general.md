---
title: 'Strona właściwości krok niestandardowej kompilacji: Ogólna | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCCustomBuildStep.AdditionalInputs
- VC.Project.VCCustomBuildStep.CustomBuildAfterTargets
- VC.Project.VCCustomBuildStep.CustomBuildBeforeTargets
- VC.Project.VCCustomBuildStep.Outputs
- VC.Project.VCCustomBuildStep.Message
- VC.Project.VCCustomBuildStep.Command
dev_langs:
- C++
helpviewer_keywords:
- project properties, custom build step
- custom build step (general)
ms.assetid: bd319741-0491-46c4-a428-7c61b4b46a02
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: df655f06d3b6d6b2b7b36f83f7c109adce758fef
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45721997"
---
# <a name="custom-build-step-property-page-general"></a>Strona właściwości Niestandardowy krok budowania: ogólne
Dla każdej kombinacji konfiguracji projektu i platformy docelowej w projekcie można określić niestandardowy krok wykonywany podczas kompilacji projektu.  

Wersja systemu Linux na tej stronie, zobacz [właściwości kroku kompilacji niestandardowy (Linux C++)](../linux/prop-pages/custom-build-step-linux.md).
  
## <a name="uielement-list"></a>Lista elementów UI  
- **Wiersz polecenia**

   Polecenie wykonywane przez krok niestandardowej kompilacji.  
  
- **Opis**

   Komunikat, który jest wyświetlany podczas wykonywania kroku niestandardowej kompilacji.  
  
- **dane wyjściowe**

   Plik wyjściowy, generowany przez krok niestandardowej kompilacji. To ustawienie jest wymagane, aby kompilacje przyrostowe działały poprawnie.  
  
- **Dodatkowe zależności**

   Rozdzielana średnikami lista wszelkich dodatkowych plików wejściowych dla kroku niestandardowej kompilacji.  
  
- **Wykonaj po i wykonaj przed**

   Te opcje definiują, kiedy krok niestandardowej kompilacji jest uruchamiany w procesie kompilacji w stosunku do wymienionych celów. Najczęściej wymienione cele to BuildGenerateSources, BuildCompile i BuildLink, ponieważ stanowią one najważniejsze kroki procesu kompilacji. Inne często wymienione cele to Midl, CLCompile i Link.  
  
- **Traktuj produkty wyjściowe jako zawartość**

   Ta opcja jest przydatna tylko dla aplikacji uniwersalnych platformy Windows lub Windows Phone, które obejmują wszystkie pliki zawartości w pakiecie .appx.  
  
### <a name="to-specify-a-custom-build-step"></a>Aby określić krok niestandardowej kompilacji  
  
1.  Na pasku menu wybierz **projektu**, **właściwości**. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../ide/working-with-project-properties.md).  
  
2.  W **stron właściwości** okno dialogowe, przejdź do **właściwości konfiguracji**, **niestandardowy krok budowania**, **ogólne** strony.  
  
3.  Zmodyfikuj ustawienia.  
  
## <a name="see-also"></a>Zobacz też  
 [Strony właściwości](../ide/property-pages-visual-cpp.md)