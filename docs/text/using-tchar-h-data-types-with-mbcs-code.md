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
ms.openlocfilehash: dd43c29d77c3351e8f597b474c4756ad3d45ef2b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215364"
---
# <a name="using-tcharh-data-types-with-_mbcs-code"></a>Używanie typów danych TCHAR.H z kodem _MBCS

Po `_MBCS` zdefiniowaniu stałej manifestu dana procedura tekstu ogólnego mapuje do jednego z następujących rodzajów procedur:

- Procedura SBCS, która obsługuje odpowiednio bajty wielobajtowe, znaki i ciągi. W tym przypadku argumenty ciągu powinny być typu **`char*`** . Na przykład `_tprintf` mapuje na `printf` ; argumenty ciągu mają `printf` Typ **`char*`** . W przypadku użycia `_TCHAR` typu danych rodzajowych dla typów ciągów formalne i rzeczywiste typy parametrów dla `printf` dopasowania, ponieważ `_TCHAR*` mapuje na **`char*`** .

- Procedura specyficzna dla MBCS. W tym przypadku argumenty ciągu powinny być typu `unsigned char*` . Na przykład `_tcsrev` mapuje do `_mbsrev` , który oczekuje i zwraca ciąg typu `unsigned char*` . W przypadku użycia `_TCHAR` typu danych rodzajowych dla typów ciągów istnieje potencjalny konflikt typu, ponieważ `_TCHAR` mapuje do typu **`char`** .

Poniżej przedstawiono trzy rozwiązania uniemożliwiające konflikt tego typu (oraz ostrzeżenia kompilatora C lub błędy kompilatora języka C++, które byłyby wynikiem):

- Użyj zachowania domyślnego. Używanie TCHAR. h zawiera prototypy procedury tekstu ogólnego dla procedur w bibliotekach czasu wykonywania, jak w poniższym przykładzie.

    ```cpp
    char * _tcsrev(char *);
    ```

   W domyślnym przypadku prototyp jest `_tcsrev` mapowany do `_mbsrev` thunk w libc. lib. Spowoduje to zmianę typów `_mbsrev` parametrów przychodzących i wychodzących wartości zwracanej z `_TCHAR*` (czyli `char *` ) na `unsigned char *` . Ta metoda zapewnia Dopasowywanie typów `_TCHAR` , gdy jest używany, ale jest stosunkowo wolne ze względu na obciążenie wywołania funkcji.

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

   Po podniesieniu tego podejścia należy zachować ostrożność, aby zapewnić użycie odpowiednich typów danych dla argumentów ciągów i wartości zwracanych przez ciąg. Można użyć rzutowania typu, aby zapewnić odpowiedni typ dopasowania lub użyć `_TXCHAR` typu danych rodzajowych. `_TXCHAR`mapuje do typu **`char`** w kodzie SBCS, ale mapuje do typu **`unsigned char`** w kodzie MBCS. Aby uzyskać więcej informacji na temat makr tekstu ogólnego, zobacz [Mapowanie tekstu ogólnego](../c-runtime-library/generic-text-mappings.md) w *dokumentacji biblioteki wykonawczej*.

## <a name="see-also"></a>Zobacz także

[Mapowania tekstu ogólnego w używanie TCHAR. h](../text/generic-text-mappings-in-tchar-h.md)
