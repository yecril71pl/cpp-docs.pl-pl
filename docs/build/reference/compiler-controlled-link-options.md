---
title: Opcje LINK kontrolowane przez kompilator
ms.date: 11/04/2016
f1_keywords:
- link
helpviewer_keywords:
- LINK tool [C++], compiler-controlled options
- linker [C++], CL compiler control
- linking [C++], affected by CL features
- cl.exe compiler [C++], features that affect linking
- cl.exe compiler [C++], controlling linker
ms.assetid: e4c03896-c99c-4599-8502-e0f4bebe69d0
ms.openlocfilehash: 21d0baccaf74fc08bb110b0ae9f8b7dc108abd6b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50561580"
---
# <a name="compiler-controlled-link-options"></a>Opcje LINK kontrolowane przez kompilator

Kompilator CL automatycznie wywołuje łącza, chyba że określono opcję/c. CL zapewnia kontrolę nad konsolidator przy użyciu opcji wiersza polecenia i argumentów. Poniższa tabela zawiera podsumowanie funkcji w CL, które wpływają niekorzystnie na konsolidację.

|Specyfikacja CL|Akcja CL, która ma wpływ na LINK|
|----------------------|---------------------------------|
|Rozszerzenia nazw plików innych niż .c ",".cxx "," CPP "lub".def|Przekazuje nazwę pliku jako dane wejściowe LINK|
|*Nazwa pliku*.def|/ DEF przekazuje:*filename*.def|
|/F*numer*|Przebiegi /STACK:*numer*|
|/FD*nazwy pliku*|Przekazuje/PDB:*nazwy pliku*|
|/Fe*nazwy pliku*|Przekazuje/OUT:*nazwy pliku*|
|/FM*nazwy pliku*|Przebiegi/map:*nazwy pliku*|
|/GY|Tworzy funkcje pakowane (COMDATs); Włącza łączenie na poziomie — funkcja|
|/LD|Przekazuje/dll|
|/ LDd|Przekazuje/dll|
|/link|Przekazuje pozostałą część wiersza polecenia do łącza|
|/MD lub/MT|Umieszcza domyślną nazwę biblioteki w pliku .obj|
|/ MDd lub/mtd|W pliku .obj, umieszcza domyślną nazwę biblioteki. Definiuje symbol **_DEBUG**|
|/nologo|/ Nologo przekazuje|
|/ Zd|Przebiegi/Debug|
|Zi lub/z7|Przebiegi/Debug|
|/ZL|Pomija domyślną nazwę biblioteki z pliku .obj|

Aby uzyskać więcej informacji, zobacz [opcje kompilatora](../../build/reference/compiler-options.md).

## <a name="see-also"></a>Zobacz też

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)