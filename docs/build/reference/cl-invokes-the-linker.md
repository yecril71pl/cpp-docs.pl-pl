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
ms.openlocfilehash: bc9c5c4815dc83b37d0b7971d5fd0f31db51e39e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32371918"
---
# <a name="cl-invokes-the-linker"></a>CL wywołuje konsolidator
CL wywołuje konsolidator automatycznie, po kompilacji, chyba że używana jest opcja /c. CL przekazuje do konsolidator nazwy plików .obj utworzone podczas kompilowania kodu i nazwy inne pliki określone w wierszu polecenia. Konsolidator używa opcji wymienionych w zmiennej środowiskowej łącza. Opcja/Link umożliwia określenie opcji konsolidatora w wierszu polecenia CL. Opcje, które należy wykonać opcji/Link zastępują w zmiennej środowiskowej łącza. W poniższej tabeli przedstawiono opcje Pomiń łączenie.  
  
|Opcja|Opis|  
|------------|-----------------|  
|/c|Kompiluj bez konsolidacji|  
|/ /P E, /EP,|Przetwarzanie wstępne bez kompilowania lub łączenia|  
|/ZG|Generuj prototypy funkcji|  
|/ZS|Sprawdzanie składni|  
  
 Aby uzyskać szczegółowe informacje na temat łączenia, zobacz [opcje konsolidatora](../../build/reference/linker-options.md).  
  
## <a name="example"></a>Przykład  
 Załóżmy, że kompilacja pliki źródłowe C trzy: MAIN.c, MOD1.c i MOD2.c. Każdy plik zawiera wywołanie funkcji zdefiniowanej w innym pliku:  
  
-   MAIN.c wywołuje funkcję `func1` MOD1.c i funkcja `func2` w MOD2.c.  
  
-   MOD1.c wywołuje funkcje biblioteki standardowej `printf_s` i `scanf_s`.  
  
-   MOD2.c wywołuje funkcje graficzne o nazwie `myline` i `mycircle`, które są zdefiniowane w bibliotece o nazwie MYGRAPH.lib.  
  
 Aby utworzyć ten program, kompilacji z następującego polecenia:  
  
```  
CL MAIN.c MOD1.C MOD2.C MYGRAPH.lib  
```  
  
 CL najpierw kompiluje pliki źródłowe C i tworzy pliki obiektu MAIN.obj, MOD1.obj i MOD2.obj. Kompilator umieszcza nazwę biblioteki standardowe w każdym .obj pliku. Aby uzyskać więcej informacji, zobacz [biblioteki wykonawczej użyj](../../build/reference/md-mt-ld-use-run-time-library.md).  
  
 CL przekazuje nazwy plików .obj, wraz z nazwą MYGRAPH.lib, konsolidator. Konsolidator rozpoznawania odwołań zewnętrznych w następujący sposób:  
  
1.  W MAIN.obj, odwołanie do `func1` został rozwiązany za pomocą definicji w MOD1.obj; odwołanie do `func2` został rozwiązany za pomocą definicji w MOD2.obj.  
  
2.  W MOD1.obj, odwołania do `printf_s` i `scanf_s` są rozpoznawane przy użyciu definicji w bibliotece o nazwie w obrębie MOD1.obj znajdzie konsolidator.  
  
3.  W MOD2.obj, odwołania do `myline` i `mycircle` są rozpoznawane przy użyciu definicji w MYGRAPH.lib.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)