---
title: Reguły i ograniczenia dotyczące elementu dllimport-dllexport
ms.date: 11/04/2016
helpviewer_keywords:
- dllexport attribute [C++], limitations and rules
- dllimport attribute [C++], limitations and rules
- dllexport attribute [C++]
ms.assetid: 274b735f-ab9c-4b07-8d0e-fdb65d664634
ms.openlocfilehash: cc83a43fd09299710585fa104dbd4dc847036c68
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62158430"
---
# <a name="rules-and-limitations-for-dllimportdllexport"></a>Reguły i ograniczenia dotyczące atrybutów dllimport/dllexport

**Specyficzne dla firmy Microsoft**

- Jeśli deklarujesz funkcję bez atrybutu **dllimport** lub `dllexport` Attribute, funkcja nie jest uważana za część interfejsu dll. W związku z tym definicja funkcji musi być obecna w tym module lub w innym module tego samego programu. Aby uczynić funkcję części interfejsu DLL, należy zadeklarować definicję funkcji w innym module jako `dllexport`. W przeciwnym razie podczas kompilowania klienta zostanie wygenerowany błąd konsolidatora.

- Jeśli pojedynczy moduł w programie zawiera **dllimport** i `dllexport` deklaracje dla tej samej funkcji, `dllexport` atrybut ma pierwszeństwo przed atrybutem **dllimport** . Jest jednak generowane ostrzeżenie kompilatora. Przykład:

    ```
    #define DllImport   __declspec( dllimport )
    #define DllExport   __declspec( dllexport )

       DllImport void func1( void );
       DllExport void func1( void );   /* Warning; dllexport */
                                       /* takes precedence. */

    ```

- Nie można zainicjować statycznego wskaźnika danych przy użyciu adresu obiektu danych zadeklarowanego z atrybutem **dllimport** . Na przykład poniższy kod generuje błędy:

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

- Inicjowanie wskaźnika funkcji statycznej z adresem funkcji zadeklarowanej za pomocą elementu **dllimport** ustawia wskaźnik na adres biblioteki DLL import thunk (zastępczy kod, który przekazuje kontrolę do funkcji), a nie adres funkcji. To przypisanie nie generuje komunikatu o błędzie:

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

- Ponieważ program, który zawiera `dllexport` atrybut w deklaracji obiektu, musi podać definicję dla tego obiektu, można zainicjować globalny lub lokalny wskaźnik funkcji statycznej przy użyciu adresu `dllexport` funkcji. Analogicznie, można zainicjować globalny lub lokalny wskaźnik danych statycznych o adresie obiektu `dllexport` danych. Przykład:

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

## <a name="see-also"></a>Zobacz też

[Importowanie bibliotek DLL i eksportowanie funkcji](../c-language/dll-import-and-export-functions.md)
