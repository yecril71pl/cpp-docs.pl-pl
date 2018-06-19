---
title: Ostrzeżenie LNK4075 narzędzi konsolidatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4075
dev_langs:
- C++
helpviewer_keywords:
- LNK4075
ms.assetid: f39ad3f9-c263-4cf0-9d70-259fc56ac96d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4bd9a4ecdad30a0be2d45300367f6f79a65a6b31
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33301037"
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