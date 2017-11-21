---
title: Znak sekwencji | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 1e6961a9-150e-4c13-b427-9af4b6a1fb7a
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c097f213d790a992d12a8c358282a5340fce52c4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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