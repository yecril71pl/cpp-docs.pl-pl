---
title: Inicjalizacja CRT
description: Opisuje sposób inicjowania stanu globalnego w kodzie natywnym przez CRT.
ms.topic: conceptual
ms.date: 11/04/2016
helpviewer_keywords:
- CRT initialization [C++]
ms.assetid: e7979813-1856-4848-9639-f29c86b74ad7
ms.openlocfilehash: 25f1e2a7e5b7d91c729bb45bd79ba9a8720cead1
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2020
ms.locfileid: "91589773"
---
# <a name="crt-initialization"></a>Inicjalizacja CRT

W tym temacie opisano sposób inicjowania przez CRT stanu globalnego w kodzie natywnym.

Domyślnie konsolidator obejmuje bibliotekę CRT, która udostępnia własny kod uruchomienia. Ten kod uruchamiania inicjuje bibliotekę CRT, wywołuje globalne inicjatory, a następnie wywołuje funkcję dostarczoną przez użytkownika `main` dla aplikacji konsolowych.

## <a name="initializing-a-global-object"></a>Inicjowanie obiektu globalnego

Spójrzmy na poniższy kod:

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

Zgodnie ze standardem C/C++, `func()` musi być wywoływana przed `main()` wykonaniem. Ale który je wywołuje?

Jednym ze sposobów określenia obiektu wywołującego jest ustawienie punktu przerwania w programie `func()` , debugowanie aplikacji i sprawdzenie stosu. Jest to możliwe, ponieważ kod źródłowy CRT jest dołączony do programu Visual Studio.

Podczas przeglądania funkcji na stosie zobaczysz, że CRT wywołuje listę wskaźników funkcji. Te funkcje są podobne do `func()` , lub konstruktorów dla wystąpień klas.

CRT pobiera listę wskaźników funkcji z kompilatora języka Microsoft C++. Gdy kompilator widzi inicjatora globalnego, generuje inicjator dynamiczny w `.CRT$XCU` sekcji gdzie `CRT` jest nazwą sekcji i `XCU` jest nazwą grupy. Aby uzyskać listę inicjatorów dynamicznych, uruchom polecenie **polecenia DUMPBIN/All Main. obj**, a następnie wyszukaj `.CRT$XCU` sekcję. Ma to zastosowanie, gdy Main. cpp jest kompilowany jako plik języka C++, a nie plik C. Będzie wyglądać podobnie do poniższego przykładu:

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
--------  ----------------  -----------------  --------  -------
00000000  DIR32             00000000           C         ??__Egi@@YAXXZ (void __cdecl `dynamic initializer for 'gi''(void))
```

CRT definiuje dwa wskaźniki:

- `__xc_a` w elemencie `.CRT$XCA`

- `__xc_z` w elemencie `.CRT$XCZ`

Żadna z grup nie ma żadnych innych symboli zdefiniowanych poza `__xc_a` i `__xc_z` .

Teraz, gdy konsolidator odczytuje różne `.CRT` grupy, łączy je w jednej sekcji i porządkuje je alfabetycznie. Oznacza to, że zdefiniowane przez użytkownika inicjatory globalne (które są umieszczane w kompilatorze Microsoft C++ `.CRT$XCU` ) zawsze będą znajdować się po `.CRT$XCA` i wcześniej `.CRT$XCZ` .

Sekcja będzie wyglądać podobnie do poniższego przykładu:

```
.CRT$XCA
            __xc_a
.CRT$XCU
            Pointer to Global Initializer 1
            Pointer to Global Initializer 2
.CRT$XCZ
            __xc_z
```

Dlatego Biblioteka CRT używa zarówno programu `__xc_a` , jak i `__xc_z` do określenia początku i końca listy globalnych inicjatorów z powodu sposobu, w jaki są one ustalone w pamięci po załadowaniu obrazu.

## <a name="see-also"></a>Zobacz też

[Funkcje biblioteki CRT](../c-runtime-library/crt-library-features.md)
