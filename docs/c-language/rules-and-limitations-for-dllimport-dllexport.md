---
title: Reguły i ograniczenia dotyczące atrybutów dllimport / dllexport
ms.date: 11/04/2016
helpviewer_keywords:
- dllexport attribute [C++], limitations and rules
- dllimport attribute [C++], limitations and rules
- dllexport attribute [C++]
ms.assetid: 274b735f-ab9c-4b07-8d0e-fdb65d664634
ms.openlocfilehash: 123ccf583fe5e07d9f2610ec621b48d8a8c39be8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50622032"
---
# <a name="rules-and-limitations-for-dllimportdllexport"></a>Reguły i ograniczenia dotyczące atrybutów dllimport/dllexport

**Microsoft Specific**

- Jeśli deklarowana jest funkcja bez **dllimport** lub `dllexport` atrybutu, funkcja nie jest uważany za część interfejsu biblioteki DLL. W związku z tym definicji funkcji musi być obecny, w tym module lub w innym module tego samego programu. Aby funkcja częścią interfejsu biblioteki DLL, należy zadeklarować definicji funkcji w module jako `dllexport`. W przeciwnym razie zostanie wygenerowany błąd konsolidatora, gdy klient jest wbudowana.

- Jeśli zawiera pojedynczy moduł w programie **dllimport** i `dllexport` deklaracje dla tej samej funkcji `dllexport` atrybut ma pierwszeństwo przed **dllimport** atrybutu. Jednak kompilator wygeneruje ostrzeżenie. Na przykład:

    ```
    #define DllImport   __declspec( dllimport )
    #define DllExport   __declspec( dllexport )

       DllImport void func1( void );
       DllExport void func1( void );   /* Warning; dllexport */
                                       /* takes precedence. */

    ```

- Nie można zainicjować wskaźnik danych statycznych przy użyciu adresu obiektu danych zadeklarowane za pomocą **dllimport** atrybutu. Na przykład poniższy kod generuje błędy:

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

- Inicjowanie wskaźnik funkcję statyczną przy użyciu adresu funkcji zadeklarowanych za pomocą **dllimport** ustawia wskaźnik adres thunk importu biblioteki DLL (kod odcinek, który przekazuje sterowanie do funkcji), a nie na adres Funkcja. Tego przypisania nie generuje komunikat o błędzie:

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

- Ponieważ program, który zawiera `dllexport` atrybutu w deklaracji obiektu, należy podać definicję dla tego obiektu, można zainicjować wskaźnik statycznej funkcji globalnych lub lokalnych z adresem `dllexport` funkcji. Podobnie, można zainicjować wskaźnik globalnych lub lokalnych danych statycznych, adresem `dllexport` obiektu danych. Na przykład:

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

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Importowanie bibliotek DLL i eksportowanie funkcji](../c-language/dll-import-and-export-functions.md)