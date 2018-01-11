---
title: -STACK | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /stack
dev_langs: C++
helpviewer_keywords:
- -STACK editbin option
- STACK editbin option
- stack, setting size
- /STACK editbin option
ms.assetid: a39bcff0-c945-4355-80cc-8e4f24a5f142
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 21438bf8f214c10525aa7e9a5829f835b8a33f2c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="stack"></a>/STACK
```  
/STACK:reserve[,commit]  
```  
  
## <a name="remarks"></a>Uwagi  
 Ta opcja umożliwia ustawienie rozmiaru stosu w bajtach i przyjmuje argumenty w notacji dziesiętnej lub języka C. Opcja /STACK ma zastosowanie tylko do pliku wykonywalnego.  
  
 *Zarezerwować* argument określa alokacji całkowita stosu w pamięci wirtualnej. Polecenia EDITBIN Zaokrągla wartość w górę określonej wartości najbliższej 4 bajty.  
  
 Opcjonalny `commit` argument podlega interpretacji przez system operacyjny. Windows NT, Windows 95 i Windows 98 `commit` określa ilość pamięci fizycznej do przydzielenia naraz. Zadeklarowanej pamięci wirtualnej spowoduje, że miejsca, które mają zostać zarezerwowane w pliku stronicowania. Wyższy `commit` wartość zaoszczędzić czas podczas aplikacji wymaga więcej miejsca na stosie, ale zwiększa wymagania dotyczące pamięci i prawdopodobnie czas uruchamiania.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje EDITBIN](../../build/reference/editbin-options.md)