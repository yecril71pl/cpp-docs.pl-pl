---
title: CL wywołuje konsolidator
ms.date: 11/04/2016
f1_keywords:
- cl
helpviewer_keywords:
- compiling source code [C++], without linking
- invoking linker from the compiler
- LINK tool [C++], invoking from CL compiler
- cl.exe compiler [C++], compiling without linking
- cl.exe compiler [C++], controlling linker
ms.assetid: eae47ef7-09eb-40c9-b318-7c714cd452fc
ms.openlocfilehash: f8d8c5e1b0ca4d2a35a57683fea2e6de12747860
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57821486"
---
# <a name="cl-invokes-the-linker"></a>CL wywołuje konsolidator

CL wywołuje konsolidator automatycznie, po kompilacji, chyba że używana jest opcja/c. CL przekazuje do konsolidatora, nazwy plików .obj, utworzony podczas kompilowania i nazwy inne pliki określone w wierszu polecenia. Konsolidator używa opcje wymienione w zmiennej środowiskowej łącza. Opcja/Link umożliwia określenie opcji konsolidatora w wierszu polecenia CL. Opcje, które należy wykonać opcji/Link przesłaniają akcje w zmiennej środowiskowej łącza. Opcje w poniższej tabeli Pomiń łączenie.

|Opcja|Opis|
|------------|-----------------|
|/c|Kompiluj bez konsolidacji|
|/E, /EP, /P|Przetwarzanie wstępne bez kompilowania i łączenia|
|/Zg|Generuj prototypy funkcji|
|/Zs|Sprawdź składnię|

Aby uzyskać szczegółowe informacje na temat łączenia, zobacz [opcje konsolidatora MSVC](linker-options.md).

## <a name="example"></a>Przykład

Załóżmy, czy kompilujesz pliki źródłowe C trzy: MAIN.c MOD1.c i MOD2.c. Każdy plik zawiera wywołanie do funkcji zdefiniowanych w innym pliku:

- MAIN.c wywołuje funkcję `func1` MOD1.c i funkcja `func2` w MOD2.c.

- MOD1.c wywołuje funkcje biblioteki standardowej `printf_s` i `scanf_s`.

- MOD2.c wywołuje funkcje grafiki, o nazwie `myline` i `mycircle`, które są definiowane w bibliotece o nazwie MYGRAPH.lib.

Aby skompilować ten program, należy skompilować przy użyciu następującego polecenia:

```
CL MAIN.c MOD1.C MOD2.C MYGRAPH.lib
```

CL najpierw kompiluje pliki źródłowe C i tworzy pliki obiektów MAIN.obj MOD1.obj i MOD2.obj. Kompilator umieszcza nazwę biblioteki standardowej w każdym pliku obj. Aby uzyskać więcej informacji, zobacz [korzystaj z bibliotek wykonawczych](md-mt-ld-use-run-time-library.md).

CL przekazuje nazwy plików .obj, wraz z nazwą MYGRAPH.lib, do konsolidatora. Konsolidator rozpoznawania odwołań zewnętrznych w następujący sposób:

1. W MAIN.obj, odwołanie do `func1` rozwiązania przy użyciu definicji w MOD1.obj; odwołanie do `func2` zostanie rozwiązany w MOD2.obj przy użyciu definicji.

1. W MOD1.obj, odwołania do `printf_s` i `scanf_s` są rozpoznawane za pomocą definicji w bibliotece programu o nazwie w ramach MOD1.obj konsolidator wykryje.

1. W MOD2.obj, odwołania do `myline` i `mycircle` są rozpoznawane za pomocą definicji w MYGRAPH.lib.

## <a name="see-also"></a>Zobacz także

[MSVC Compiler Options](compiler-options.md)<br/>
[Ustawianie opcji kompilatora](compiler-command-line-syntax.md)
