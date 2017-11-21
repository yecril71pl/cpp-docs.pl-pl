---
title: "Nazwy środowiska | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 9af409a5-e724-465a-9a21-88d3586c2e92
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 819bb0395ed8a47c7da9df85d50cd26357c84422
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="environment-names"></a>Nazwy środowiska
**ANSI 4.10.4.4** zbiór nazwy środowiska, a także metoda zmieniania listy środowiska używane przez [getenv —](../c-runtime-library/reference/getenv-wgetenv.md) — funkcja  
  
 Zestaw nazw środowisko jest nieograniczona.  
  
 Aby zmienić zmienne środowiskowe z poziomu programu C, należy wywołać [_putenv —](../c-runtime-library/reference/putenv-wputenv.md) funkcji. Aby zmienić zmienne środowiskowe z wiersza polecenia w systemie Windows, użyj polecenia SET (na przykład USTAWIĆ LIB = D:\ BIBLIOTEKI).  
  
 Zmienne środowiskowe ustawić z poziomu programu C istnieje tylko tak długo, jak działa ich hosta kopia powłokę poleceń systemu operacyjnego (CMD. Plik EXE lub COMMAND.COM). Na przykład wiersza  
  
```  
system( SET LIB = D:\LIBS );  
```  
  
 może działać kopia powłokę poleceń (CMD. (EXE), wartość zmiennej środowiskowej LIB i powrócić do programu C, kończenie dodatkowej kopię CMD. WYWOŁANIE PLIKU EXE. Kończenie tej kopii CMD. EXE usuwa tymczasowej zmiennej środowiskowej LIB.  
  
 Podobnie, zmiany wprowadzone przez `_putenv` ostatniego działać tylko do momentu zakończenia programu.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje bibliotek](../c-language/library-functions.md)   
 [_putenv —, _wputenv —](../c-runtime-library/reference/putenv-wputenv.md)   
 [getenv —, _wgetenv —](../c-runtime-library/reference/getenv-wgetenv.md)