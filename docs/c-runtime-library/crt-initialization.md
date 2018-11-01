---
title: Inicjalizacja CRT
ms.date: 11/04/2016
helpviewer_keywords:
- CRT initialization [C++]
ms.assetid: e7979813-1856-4848-9639-f29c86b74ad7
ms.openlocfilehash: 615c113082e2ef0dbfc40bafbfa040c06e628da5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50656953"
---
# <a name="crt-initialization"></a>Inicjalizacja CRT

W tym temacie opisano, jak CRT inicjalizuje globalnego stanów w kodzie natywnym.

Domyślnie konsolidator zawiera biblioteki CRT, która zawiera swój własny kod startowy. Ten kod startowy inicjuje biblioteki CRT, wywołuje inicjatorów globalnych, a następnie wywołuje dostarczonych przez użytkownika `main` funkcji dla aplikacji konsoli.

## <a name="initializing-a-global-object"></a>Inicjowanie obiektów globalnych

Rozważmy poniższy kod:

```
int func(void)
{
    return 3;
}

int gi = func();

int main()
{
    return gi;
}
```

Zgodnie ze standardem C/C++ `func()` musi zostać wywołana przed `main()` jest wykonywany. Ale który ją wywołuje?

Jednym ze sposobów, aby określić, to jest, aby ustawić punkt przerwania `func()`, debugowania aplikacji i sprawdzić stosu. Jest to możliwe, ponieważ kod źródłowy CRT jest dołączony do Visual Studio.

Podczas przeglądania funkcji na stosie znajdziesz, że CRT jest lista wskaźników do funkcji w pętli i wywoływania każdy z nich, po ich napotkaniu. Te funkcje są podobne do `func()` lub konstruktory wystąpień klas.

CRT uzyskuje listę wskaźników do funkcji z kompilator języka Visual C++. Gdy kompilator wykryje inicjatorze globalnym, generuje dynamiczny inicjator w `.CRT$XCU` sekcji (gdzie `CRT` jest nazwy sekcji i `XCU` to nazwa grupy). Aby uzyskać listę tych inicjatory dynamicznego, uruchom polecenie **dumpbin/all main.obj**, a następnie wyszukaj `.CRT$XCU` sekcji (w przypadku main.cpp jest kompilowany jako plik C++ nie jest to plik C). Będzie podobny do następującego:

```
SECTION HEADER #6
.CRT$XCU name
       0 physical address
       0 virtual address
       4 size of raw data
     1F2 file pointer to raw data (000001F2 to 000001F5)
     1F6 file pointer to relocation table
       0 file pointer to line numbers
       1 number of relocations
       0 number of line numbers
40300040 flags
         Initialized Data
         4 byte align
         Read Only

RAW DATA #6
  00000000: 00 00 00 00                                      ....

RELOCATIONS #6
                                                Symbol    Symbol
Offset    Type              Applied To         Index     Name
--------  ----------------  -----------------  --------  ------
00000000  DIR32                      00000000         C  ??__Egi@@YAXXZ (void __cdecl `dynamic initializer for 'gi''(void))
```

CRT definiuje dwa wskaźniki:

- `__xc_a` W `.CRT$XCA`

- `__xc_z` W `.CRT$XCZ`

Obie grupy nie mają inne symbole zdefiniowane, z wyjątkiem `__xc_a` i `__xc_z`.

Teraz, gdy program łączący odczytuje różne `.CRT` grup, jego łączy je w jednej sekcji i porządkuje je w kolejności alfabetycznej. Oznacza to, że inicjatorów globalnych zdefiniowanych przez użytkownika (które kompilator języka Visual C++ zapisuje w `.CRT$XCU`) będzie zawsze mają po `.CRT$XCA` i przed `.CRT$XCZ`.

Sekcja będzie wyglądać w następujący sposób:

```
.CRT$XCA
            __xc_a
.CRT$XCU
            Pointer to Global Initializer 1
            Pointer to Global Initializer 2
.CRT$XCZ
            __xc_z
```

Tak, biblioteka CRT będą wykorzystywane serwery `__xc_a` i `__xc_z` do określenia początku i końca listy inicjatorów globalnych ze względu na sposób, w którym one są ułożone w pamięci po załadowaniu obrazu.

## <a name="see-also"></a>Zobacz też

[Biblioteka CRT, funkcje](../c-runtime-library/crt-library-features.md)