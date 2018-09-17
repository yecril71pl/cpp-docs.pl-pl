---
title: Opcje LINK kontrolowane przez kompilator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- link
dev_langs:
- C++
helpviewer_keywords:
- LINK tool [C++], compiler-controlled options
- linker [C++], CL compiler control
- linking [C++], affected by CL features
- cl.exe compiler [C++], features that affect linking
- cl.exe compiler [C++], controlling linker
ms.assetid: e4c03896-c99c-4599-8502-e0f4bebe69d0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ee952fe5152d98aa33c4ef7e98f8a2eb3ef077be
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45726430"
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