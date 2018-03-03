---
title: "Niedopełnienie wartości zmiennoprzecinkowych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 78af8016-643c-47db-b4f1-7f06cb4b243e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ecea42172ed285f24a22cba004fb156784483643
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="underflow-of-floating-point-values"></a>Niedopełnienie wartości zmiennoprzecinkowych
**ANSI 4.5.1** ustawionego wyrażenie całkowite funkcje matematyce `errno` wartość makra `ERANGE` na niedopełnienie zakresu błędów  
  
 Niedomiar nie ustawia wyrażenie `errno` do `ERANGE`. Gdy zbliża się wartość zero, a ostatecznie niedopełnienie, wartość jest równa zero.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje bibliotek](../c-language/library-functions.md)