---
title: Oczyszczanie zasobów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- termination handlers [C++], cleaning up resources
- exception handling [C++], cleaning up resources
- C++ exception handling, termination handlers
- resources [C++], cleaning up
- exception handling [C++], cleanup code
- try-catch keyword [C++], termination handlers
ms.assetid: 65753efe-6a27-4750-b90c-50635775c1b6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1c7c589f5ac6baef0ef4420d997fa6497f4e03d5
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39408510"
---
# <a name="cleaning-up-resources"></a>Oczyszczanie zasobów
Podczas wykonywania programu obsługi zakończenia może nie wiedzieć, które zasoby są przydzielane faktycznie, zanim został wywołany program obsługi przerwania. Istnieje możliwość, że **__try** blok instrukcji zostało przerwane przed wszystkie zasoby przydzielone, tak, aby nie wszystkie zasoby zostały otwarte.  
  
 W związku z tym aby zapewnić bezpieczne, należy sprawdzić aby zobaczyć, jakie zasoby są faktycznie otwarte przed kontynuowaniem oczyszczania obsługę przerwania. Jest zalecaną procedurą:  
  
1.  Inicjowanie dojścia do wartości NULL.  
  
2.  W **__try** instrukcji zablokować, przydzielania zasobów. Uchwyty są ustawione na wartości dodatnich, zasób jest przydzielony.  
  
3.  W **__finally** blok instrukcji wersji każdego zasobu, którego odpowiednie dojścia lub zmiennej flaga jest różna od zera lub not NULL.  
  
## <a name="example"></a>Przykład  
 Na przykład w poniższym kodzie użyto programu obsługi zakończenia Zamknij trzy pliki i blok pamięci, która została przydzielona w **__try** blok instrukcji. Przed Oczyszczanie zasobu, kod najpierw sprawdza, jeśli zasób został przydzielony.  
  
```cpp 
// exceptions_Cleaning_up_Resources.cpp  
#include <stdlib.h>  
#include <malloc.h>  
#include <stdio.h>  
#include <windows.h>  
  
void fileOps() {  
   FILE  *fp1 = NULL,  
         *fp2 = NULL,  
         *fp3 = NULL;  
   LPVOID lpvoid = NULL;  
   errno_t err;  
  
   __try {  
      lpvoid = malloc( BUFSIZ );  
  
      err = fopen_s(&fp1, "ADDRESS.DAT", "w+" );  
      err = fopen_s(&fp2, "NAMES.DAT", "w+" );  
      err = fopen_s(&fp3, "CARS.DAT", "w+" );  
   }  
   __finally {  
      if ( fp1 )  
         fclose( fp1 );  
      if ( fp2 )  
         fclose( fp2 );  
      if ( fp3 )  
         fclose( fp3 );  
      if ( lpvoid )  
         free( lpvoid );  
   }  
}  
  
int main() {  
   fileOps();  
}  
```  
  
## <a name="see-also"></a>Zobacz także  
 [Pisanie programu obsługi zakończenia](../cpp/writing-a-termination-handler.md)   
 [Obsługa wyjątków strukturalnych (C/C++)](../cpp/structured-exception-handling-c-cpp.md)