---
title: Rozpoznawanie niejednoznacznych deklaracje (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 3d773ee7-bbea-47de-80c2-cb0a9d4ec0b9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 530111ee439a991201debab876d485a36b7f5ac5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="resolving-ambiguous-declarations-c"></a>Rozpoznawanie niejednoznacznych deklaracje (C++)
Aby wykonać jawne konwersje z jednego typu do innego, należy użyć rzutowania, określający nazwę odpowiedniego typu. Wynik rzutowania niektóre wpisz niejednoznaczności składni. Następujące rzutowanie typu stylu funkcji jest niejednoznaczny:  
  
```  
char *aName( String( s ) );  
```  
  
 Nie jest jasne, czy jest deklaracji funkcji lub deklaracji obiektu rzutowany jako inicjator funkcja stylu: można zadeklarować funkcji zwracającej typ **char \***  pobierającej jeden argument typu `String` , lub można zadeklarować obiektu `aName` i zainicjować go z wartością `s` Rzutowanie na typ `String`.  
  
 Jeśli deklaracji mogą zostać uwzględnione w deklaracji funkcji prawidłowe, będzie traktowane jako takie. Tylko wtedy, gdy nie może być deklaracji funkcji — to znaczy, jeśli jest nieprawidłowy — jest zbadane instrukcji, aby sprawdzić, czy jest rzutowanie typu stylu funkcji. W związku z tym kompilator uwzględnia instrukcji być deklaracji funkcji i ignoruje nawiasy, identyfikator `s`. Z drugiej strony, instrukcje:  
  
```  
char *aName( (String)s );  
```  
  
 and  
  
```  
char *aName = String( s );  
```  
  
 są wyraźnie deklaracje obiektów i zdefiniowanych przez użytkownika konwersja z typu `String` na typ **char \***  jest wywoływane w celu wykonania inicjowania `aName`.  
  
## <a name="see-also"></a>Zobacz też  
 