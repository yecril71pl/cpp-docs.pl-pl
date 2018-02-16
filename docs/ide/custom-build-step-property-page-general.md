---
title: "Strona właściwości kroku kompilacji niestandardowej: Ogólna | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2e57d6cf00843cd6604ef269235602ea1b5b5e9b
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="custom-build-step-property-page-general"></a>Strona właściwości Niestandardowy krok budowania: ogólne
Dla każdej kombinacji konfiguracji projektu i platformy docelowej w projekcie można określić niestandardowy krok wykonywany podczas kompilacji projektu.  

Dla wersji systemu Linux na tej stronie, zobacz [właściwości kroku kompilacji niestandardowej (Linux C++)](../linux/prop-pages/custom-build-step-linux.md).
  
## <a name="uielement-list"></a>Lista elementów UI  
 Wiersz polecenia  
 Polecenie wykonywane przez krok niestandardowej kompilacji.  
  
 **Opis**  
 Komunikat, który jest wyświetlany podczas wykonywania kroku niestandardowej kompilacji.  
  
 **dane wyjściowe**  
 Plik wyjściowy, generowany przez krok niestandardowej kompilacji. To ustawienie jest wymagane, aby kompilacje przyrostowe działały poprawnie.  
  
 Dodatkowe zależności  
 Rozdzielana średnikami lista wszelkich dodatkowych plików wejściowych dla kroku niestandardowej kompilacji.  
  
 Wykonanie i wykonać przed  
 Te opcje definiują, kiedy krok niestandardowej kompilacji jest uruchamiany w procesie kompilacji w stosunku do wymienionych celów. Najczęściej wymienione cele to BuildGenerateSources, BuildCompile i BuildLink, ponieważ stanowią one najważniejsze kroki procesu kompilacji. Inne często wymienione cele to Midl, CLCompile i Link.  
  
 Traktuj dane wyjściowe jako zawartość  
 Ta opcja jest znaczący tylko dla aplikacji platformy uniwersalnej systemu Windows lub Windows Phone, które zawiera wszystkie pliki zawartości w pakiecie .appx.  
  
### <a name="to-specify-a-custom-build-step"></a>Aby określić krok niestandardowej kompilacji  
  
1.  Na pasku menu wybierz **projektu**, **właściwości**. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../ide/working-with-project-properties.md).  
  
2.  W **strony właściwości** okno dialogowe, przejdź do **właściwości konfiguracji**, **niestandardowy krok kompilacji**, **ogólne** strony.  
  
3.  Zmodyfikuj ustawienia.  
  
## <a name="see-also"></a>Zobacz też  
 [Strony właściwości](../ide/property-pages-visual-cpp.md)