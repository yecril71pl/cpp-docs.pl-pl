---
title: "Zwalnianie bibliotek DLL załadowanych z opóźnieniem | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- __FUnloadDelayLoadedDLL2
- delayed loading of DLLs, unloading
ms.assetid: 6463bc71-020e-4aff-a4ca-90360411c54e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8b47969da4c560f28c07ac09caef83873e362ddc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="unloading-a-delay-loaded-dll"></a>Zwalnianie bibliotek DLL załadowanych z opóźnieniem
Pomocnika dostarczony domyślne załadować z opóźnieniem sprawdza, czy deskryptory załadować z opóźnieniem są wskaźnik i kopię oryginalnej tabelę adresów importu (IAT) w polu pUnloadIAT. Jeśli tak, zapisze wskaźnik na liście do deskryptora opóźnienia importowania. Dzięki temu funkcja pomocnika można znaleźć biblioteki DLL według nazwy do obsługi jawne zwalnianie tej biblioteki DLL.  
  
 W tym miejscu są skojarzone struktury oraz funkcje dla jawne zwalnianie bibliotek DLL załadowanych z opóźnieniem:  
  
```  
//  
// Unload support from delayimp.h  
//  
  
// routine definition; takes a pointer to a name to unload  
  
ExternC  
BOOL WINAPI  
__FUnloadDelayLoadedDLL2(LPCSTR szDll);  
  
// structure definitions for the list of unload records  
typedef struct UnloadInfo * PUnloadInfo;  
typedef struct UnloadInfo {  
    PUnloadInfo     puiNext;  
    PCImgDelayDescr pidd;  
    } UnloadInfo;  
  
// from delayhlp.cpp  
// the default delay load helper places the unloadinfo records in the   
// list headed by the following pointer.  
ExternC  
PUnloadInfo __puiHead;  
```  
  
 Struktura UnloadInfo jest implementowane za pomocą klasy C++, która używa **Funkcja LocalAlloc** i **LocalFree** implementacji jako jego operatora **nowe** i operatora  **Usuń** odpowiednio. Te opcje są przechowywane w standardowe połączonej listy przy użyciu __puiHead kierownikiem listy.  
  
 Wywołanie __FUnloadDelayLoadedDLL będzie podejmować próby wyszukania nazwy Podaj na liście ładowanych bibliotek DLL (wymagana jest dokładne dopasowanie). Jeśli znaleziono kopię IAT w pUnloadIAT jest kopiowana za pośrednictwem początku uruchomionych IAT do przywrócenia wskaźniki thunk biblioteki zostanie zwolniona z **FreeLibrary**, dopasowywania **UnloadInfo** rekord jest rozłączony z listy i usunięta, a wartość TRUE, jest zwracany.  
  
 Argument funkcji __FUnloadDelayLoadedDLL2 jest rozróżniana wielkość liter. Na przykład określ:  
  
```  
__FUnloadDelayLoadedDLL2("user32.DLL");  
```  
  
 a nie:  
  
```  
__FUnloadDelayLoadedDLL2("User32.DLL");.  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Ogólne informacje funkcji Pomocnik](understanding-the-helper-function.md)