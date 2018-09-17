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
ms.openlocfilehash: e88ac63ace95ac0b9874dc3376210f3f5b4af320
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716658"
---
# <a name="link-environment-variables"></a>Zmienne środowiskowe LINK

Narzędzie łącze używane następujące zmienne środowiskowe:

- ŁĄCZA i \_łącze\_, jeśli została zdefiniowana. Narzędzie łącze dołącza opcje i argumenty zdefiniowanej zmiennej środowiskowej łącze i dołącza opcje i argumenty zdefiniowane w \_łącze\_ zmiennej środowiskowej, aby argumenty wiersza polecenia, przed rozpoczęciem przetwarzania.

- LIB, jeśli została zdefiniowana. Narzędzia łącze używa ścieżki LIB, aby wyszukać obiekt, bibliotekę lub inny plik określony w wierszu polecenia lub przez [/BASE](../../build/reference/base-base-address.md) opcji. Używa również ścieżki biblioteki można znaleźć pliku .pdb o nazwie w obiekcie. Lib — zmienna może zawierać specyfikacji ścieżki, oddzielając je średnikami. Jedna ścieżka musi wskazywać podkatalog \lib instalację programu Visual C++.

- ŚCIEŻKA, jeśli narzędzie musi zostać uruchomiony CVTRES i nie można odnaleźć pliku w tym samym katalogu co LINKU. (LINK wymaga CVTRES połączyć plik .res). ŚCIEŻKA musi wskazywać w podkatalogu \bin instalację programu Visual C++.

- TMP, aby określić katalog podczas łączenia OMF lub .res plików.

## <a name="see-also"></a>Zobacz też

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)<br/>
[Kompilowanie kodu C/C++ w wierszu polecenia](../../build/building-on-the-command-line.md)<br/>
[Ustawianie ścieżki i zmiennych środowiskowych dla kompilacji z wiersza polecenia](../../build/setting-the-path-and-environment-variables-for-command-line-builds.md)
