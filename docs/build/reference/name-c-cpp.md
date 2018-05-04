---
title: NAZWA (C/C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- name
dev_langs:
- C++
helpviewer_keywords:
- NAME .def file statement
ms.assetid: 5c9b6bd8-9275-46a5-afba-f17a5936dc26
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a94b82a65cf68d9802d7bf9620e4128ab6b35071
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
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