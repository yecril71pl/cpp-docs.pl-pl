---
title: Niedopełnienie wartości zmiennoprzecinkowych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 78af8016-643c-47db-b4f1-7f06cb4b243e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4ceaa41dcaca88c7857a03c16ccccabdba086fd0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32387827"
---
# <a name="underflow-of-floating-point-values"></a>Niedopełnienie wartości zmiennoprzecinkowych
**ANSI 4.5.1** ustawionego wyrażenie całkowite funkcje matematyce `errno` wartość makra `ERANGE` na niedopełnienie zakresu błędów  
  
 Niedomiar nie ustawia wyrażenie `errno` do `ERANGE`. Gdy zbliża się wartość zero, a ostatecznie niedopełnienie, wartość jest równa zero.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje bibliotek](../c-language/library-functions.md)