---
title: "Błąd narzędzi konsolidatora LNK2027 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK2027
dev_langs: C++
helpviewer_keywords: LNK2027
ms.assetid: e2f857a8-8e8a-4697-bbff-12ccb84a35c1
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b9cefb948ffd09421a6d4a9c1c540ef22f8736fc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-error-lnk2027"></a>Błąd narzędzi konsolidatora LNK2027
Moduł nierozpoznane odwołanie "module"  
  
 Plik przekazywane do konsolidatora ma zależność w module, który nie został określony z **/assemblymodule** ani przekazywane bezpośrednio do konsolidatora.  
  
 Aby rozwiązać LNK2027, wykonaj jedną z następujących czynności:  
  
-   Nie są przekazywane do konsolidatora plik z zależności modułu.  
  
-   Określ moduł **/assemblymodule**.  
  
-   Jeśli moduł jest bezpieczne modułu .netmodule, należy przekazać modułu bezpośrednio do konsolidatora.  
  
 Aby uzyskać więcej informacji, zobacz [/assemblymodule (Dodaj moduł MSIL do zestawu)](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md) i [modułu .netmodule pliki jako dane wejściowe konsolidatora](../../build/reference/netmodule-files-as-linker-input.md).