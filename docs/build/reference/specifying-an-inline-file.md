---
title: Określanie pliku wbudowanego
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, inline files
- inline files [C++], specifying NMAKE
- files [C++], inline
ms.assetid: 393eccfb-3fc9-4bac-a30c-8ac8d221cca3
ms.openlocfilehash: 7eb123ef3f2115df5c65d266630bded8cb54baae
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823949"
---
# <a name="specifying-an-inline-file"></a>Określanie pliku wbudowanego

Określ dwa nawiasy (<<) w poleceniu gdzie *filename* jest wyświetlany. Nawiasy kątowe nie może być rozwinięciu makra.

## <a name="syntax"></a>Składnia

```
<<[filename]
```

## <a name="remarks"></a>Uwagi

Po uruchomieniu polecenia nawiasy kątowe są zastępowane przez *filename*, jeśli określono lub przez unikatową nazwę generowane NMAKE. Jeśli zostanie określony, *filename* muszą być zgodne nawiasy kątowe, bez spacji lub tabulatorów. Ścieżka jest dozwolone. Rozszerzenie nie jest wymagane lub zakłada, że. Jeśli *filename* jest określony, plik jest tworzony w bieżącej lub określony katalog zastąpienie wszystkich istniejących plików o takiej nazwie; w przeciwnym razie jest tworzony w katalogu TMP (lub bieżącego katalogu, jeśli zmienna środowiskowa TMP nie zdefiniowano). Jeśli poprzednie *filename* jest używane ponownie, NMAKE zastępuje poprzedni plik.

## <a name="see-also"></a>Zobacz także

[Pliki wbudowane w pliku reguł programu Make](inline-files-in-a-makefile.md)
