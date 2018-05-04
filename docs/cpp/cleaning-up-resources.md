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
ms.openlocfilehash: 960e19400ae1d00108d57eb85d3df01ebf1dbc33
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="cleaning-up-resources"></a>Oczyszczanie zasobów
Podczas wykonywania programu obsługi zakończenia może nie wiedzieć, który faktycznie przydzielania zasobów przed programu obsługi zakończenia została wywołana. Istnieje możliwość, że `__try` blok instrukcji zostało przerwane przed wszystkie zasoby przydzielone, tak aby nie wszystkie zasoby zostały otwarte.  
  
 W związku z tym być bezpieczne, należy sprawdzić, zobacz zasoby są faktycznie otwarte przed rozpoczęciem oczyszczania obsługi zakończenia. Procedury zalecane jest:  
  
1.  Inicjowanie dojścia do wartości NULL.  
  
2.  W `__try` instrukcji bloków, przydzielanie zasobów. Uchwyty są ustawiane na wartości dodatnie zasobu jest przydzielony.  
  
3.  W `__finally` blok instrukcji, zwolnij każdy zasób, którego odpowiednie dojścia lub flagi zmiennej jest różna od zera lub not NULL.  
  
## <a name="example"></a>Przykład  
 Na przykład w poniższym kodzie użyto programu obsługi zakończenia, aby zamknąć trzy pliki i blok pamięci, która była przydzielona w `__try` blok instrukcji. Przed czyszczenie zasobu, kod najpierw sprawdza, jeśli zasób został przydzielony.  
  
```  
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
  
## <a name="see-also"></a>Zobacz też  
 [Pisanie programu obsługi zakończenia](../cpp/writing-a-termination-handler.md)   
 [Obsługa wyjątków strukturalnych (C/C++)](../cpp/structured-exception-handling-c-cpp.md)