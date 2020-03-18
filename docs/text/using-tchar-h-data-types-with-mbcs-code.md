---
title: Używanie typów danych TCHAR.H z kodem _MBCS
ms.date: 11/04/2016
helpviewer_keywords:
- mapping generic-text
- generic-text data types [C++]
- generic-text mappings [C++]
- MBCS [C++], generic-text mappings
- TCHAR.H data types, mapping
- mappings [C++], TCHAR.H
ms.assetid: 298583c5-22c3-40f6-920e-9ec96d42abd8
ms.openlocfilehash: 78e5d89e1e87d081e762fab1298eb990b914324c
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446594"
---
# <a name="using-tcharh-data-types-with-_mbcs-code"></a>Używanie typów danych TCHAR.H z kodem _MBCS

Gdy `_MBCS` jest zdefiniowana stała manifestu, dana procedura ogólna tekstu mapuje do jednego z następujących rodzajów procedur:

- Procedura SBCS, która obsługuje odpowiednio bajty wielobajtowe, znaki i ciągi. W takim przypadku argumenty ciągu powinny być typu `char*`. Na przykład `_tprintf` Maps `printf`; argumenty ciągu do `printf` są typu `char*`. Jeśli używasz typu danych `_TCHAR` Generic-Text dla typów ciągów, formalne i rzeczywiste typy parametrów dla `printf` Match, ponieważ `_TCHAR*` mapowania do `char*`.

- Procedura specyficzna dla MBCS. W takim przypadku argumenty ciągu powinny być typu `unsigned char*`. Na przykład `_tcsrev` mapuje do `_mbsrev`, która oczekuje i zwraca ciąg typu `unsigned char*`. Jeśli używasz typu danych `_TCHAR` Generic-Text dla typów ciągów, występuje konflikt typu potencjalnego, ponieważ `_TCHAR` mapuje do typu `char`.

Poniżej znajdują się trzy rozwiązania uniemożliwiające konflikt tego typu (oraz ostrzeżenia kompilatora C C++ lub błędy kompilatora, które byłyby wynikiem):

- Użyj zachowania domyślnego. Używanie TCHAR. h zawiera prototypy procedury tekstu ogólnego dla procedur w bibliotekach czasu wykonywania, jak w poniższym przykładzie.

    ```cpp
    char * _tcsrev(char *);
    ```

   W domyślnym przypadku prototyp `_tcsrev` mapowania do `_mbsrev` za pomocą thunk w libc. lib. Spowoduje to zmianę typów `_mbsrev` przychodzących parametrów i wychodzącej wartości zwracanej z `_TCHAR*` (czyli `char *`) do `unsigned char *`. Ta metoda zapewnia Dopasowywanie typów w przypadku używania `_TCHAR`, ale jest stosunkowo niska z powodu obciążenia wywołania funkcji.

- Użyj funkcji tworzenia i wykreślania w kodzie następujących instrukcji preprocesora.

    ```cpp
    #define _USE_INLINING
    ```

   Ta metoda powoduje, że Wbudowana funkcja thunk w używanie TCHAR. h mapuje procedurę tekstu ogólnego bezpośrednio do odpowiedniej procedury MBCS. Poniższy fragment kodu z używanie TCHAR. h zawiera przykład tego, jak to zrobić.

    ```cpp
    __inline char *_tcsrev(char *_s1)
    {return (char *)_mbsrev((unsigned char *)_s1);}
    ```

   Jeśli możesz użyć funkcji tworzenia konspektu, jest to najlepsze rozwiązanie, ponieważ gwarantuje ono zgodność typów i nie ma dodatkowego kosztu czasu.

- Używaj bezpośredniego mapowania, dołączając następującą instrukcję preprocesora w kodzie.

    ```cpp
    #define _MB_MAP_DIRECT
    ```

   Takie podejście zapewnia szybką alternatywę, jeśli nie chcesz używać zachowania domyślnego lub nie można użyć funkcji tworzenia konspektu. Powoduje to zamapowanie procedury tekstu ogólnego przez makro bezpośrednio do wersji MBCS procedury, jak w poniższym przykładzie z używanie TCHAR. h.

    ```cpp
    #define _tcschr _mbschr
    ```

   Po podniesieniu tego podejścia należy zachować ostrożność, aby zapewnić użycie odpowiednich typów danych dla argumentów ciągów i wartości zwracanych przez ciąg. Można użyć rzutowania typu, aby upewnić się, że odpowiedni typ jest zgodny lub można użyć `_TXCHAR` typu danych rodzajowych. `_TXCHAR` mapuje do typu **char** w kodzie SBCS, ale mapuje na typ **unsigned char** in Code MBCS. Aby uzyskać więcej informacji na temat makr tekstu ogólnego, zobacz [Mapowanie tekstu ogólnego](../c-runtime-library/generic-text-mappings.md) w *dokumentacji biblioteki wykonawczej*.

## <a name="see-also"></a>Zobacz też

[Mapowania typu ogólny-tekst w pliku tchar.h](../text/generic-text-mappings-in-tchar-h.md)
