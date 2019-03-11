---
title: Używanie typów danych TCHAR.H z kodem _MBCS
ms.date: 11/04/2016
f1_keywords:
- tchar.h
- TCHAR
helpviewer_keywords:
- mapping generic-text
- generic-text data types [C++]
- generic-text mappings [C++]
- MBCS [C++], generic-text mappings
- TCHAR.H data types, mapping
- mappings [C++], TCHAR.H
ms.assetid: 298583c5-22c3-40f6-920e-9ec96d42abd8
ms.openlocfilehash: 62801cfc2386cf2aee7fd35a5e589d73b4f91918
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57742030"
---
# <a name="using-tcharh-data-types-with-mbcs-code"></a>Używanie typów danych TCHAR.H z kodem _MBCS

Gdy stała manifestu `_MBCS` jest zdefiniowany, danej procedury zwykłego tekstu mapuje do jednej z następujących rodzajów procedury:

- Procedury SBCS, która obsługuje wielobajtowych bajtów, znaków i ciągów, odpowiednio. W tym przypadku powinny być typu argumenty typu string `char*`. Na przykład `_tprintf` mapuje `printf`; argumentów ciągów `printf` typu `char*`. Jeśli używasz `_TCHAR` typ danych — zwykły tekst dla ciągu typy, typy formalnego i rzeczywistego parametru dla `printf` zgodny, ponieważ `_TCHAR*` mapuje `char*`.

- Procedury specyficzne dla MBCS. W tym przypadku powinny być typu argumenty typu string `unsigned char*`. Na przykład `_tcsrev` mapuje `_mbsrev`, który oczekuje, że i zwraca ciąg typu `unsigned char*`. Jeśli używasz `_TCHAR` ma typ danych — zwykły tekst dla swojego typu string jest potencjalny konflikt typu `_TCHAR` mapy na typ `char`.

Poniżej przedstawiono trzy rozwiązania do zapobiegania ten konflikt typu (i ostrzeżenia kompilatora C lub C++ błędy kompilatora, które umożliwiałyby):

- Użyj zachowania domyślnego. Tchar.h udostępnia prototypy procedur zwykłego tekstu dla procedur w bibliotekach wykonawczych, jak w poniższym przykładzie.

    ```cpp
    char * _tcsrev(char *);
    ```

   W przypadku domyślnej prototypu `_tcsrev` mapuje `_mbsrev` za pośrednictwem osadzony w Libc.lib. Spowoduje to zmianę typów `_mbsrev` parametry przychodzące i wychodzące zwracają wartość z `_TCHAR*` (czyli `char *`) do `unsigned char *`. Ta metoda zapewnia typ dopasowania, gdy używasz `_TCHAR`, ale jest stosunkowo niska z powodu obciążenie wywołania funkcji.

- Aby użyć funkcji wbudowanie, zawierające następującą instrukcję preprocesora w kodzie.

    ```cpp
    #define _USE_INLINING
    ```

   Ta metoda powoduje, że thunk funkcji wbudowanych, podany w pliku tchar.h procedury — zwykły tekst bezpośrednio mapować do odpowiedniej procedury MBCS. W poniższym fragmencie kodu z pliku tchar.h przykład jak to zrobić.

    ```cpp
    __inline char *_tcsrev(char *_s1)
    {return (char *)_mbsrev((unsigned char *)_s1);}
    ```

   Jeśli użyjesz wstawienia, zrównoważenia jest najlepszym rozwiązaniem, ponieważ gwarantuje to typ dopasowania i ma koszt nie dodatkowego czasu.

- Za pomocą bezpośredniego mapowania zawierające następującą instrukcję preprocesora w kodzie.

    ```cpp
    #define _MB_MAP_DIRECT
    ```

   To podejście oferuje szybkie alternatywna, jeśli nie mają być używane domyślne zachowanie lub nie można użyć ze śródwierszowaniem. Powoduje procedury zwykłego tekstu mają być mapowane przez makro bezpośrednio do wersji MBCS standardowego, jak w poniższym przykładzie z tchar.h.

    ```cpp
    #define _tcschr _mbschr
    ```

   W przypadku zastosowania tego podejścia musi być ostrożnym, aby zapewnić stosowanie typów danych odpowiednie argumenty typu string i zwracane wartości ciągu. Rzutowanie typów można użyć do zapewnienia odpowiedniego typu dopasowania lub skorzystać z `_TXCHAR` typu danych — zwykły tekst. `_TXCHAR` mapuje do typu **char** SBCS kodu, ale mapy na typ **unsigned char** MBCS kodu. Aby uzyskać więcej informacji na temat makra zwykłego tekstu, zobacz [mapowania typ ogólny-tekst](../c-runtime-library/generic-text-mappings.md) w *odwołanie do biblioteki wykonawczej*.

## <a name="see-also"></a>Zobacz także

[Mapowania typu ogólny-tekst w pliku tchar.h](../text/generic-text-mappings-in-tchar-h.md)
