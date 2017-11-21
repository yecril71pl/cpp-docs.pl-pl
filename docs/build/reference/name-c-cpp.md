---
title: NAZWA (C/C++) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: name
dev_langs: C++
helpviewer_keywords: NAME .def file statement
ms.assetid: 5c9b6bd8-9275-46a5-afba-f17a5936dc26
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 46bbbef9df3f68f322196962042039b32b4e0113
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="name-cc"></a>NAZWA (C/C++)
Określa nazwę pliku wyjściowego głównego.  
  
```  
NAME [application][BASE=address]  
```  
  
## <a name="remarks"></a>Uwagi  
 Odpowiednik sposobem określania nazwy pliku wyjściowego jest z [/OUT](../../build/reference/out-output-file-name.md) — opcja konsolidatora i sposób, aby ustawić adres podstawowy równoważny jest [/BASE](../../build/reference/base-base-address.md) — opcja konsolidatora. Jeśli określono oba/OUT zastępuje **nazwa**.  
  
 W przypadku tworzenia biblioteki DLL, nazwa mają wpływ tylko na nazwę biblioteki DLL.  
  
## <a name="see-also"></a>Zobacz też  
 [Zasady dla instrukcji definicji modułu](../../build/reference/rules-for-module-definition-statements.md)