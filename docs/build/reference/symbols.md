---
title: /SYMBOLS
ms.date: 09/05/2018
f1_keywords:
- /symbols
helpviewer_keywords:
- symbols, dumping
- public symbols
- symbols, displaying COFF symbol table
- symbol tables
- SYMBOLS dumpbin option
- /SYMBOLS dumpbin option
- -SYMBOLS dumpbin option
ms.assetid: 34bcae90-4561-4c77-a80c-065508dec39a
ms.openlocfilehash: a47b7da9f0b01353ef15e8b5c070c19e7c521c37
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62317708"
---
# <a name="symbols"></a>/SYMBOLS

```
/SYMBOLS
```

Ta opcja wyświetla tabelą symboli COFF. Tabele symboli istnieje we wszystkich plikach obiektu. Tabela symboli COFF pojawia się w pliku obrazu, tylko wtedy, gdy jest on połączony przy użyciu opcji/Debug.

Poniżej znajduje się opis danych wyjściowych dla /SYMBOLS. Dodatkowe informacje na temat znaczenia /SYMBOLS danych wyjściowych można znaleźć przez wyszukiwanie w pliku winnt.h (IMAGE_SYMBOL i IMAGE_AUX_SYMBOL) lub w dokumentacji COFF.

Biorąc pod uwagę następujące zrzutu próbki:

```
Dump of file main.obj
File Type: COFF OBJECT

COFF SYMBOL TABLE
000 00000000 DEBUG    notype       Filename     | .file
    main.cpp
002 000B1FDB ABS      notype       Static       | @comp.id
003 00000000 SECT1    notype       Static       | .drectve
    Section length     26, #relocs    0, #linenums    0, checksum 722C964F
005 00000000 SECT2    notype       Static       | .text
    Section length     23, #relocs    1, #linenums    0, checksum 459FF65F, selection    1 (pick no duplicates)
007 00000000 SECT2    notype ()    External     | _main
008 00000000 UNDEF    notype ()    External     | ?MyDump@@YAXXZ (void __cdecl MyDump(void))

String Table Size = 0x10 bytes

  Summary

         26 .drectve
         23 .text
```

## <a name="remarks"></a>Uwagi

Poniższy opis, wiersze rozpoczynające się od numeru symboli w tym artykule opisano kolumny, które zawierają informacje dotyczące użytkowników:

- Pierwsze trzy cyfrowy numer jest symbol/numer indeksu.

- Jeśli trzecia kolumna zawiera s*x*, symbol jest zdefiniowany w tej sekcji pliku obiektu. Ale jeśli pojawi się UNDEF, nie jest zdefiniowany w tym obiekcie i muszą zostać rozwiązane w innym miejscu.

- Piąta kolumna (statyczny, zewnętrzny) informuje, czy symbol jest widoczny tylko w obrębie obiektu lub czy nie jest publiczny (widoczny zewnętrznie). Symbol statyczny _sym, nie można połączyć _sym symboli publicznych; będą to dwa różne wystąpienia funkcji o nazwie _sym.

Ostatnia kolumna numerowana wiersza nazwy symbolu, zarówno dekorowane i niedekorowanego.

Tylko [/HEADERS](headers.md) — opcja polecenia DUMPBIN jest dostępna do użycia w plikach z [/GL](gl-whole-program-optimization.md) — opcja kompilatora.

## <a name="see-also"></a>Zobacz także

[Opcje DUMPBIN](dumpbin-options.md)
