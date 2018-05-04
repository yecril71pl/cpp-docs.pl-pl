---
title: Znak sekwencji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 1e6961a9-150e-4c13-b427-9af4b6a1fb7a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 85cf817a4d50346b9d10a9a9d1bc27abb5904433
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="character-sequences"></a>Sekwencje znaków
**ANSI 3.8.2** mapowanie sekwencje znaków pliku źródłowego  
  
 Instrukcje preprocesora używać tego samego znaku ustawić jako instrukcji pliku źródłowego z powodu wyjątku, które sekwencjach specjalnych nie są obsługiwane.  
  
 W związku z tym aby określić ścieżkę do plików dołączanych, użyj tylko jeden ukośnik odwrotny:  
  
```  
#include "path1\path2\myfile"  
```  
  
 W kodu źródłowego wymagane są dwa razy:  
  
```  
fil = fopen( "path1\\path2\\myfile", "rt" );  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Dyrektywy przetwarzania wstępnego](../c-language/preprocessing-directives.md)