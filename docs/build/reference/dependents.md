---
title: /DEPENDENTS
ms.date: 07/15/2019
f1_keywords:
- /dependents
helpviewer_keywords:
- -DEPENDENTS dumpbin option
- /DEPENDENTS dumpbin option
- DEPENDENTS dumpbin option
ms.assetid: 9b31da2a-75ac-4bbf-a3f1-adf8b0ecbbb4
ms.openlocfilehash: 88f0062a6bbca3f9199a12f739c2ade5f9d912cd
ms.sourcegitcommit: 7f5b29e24e1be9b5985044a030977485fea0b50c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/17/2019
ms.locfileid: "68299746"
---
# <a name="dependents"></a>/DEPENDENTS

Zrzuca nazwy bibliotek DLL, z których funkcja importuje obrazy. Można użyć listy, aby określić, które biblioteki dll mają być rozpowszechniane wraz z aplikacją, lub znaleźć nazwę brakującej zależności.

## <a name="syntax"></a>Składnia

> **/DEPENDENTS**

Ta opcja ma zastosowanie do wszystkich plików wykonywalnych określonych w wierszu polecenia. Nie przyjmuje żadnych argumentów.

## <a name="remarks"></a>Uwagi

Opcja **/DEPENDENTS** dodaje nazwy bibliotek DLL, z których obraz importuje funkcje do danych wyjściowych. Ta opcja nie zrzuca nazw zaimportowanych funkcji. Aby wyświetlić nazwy zaimportowanych funkcji, użyj opcji [/Imports —](imports-dumpbin.md) .

Tylko opcja [/Headers](headers.md) polecenia DUMPBIN jest dostępna do użycia w przypadku plików utworzonych przy użyciu opcji kompilatora [/GL](gl-whole-program-optimization.md) .

## <a name="example"></a>Przykład

Ten przykład przedstawia dane wyjściowe polecenia DUMPBIN opcji **/DEPENDENTS** w pliku wykonywalnym klienta wbudowane w [przewodniku: Tworzenie własnej biblioteki](../walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)dołączanej dynamicznie i korzystanie z niej:

```cmd
C:\Users\username\Source\Repos\MathClient\Debug>dumpbin /DEPENDENTS MathClient.exe
Microsoft (R) COFF/PE Dumper Version 14.16.27032.1
Copyright (C) Microsoft Corporation.  All rights reserved.


Dump of file MathClient1322.exe

File Type: EXECUTABLE IMAGE

  Image has the following dependencies:

    MathLibrary.dll
    MSVCP140D.dll
    VCRUNTIME140D.dll
    ucrtbased.dll
    KERNEL32.dll

  Summary

        1000 .00cfg
        1000 .data
        2000 .idata
        1000 .msvcjmc
        3000 .rdata
        1000 .reloc
        1000 .rsrc
        8000 .text
       10000 .textbss
```

## <a name="see-also"></a>Zobacz także

[Opcje DUMPBIN](dumpbin-options.md)
