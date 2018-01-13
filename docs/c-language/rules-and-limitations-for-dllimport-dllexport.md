---
title: "Reguły i ograniczenia dotyczące atrybutów dllimport i dllexport | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- dllexport attribute [C++], limitations and rules
- dllimport attribute [C++], limitations and rules
- dllexport attribute [C++]
ms.assetid: 274b735f-ab9c-4b07-8d0e-fdb65d664634
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 62b012f1ce81ffa30528d027e36b299e9e38d2f2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="rules-and-limitations-for-dllimportdllexport"></a>Reguły i ograniczenia dotyczące atrybutów dllimport/dllexport
**Dotyczące firmy Microsoft**  
  
-   W przypadku funkcji bez **dllimport** lub `dllexport` atrybutu, funkcja nie jest uważany za część interfejsu biblioteki DLL. W związku z tym definicji funkcji musi być obecne w module lub w innym module ten sam program. Aby funkcja część interfejsu biblioteki DLL, muszą deklarować definicji funkcji w module jako `dllexport`. W przeciwnym razie zostanie wygenerowany błąd konsolidatora, gdy klient jest wbudowana.  
  
-   Jeśli zawiera jeden moduł w programie **dllimport** i `dllexport` deklaracje dla tej samej funkcji `dllexport` atrybut ma pierwszeństwo przed **dllimport** atrybutu. Jednak generowania ostrzeżeń kompilatora. Na przykład:  
  
    ```  
    #define DllImport   __declspec( dllimport )  
    #define DllExport   __declspec( dllexport )  
  
       DllImport void func1( void );  
       DllExport void func1( void );   /* Warning; dllexport */  
                                       /* takes precedence. */  
  
    ```  
  
-   Nie można zainicjować danych statycznych wskaźnik adres obiektu danych zadeklarowana z **dllimport** atrybutu. Na przykład następujący kod generuje błędy:  
  
    ```  
    #define DllImport   __declspec( dllimport )  
    #define DllExport   __declspec( dllexport )  
  
       DllImport int i;  
       .  
       .  
       .  
       int *pi = &i;                           /* Error */  
  
       void func2()  
       {  
          static int *pi = &i;                   /* Error */  
       }  
  
    ```  
  
-   Inicjowanie wskaźnik statycznej funkcji z adresu funkcji zadeklarowana z **dllimport** ustawia wskaźnik do adresu thunk importu biblioteki DLL (Kod szczątkowy, przesyłania funkcji sterowania) zamiast adresu Funkcja. To przypisanie nie generuje komunikat o błędzie:  
  
    ```  
    #define DllImport   __declspec( dllimport )  
    #define DllExport   __declspec( dllexport )  
  
       DllImport void func1( void   
       .  
       .  
       .  
       static void ( *pf )( void ) = &func1;   /* No Error */  
  
       void func2()  
       {  
          static void ( *pf )( void ) = &func1;  /* No Error */  
       }  
  
    ```  
  
-   Ponieważ program, który obejmuje `dllexport` atrybutu w deklaracji obiektu musi podać definicję dla tego obiektu, należy zainicjować wskaźnik statycznej funkcji globalnych lub lokalnych z adresem `dllexport` funkcji. Podobnie można zainicjować wskaźnik globalnych lub lokalnych danych statycznych adres `dllexport` obiektu danych. Na przykład:  
  
    ```  
    #define DllImport   __declspec( dllimport )  
    #define DllExport   __declspec( dllexport )  
  
       DllImport void func1( void );  
       DllImport int i;  
  
       DllExport void func1( void );  
       DllExport int i;  
       .  
       .  
       .  
       int *pi = &i;                            /* Okay */  
       static void ( *pf )( void ) = &func1;    /* Okay */  
  
       void func2()  
       {  
          static int *pi = i;                     /* Okay */  
          static void ( *pf )( void ) = &func1;   /* Okay */  
       }  
  
    ```  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Importowanie bibliotek DLL i eksportowanie funkcji](../c-language/dll-import-and-export-functions.md)