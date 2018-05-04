---
title: -HIGHENTROPYVA | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /HIGHENTROPYVA
dev_langs:
- C++
helpviewer_keywords:
- HIGHENTROPYVA editbin option
- -HIGHENTROPYVA editbin option
- /HIGHENTROPYVA editbin option
ms.assetid: ef4b7c63-440d-40ca-b39d-edefb3217505
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 122f524db9af10449ce809e5a8de78148d04d431
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
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