---
title: -HIGHENTROPYVA | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /HIGHENTROPYVA
dev_langs:
- C++
helpviewer_keywords:
- HIGHENTROPYVA editbin option
- -HIGHENTROPYVA editbin option
- /HIGHENTROPYVA editbin option
ms.assetid: ef4b7c63-440d-40ca-b39d-edefb3217505
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 36ca3ea93f494587663d863b1dc4646750d38e82
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="highentropyva"></a>/HIGHENTROPYVA
Określa, czy obrazu wykonywalnego obsługuje randomizacji układu przestrzeni adresowej 64-bitowych wysokiej entropii (ASLR).  
  
```  
  
/HIGHENTROPYVA[:NO]  
```  
  
## <a name="remarks"></a>Uwagi  
 Ta opcja modyfikuje nagłówka pliku dll lub plik .exe, aby wskazać, czy obsługiwane jest ASLR z 64-bitowych adresów. Gdy ta opcja jest ustawiona na plik wykonywalny i wszystkie moduły, w których zależy, systemu operacyjnego, który obsługuje 64-bitowych ASLR można rebase segmenty obrazu wykonywalnego w czasie ładowania przy użyciu losowego adresów w 64-bitowych wirtualnej przestrzeni adresowej. Ta przestrzeń adresowa dużych sprawia, że utrudnia osobie atakującej odgadnąć lokalizacji obszaru pamięci.  
  
 Domyślnie konsolidator ustawia tę opcję dla 64-bitowych obrazów wykonywalnych. Aby ustawić tę opcję, [/DYNAMICBASE](../../build/reference/dynamicbase.md) opcja musi mieć wartość.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje polecenia EDITBIN](../../build/reference/editbin-options.md)   
 [/ DYNAMICBASE](../../build/reference/dynamicbase.md)   
 [Poziom ochrony oprogramowania niezależnego dostawcy oprogramowania systemu Windows](http://msdn.microsoft.com/library/bb430720.aspx)