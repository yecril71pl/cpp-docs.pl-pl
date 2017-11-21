---
title: -LINKERMEMBER | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /linkermember
dev_langs: C++
helpviewer_keywords:
- /LINKERMEMBER dumpbin option
- LINKERMEMBER dumpbin option
- -LINKERMEMBER dumpbin option
ms.assetid: c96868c1-d70e-4651-ae36-c55b58b16406
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1af5cf0f3304b77bf731a95f8fc771bf7010dfbc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="linkermember"></a>/LINKERMEMBER
```  
/LINKERMEMBER[:{1|2}]  
```  
  
## <a name="remarks"></a>Uwagi  
 Ta opcja powoduje wyświetlenie symbole publiczne zdefiniowane w bibliotece. Należy określić argument 1 do wyświetlenia symboli w kolejności obiektu, wraz z ich przesunięcia. Należy określić argument 2, aby wyświetlić przesunięcia i liczby indeksu obiektów, a następnie wyświetlić symbole w kolejności alfabetycznej, wraz z indeksu obiektu dla każdego. Aby uzyskać zarówno dane wyjściowe, należy określić /LINKERMEMBER bez argument liczbowy.  
  
 Tylko [/HEADERS](../../build/reference/headers.md) — opcja polecenia DUMPBIN jest dostępny do użytku na pliki tworzone z [/GL](../../build/reference/gl-whole-program-optimization.md) — opcja kompilatora.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje DUMPBIN](../../build/reference/dumpbin-options.md)