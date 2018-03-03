---
title: "Ostrzeżenie LNK4075 narzędzi konsolidatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK4075
dev_langs:
- C++
helpviewer_keywords:
- LNK4075
ms.assetid: f39ad3f9-c263-4cf0-9d70-259fc56ac96d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e8c3330e637ae0e0dce5e875fcc349c6deefcf27
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4075"></a>Ostrzeżenie LNK4075 narzędzi konsolidatora
ignorowanie opcja "1" z powodu specyfikacji "option2"  
  
 Druga opcja przesłania pierwszego.  
  
 Określono opcje konsolidatora wykluczają się wzajemnie.  Sprawdź, czy opcje konsolidatora.  Gdy są określone opcje konsolidatora zależy od sposobu tworzenia projektu.  
  
-   Jeśli tworzysz w środowisku programistycznym w strony właściwości konsolidatora dla projektu i zobacz, w którym określone obu opcji konsolidatora.  Zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md) Aby uzyskać więcej informacji.  
  
-   W przypadku tworzenia w wierszu polecenia, sprawdź podanych opcji konsolidatora istnieje.  
  
-   W przypadku tworzenia ze skryptami kompilacji, przejrzyj skryptach, aby zobaczyć, którym określone te opcje konsolidatora.  
  
 Jeśli okaże się, gdy są określone opcje wykluczają się wzajemnie konsolidatora, usuń jedną z opcji konsolidatora.  
  
 Oto kilka przykładów:  
  
-   Jeśli moduł został skompilowany z **/zi**, co oznacza — opcja konsolidatora wewnętrznego o nazwie/editandcontinue i moduł został skompilowany z /OPT:REF, / OPT: ICF lub/incremental: No, co oznacza nie/editandcontinue, zostanie Pobierz LNK4075.  Zobacz [/z7, / zi, /ZI (Format informacji debugowania)](../../build/reference/z7-zi-zi-debug-information-format.md) Aby uzyskać więcej informacji.