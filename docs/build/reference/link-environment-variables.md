---
title: Zmienne środowiskowe LINK | Dokumentacja firmy Microsoft
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
- variables, environment
- LINK tool [C++], environment variables
- LIB environment variable
- environment variables [C++], LINK
ms.assetid: 9a3d3291-0cc4-4a7d-9d50-80e351b90708
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 076e427e50520651f30cde20c764ff1124a6f953
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="link-environment-variables"></a>Zmienne środowiskowe LINK

LINK-narzędzie używa następujących zmiennych środowiskowych:  
  
-   ŁĄCZE i \_łącze\_, jeśli została zdefiniowana. LINK-narzędzie dołącza opcje i argumenty zdefiniowane w zmiennej środowiskowej łącza i dołącza opcje i argumenty zdefiniowane w \_łącze\_ zmiennej środowiskowej do argumentów wiersza polecenia przed rozpoczęciem przetwarzania.  
  
-   Biblioteka, jeśli została zdefiniowana. Narzędzia łącze używa ścieżka LIB podczas wyszukiwania dla obiekt, bibliotekę lub inny plik określony w wierszu polecenia lub przez [/BASE](../../build/reference/base-base-address.md) opcji. Używa również ścieżka LIB można znaleźć pliku PDB o nazwie w obiekcie. Lib — zmienna może zawierać specyfikacji ścieżki, oddzielając je średnikami. Jednej ścieżki musi wskazywać podkatalogu \lib instalację programu Visual C++.  
  
-   ŚCIEŻKA, jeśli narzędzie musi być uruchamiane CVTRES i nie można odnaleźć pliku w tym samym katalogu co łącza. (Łącze wymaga CVTRES połączyć plik .res). ŚCIEŻKA musi wskazywać podkatalogu \bin instalację programu Visual C++.  
  
-   TMP, aby określić katalog, w trakcie łączenia OMF lub .res plików.  
  
## <a name="see-also"></a>Zobacz też  

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
[Opcje konsolidatora](../../build/reference/linker-options.md)   
[Kompilowanie kodu C/C++ w wierszu polecenia](../../build/building-on-the-command-line.md)  
[Ustawianie ścieżki i zmiennych środowiskowych dla kompilacji z wiersza polecenia](../../build/setting-the-path-and-environment-variables-for-command-line-builds.md)
