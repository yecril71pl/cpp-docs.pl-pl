---
title: -SYMBOLS | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /symbols
dev_langs: C++
helpviewer_keywords:
- symbols, dumping
- public symbols
- symbols, displaying COFF symbol table
- symbol tables
- SYMBOLS dumpbin option
- /SYMBOLS dumpbin option
- -SYMBOLS dumpbin option
ms.assetid: 34bcae90-4561-4c77-a80c-065508dec39a
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 360f26de5043eae7f5cdb4688612f95b96be8fbd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="symbols"></a>/SYMBOLS
```  
/SYMBOLS  
```  
  
 Ta opcja powoduje wyświetlenie tabelą symboli COFF. Tabele symboli istnieje we wszystkich plikach obiektu. Tabela symboli COFF pojawia się w pliku obrazu tylko wtedy, gdy jest on połączony z opcji/Debug.  
  
 Poniżej znajduje się opis /SYMBOLS w danych wyjściowych. Przeszukując pliku winnt.h (IMAGE_SYMBOL i IMAGE_AUX_SYMBOL) lub COFF dokumentację można znaleźć dodatkowe informacje na temat znaczenia /SYMBOLS danych wyjściowych.  
  
 Podane następujące zrzutu próbki:  
  
```  
Dump of file main.obj  
File Type: COFF OBJECT  
  
COFF    SYMBOL    TABLE  
000    00000000   DEBUG      notype      Filename      | .file  
      main.cpp  
002   000B1FDB   ABS      notype      Static      | @comp.id  
003   00000000   SECT1      notype      Static      | .drectve  
      Section length       26, #relocs   0, #linenums    0, checksum 722C964F  
005   00000000   SECT2      notype      Static      | .text  
      Section length      23, #relocs      1, #linenums    0, checksum 459FF65F, selection    1 (pick no duplicates)  
007   00000000   SECT2      notype ()   External      | _main  
008   00000000   UNDEF      notype ()   External      | ?MyDump@@YAXXZ (void __cdecl MyDump(void))  
  
String Table Size = 0x10 bytes  
  
Summary  
  
      26 .drectve  
      23 .text  
```  
  
## <a name="remarks"></a>Uwagi  
 Następujący opis wierszy, które zaczynają się od numeru symbol opisano kolumny, które zawierają informacje dotyczące użytkowników:  
  
-   Pierwszy trzech cyfr jest symbol/numer indeksu.  
  
-   Jeśli natomiast trzecia kolumna zawiera s*x*, symbol jest zdefiniowany w tej sekcji pliku obiektu. Jednak jeśli wydaje się UNDEF, nie jest zdefiniowany w tym obiekcie i muszą zostać rozwiązane w innym miejscu.  
  
-   Kolumny piąty (statyczne, zewnętrzne) informuje, czy symbol jest widoczne tylko w obrębie tego obiektu lub czy jest on publiczny (widoczny zewnętrznie). Nie można połączyć statycznego symbolu _sym, _sym symboli publicznych; będą to dwóch różnych wystąpieniach funkcji o nazwie _sym.  
  
 Ostatnia kolumna w wierszu numerowane nazwy symbolu, zarówno dekorowane i bez.  
  
 Tylko [/HEADERS](../../build/reference/headers.md) — opcja polecenia DUMPBIN jest dostępny do użytku na pliki tworzone z [/GL](../../build/reference/gl-whole-program-optimization.md) — opcja kompilatora.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje DUMPBIN](../../build/reference/dumpbin-options.md)