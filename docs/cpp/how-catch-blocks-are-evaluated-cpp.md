---
title: Jak bloków Catch są oceniane (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- try-catch keyword [C++], catchable types
- catch keyword [C++], types of catch handlers
- C++ exception handling, catch handlers
- exception handling, catching and deleting exceptions
- types [C++], exception handling
ms.assetid: 202dbf07-8ace-4b3b-b3ae-4b45c275e0b4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0190b62491dbb9d15ee4f01a1cbc4c2741f74dbe
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947951"
---
# <a name="how-catch-blocks-are-evaluated-c"></a>Sposób oceniania bloków Catch (C++)
C++ umożliwia wyrzucanie wyjątków dowolnego typu, jednak ogólnie zaleca się wyrzucanie typów, który pochodzą od std::exception. Wyjątek C++ może zostać przechwycony przez **catch** program obsługi, który określa ten sam typ co Wyrzucony wyjątek lub przez program obsługi, który może przechwycić wyjątek dowolnego typu.  
  
 Jeśli typ wyrzuconego wyjątku to klasa, która posiada również klasę bazową (lub klasy) wyjątek może zostać przechwycony przez program obsługi, który akceptuje klasy bazowe typu wyjątku, jak również odwołania do klasy bazowej typu wyjątku. Należy zauważyć, że gdy wyjątek zostaje przechwycony przez odwołanie, następuje jego powiązanie z rzeczywistym wyrzuconym obiektem wyjątku; w przeciwnym razie jest kopią (prawie tak samo jak argument do funkcji).  
  
 Gdy wyjątek jest generowany, może zostać przechwycony przez następujące typy **catch** programów obsługi:  
  
-   Program obsługi, który może akceptować dowolny typ (przy użyciu składni wielokropka).  
  
-   Program obsługi, który akceptuje tego samego typu co obiekt wyjątku; ponieważ jest to kopia **const** i **volatile** Modyfikatory są ignorowane.  
  
-   Program obsługi, który akceptuje odwołanie do tego samego typu co obiekt wyjątku.  
  
-   Program obsługi, który akceptuje odwołanie do **const** lub **volatile** formularza tego samego typu co obiekt wyjątku.  
  
-   Program obsługi, który akceptuje klasę bazową tego samego typu co obiekt wyjątku; ponieważ jest to kopia **const** i **volatile** Modyfikatory są ignorowane. **Catch** obsługi dla klasy bazowej nie może poprzedzać **catch** obsługi dla klasy pochodnej.  
  
-   Program obsługi, który akceptuje odwołanie do klasy bazowej tego samego typu co obiekt wyjątku.  
  
-   Program obsługi, który akceptuje odwołanie do **const** lub **volatile** formularza klasy bazowej tego samego typu co obiekt wyjątku.  
  
-   Program obsługi, który akceptuje wskaźnik, do którego można przekonwertować wyrzucony obiekt wskaźnika za pomocą standardowych reguł konwersji wskaźnika.  
  
 Kolejność, w której **catch** pojawiają się programy obsługi jest ważna, ponieważ programy obsługi dla danego **spróbuj** bloku są badane w kolejności ich występowania. Na przykład, błędem jest umieszczenie programu obsługi dla klasy bazowej przed programem obsługi dla klasy pochodnej. Po pasujący obiekt typu **catch** program obsługi zostanie znaleziony, kolejne programy obsługi nie będą badane. Dzięki temu usługa wielokropek **catch** obsługi musi być ostatnim programem obsługi dla jego **spróbuj** bloku. Na przykład:  
  
```cpp 
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
  
 W tym przykładzie wielokropka **catch** program obsługi jest tylko program obsługi, który jest sprawdzany pod.  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa wyjątków języka C++](../cpp/cpp-exception-handling.md)