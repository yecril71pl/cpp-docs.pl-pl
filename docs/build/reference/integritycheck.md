---
title: -INTEGRITYCHECK | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /INTEGRITYCHECK
dev_langs: C++
helpviewer_keywords:
- -INTEGRITYCHECK editbin options
- /INTEGRITYCHECK editbin options
- INTEGRITYCHECK editbin options
ms.assetid: 2a293705-4396-421b-a5a5-693b4b867a85
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 20fa72f8cc2d12c719f0e50c250052a191b5ee81
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="integritycheck"></a>/INTEGRITYCHECK
Określa, że podpis cyfrowy obraz binarny, muszą zostać sprawdzone w czasie ładowania.  
  
```  
  
/INTEGRITYCHECK[:NO]  
```  
  
## <a name="remarks"></a>Uwagi  
 W nagłówku pliku DLL lub pliku wykonywalnego ta opcja umożliwia ustawienie Flaga, która wymaga sprawdzenia podpisu cyfrowego, przez Menedżera pamięci można załadować obrazu w systemie Windows. Wersje systemu Windows starszych niż Windows Vista zignorować tę flagę. Tę opcję należy wybrać dla 64-bitowych bibliotek DLL, zaimplementować kod trybu jądra, które jest zalecane w przypadku wszystkich sterowników urządzeń. Aby uzyskać więcej informacji, zobacz [wskazówki podpisywania kodu w trybie jądra](http://go.microsoft.com/fwlink/?linkid=237093) w witrynie MSDN.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje polecenia EDITBIN](../../build/reference/editbin-options.md)