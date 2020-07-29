---
title: Reguły i ograniczenia dotyczące elementu dllimport-dllexport
ms.date: 11/04/2016
helpviewer_keywords:
- dllexport attribute [C++], limitations and rules
- dllimport attribute [C++], limitations and rules
- dllexport attribute [C++]
ms.assetid: 274b735f-ab9c-4b07-8d0e-fdb65d664634
ms.openlocfilehash: c2f121d978962fe7fc03aa453fb0a16650aa2727
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220876"
---
# <a name="rules-and-limitations-for-dllimportdllexport"></a>Reguły i ograniczenia dotyczące atrybutów dllimport/dllexport

**Specyficzne dla firmy Microsoft**

- Jeśli deklarujesz funkcję bez **`dllimport`** `dllexport` atrybutu lub, funkcja nie jest uważana za część interfejsu dll. W związku z tym definicja funkcji musi być obecna w tym module lub w innym module tego samego programu. Aby uczynić funkcję części interfejsu DLL, należy zadeklarować definicję funkcji w innym module jako `dllexport` . W przeciwnym razie podczas kompilowania klienta zostanie wygenerowany błąd konsolidatora.

- Jeśli pojedynczy moduł w programie zawiera **`dllimport`** `dllexport` deklaracje dla tej samej funkcji, `dllexport` atrybut ma pierwszeństwo przed **`dllimport`** atrybutem. Jest jednak generowane ostrzeżenie kompilatora. Na przykład:

    ```
    #define DllImport   __declspec( dllimport )
    #define DllExport   __declspec( dllexport )

       DllImport void func1( void );
       DllExport void func1( void );   /* Warning; dllexport */
                                       /* takes precedence. */

    ```

- Nie można zainicjować statycznego wskaźnika danych z adresem obiektu danych zadeklarowanym za pomocą **`dllimport`** atrybutu. Na przykład poniższy kod generuje błędy:

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

- Inicjowanie wskaźnika funkcji statycznej przy użyciu adresu funkcji zadeklarowanej za pomocą **`dllimport`** ustawia wskaźnik na adres thunk importowania biblioteki DLL (zastępczy kod, który przekazuje kontrolę do funkcji), a nie adres funkcji. To przypisanie nie generuje komunikatu o błędzie:

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

- Ponieważ program, który zawiera `dllexport` atrybut w deklaracji obiektu, musi podać definicję dla tego obiektu, można zainicjować globalny lub lokalny wskaźnik funkcji statycznej przy użyciu adresu `dllexport` funkcji. Analogicznie, można zainicjować globalny lub lokalny wskaźnik danych statycznych o adresie `dllexport` obiektu danych. Na przykład:

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

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje importowania i eksportowania biblioteki DLL](../c-language/dll-import-and-export-functions.md)
