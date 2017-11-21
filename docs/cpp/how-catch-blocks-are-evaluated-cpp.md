---
title: "Jak bloków Catch są oceniane (C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- try-catch keyword [C++], catchable types
- catch keyword [C++], types of catch handlers
- C++ exception handling, catch handlers
- exception handling, catching and deleting exceptions
- types [C++], exception handling
ms.assetid: 202dbf07-8ace-4b3b-b3ae-4b45c275e0b4
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3af6c63ab571738f2c963c3e9b90b9aae4b644eb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="how-catch-blocks-are-evaluated-c"></a>Sposób oceniania bloków Catch (C++)
C++ umożliwia wyrzucanie wyjątków dowolnego typu, jednak ogólnie zaleca się wyrzucanie typów, który pochodzą od std::exception. Przechwycił wyjątek C++ **catch** obsługi, która określa tego samego typu, jako zwrócony wyjątek lub przez program obsługi, który można przechwycić dowolnego typu wyjątku.  
  
 Jeśli typ wyrzuconego wyjątku to klasa, która posiada również klasę podstawową (lub klasy) wyjątek może zostać przechwycony przez program obsługi, który akceptuje klasy podstawowe typu wyjątku, jak również odwołania do klasy podstawowej typu wyjątku. Należy zauważyć, że gdy wyjątek zostaje przechwycony przez odwołanie, następuje jego powiązanie z rzeczywistym wyrzuconym obiektem wyjątku; w przeciwnym razie jest kopią (prawie tak samo jak argument do funkcji).  
  
 Gdy jest zgłaszany wyjątek, może być przechwycony przez następujące typy **catch** programów obsługi:  
  
-   Program obsługi, który może akceptować dowolny typ (przy użyciu składni wielokropka).  
  
-   Program obsługi, który akceptuje tego samego typu co obiekt wyjątku; ponieważ to jest kopia do **const** i `volatile` Modyfikatory są ignorowane.  
  
-   Program obsługi, który akceptuje odwołanie do tego samego typu co obiekt wyjątku.  
  
-   Program obsługi, który przyjmuje odwołanie do **const** lub `volatile` formę tego samego typu co obiekt wyjątku.  
  
-   Program obsługi, który akceptuje klasę podstawową tego samego typu co obiekt wyjątku; ponieważ chodzi o kopiowanie przez **const** i `volatile` Modyfikatory są ignorowane. **Catch** obsługi dla klasy podstawowej nie musi poprzedzać **catch** obsługi dla klasy pochodnej.  
  
-   Program obsługi, który akceptuje odwołanie do klasy podstawowej tego samego typu co obiekt wyjątku.  
  
-   Program obsługi, który przyjmuje odwołanie do **const** lub `volatile` formularza z klasą podstawową dla tego samego typu co obiekt wyjątku.  
  
-   Program obsługi, który akceptuje wskaźnik, do którego można przekonwertować wyrzucony obiekt wskaźnika za pomocą standardowych reguł konwersji wskaźnika.  
  
 Kolejność **catch** obsługi są wyświetlane jest ważna, ponieważ programy obsługi dla danego **spróbuj** bloku są sprawdzane w kolejności ich wyglądu. Na przykład, błędem jest umieszczenie programu obsługi dla klasy podstawowej przed programem obsługi dla klasy pochodnej. Po odpowiadającego mu **catch** odnaleźć programu obsługi, kolejne obsługi nie są sprawdzane. Dzięki temu wielokropek **catch** Obsługa musi być ostatnim obsługi dla jego **spróbuj** bloku. Na przykład:  
  
```  
// ...  
try  
{  
    // ...  
}  
catch( ... )  
{  
    // Handle exception here.  
}  
// Error: the next two handlers are never examined.  
catch( const char * str )  
{  
    cout << "Caught exception: " << str << endl;  
}  
catch( CExcptClass E )  
{  
    // Handle CExcptClass exception here.  
}  
```  
  
 W tym przykładzie wielokropka **catch** program obsługi jest tylko program obsługi, która się zbadana.  
  
## <a name="see-also"></a>Zobacz też  
 [C++, obsługa wyjątków](../cpp/cpp-exception-handling.md)