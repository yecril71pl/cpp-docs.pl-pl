---
title: Określanie pliku wbudowanego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, inline files
- inline files [C++], specifying NMAKE
- files [C++], inline
ms.assetid: 393eccfb-3fc9-4bac-a30c-8ac8d221cca3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 73983094f10088920100b4fbbb8d870aee13f05e
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45720567"
---
# <a name="specifying-an-inline-file"></a>Określanie pliku wbudowanego

Określ dwa nawiasy (<<) w poleceniu gdzie *filename* jest wyświetlany. Nawiasy kątowe nie może być rozwinięciu makra.

## <a name="syntax"></a>Składnia

```
<<[filename]
```

## <a name="remarks"></a>Uwagi

Po uruchomieniu polecenia nawiasy kątowe są zastępowane przez *filename*, jeśli określono lub przez unikatową nazwę generowane NMAKE. Jeśli zostanie określony, *filename* muszą być zgodne nawiasy kątowe, bez spacji lub tabulatorów. Ścieżka jest dozwolone. Rozszerzenie nie jest wymagane lub zakłada, że. Jeśli *filename* jest określony, plik jest tworzony w bieżącej lub określony katalog zastąpienie wszystkich istniejących plików o takiej nazwie; w przeciwnym razie jest tworzony w katalogu TMP (lub bieżącego katalogu, jeśli zmienna środowiskowa TMP nie zdefiniowano). Jeśli poprzednie *filename* jest używane ponownie, NMAKE zastępuje poprzedni plik.

## <a name="see-also"></a>Zobacz też

[Pliki wbudowane w pliku reguł programu Make](../build/inline-files-in-a-makefile.md)