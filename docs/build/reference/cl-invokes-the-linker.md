---
title: CL wywołuje konsolidator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- cl
dev_langs:
- C++
helpviewer_keywords:
- compiling source code [C++], without linking
- invoking linker from the compiler
- LINK tool [C++], invoking from CL compiler
- cl.exe compiler [C++], compiling without linking
- cl.exe compiler [C++], controlling linker
ms.assetid: eae47ef7-09eb-40c9-b318-7c714cd452fc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ed6c968b86192ae79c0c921f8b3fababc596c9a2
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45713833"
---
# <a name="cl-invokes-the-linker"></a>CL wywołuje konsolidator

CL wywołuje konsolidator automatycznie, po kompilacji, chyba że używana jest opcja/c. CL przekazuje do konsolidatora, nazwy plików .obj, utworzony podczas kompilowania i nazwy inne pliki określone w wierszu polecenia. Konsolidator używa opcje wymienione w zmiennej środowiskowej łącza. Opcja/Link umożliwia określenie opcji konsolidatora w wierszu polecenia CL. Opcje, które należy wykonać opcji/Link przesłaniają akcje w zmiennej środowiskowej łącza. Opcje w poniższej tabeli Pomiń łączenie.

|Opcja|Opis|
|------------|-----------------|
|/c|Kompiluj bez konsolidacji|
|/ /P E, /EP,|Przetwarzanie wstępne bez kompilowania i łączenia|
|/ZG|Generuj prototypy funkcji|
|/ZS|Sprawdź składnię|

Aby uzyskać szczegółowe informacje na temat łączenia, zobacz [opcje konsolidatora](../../build/reference/linker-options.md).

## <a name="example"></a>Przykład

Przyjęto założenie, czy kompilujesz pliki źródłowe C trzy: MAIN.c MOD1.c i MOD2.c. Każdy plik zawiera wywołanie do funkcji zdefiniowanych w innym pliku:

- MAIN.c wywołuje funkcję `func1` MOD1.c i funkcja `func2` w MOD2.c.

- MOD1.c wywołuje funkcje biblioteki standardowej `printf_s` i `scanf_s`.

- MOD2.c wywołuje funkcje grafiki, o nazwie `myline` i `mycircle`, które są definiowane w bibliotece o nazwie MYGRAPH.lib.

Aby skompilować ten program, należy skompilować przy użyciu następującego polecenia:

```
CL MAIN.c MOD1.C MOD2.C MYGRAPH.lib
```

CL najpierw kompiluje pliki źródłowe C i tworzy pliki obiektów MAIN.obj MOD1.obj i MOD2.obj. Kompilator umieszcza nazwę biblioteki standardowej w każdym pliku obj. Aby uzyskać więcej informacji, zobacz [korzystaj z bibliotek wykonawczych](../../build/reference/md-mt-ld-use-run-time-library.md).

CL przekazuje nazwy plików .obj, wraz z nazwą MYGRAPH.lib, do konsolidatora. Konsolidator rozpoznawania odwołań zewnętrznych w następujący sposób:

1. W MAIN.obj, odwołanie do `func1` rozwiązania przy użyciu definicji w MOD1.obj; odwołanie do `func2` zostanie rozwiązany w MOD2.obj przy użyciu definicji.

1. W MOD1.obj, odwołania do `printf_s` i `scanf_s` są rozpoznawane za pomocą definicji w bibliotece programu o nazwie w ramach MOD1.obj konsolidator wykryje.

1. W MOD2.obj, odwołania do `myline` i `mycircle` są rozpoznawane za pomocą definicji w MYGRAPH.lib.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)