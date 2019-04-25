---
title: Tools.ini i NMAKE
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, reading files
- Tools.ini and NMake
ms.assetid: ebd5eab6-ddf4-430e-bf4a-1db5bb84e344
ms.openlocfilehash: 38eebb3aaf07438da85b0cfe6bd3f26fb5d6db29
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62317682"
---
# <a name="toolsini-and-nmake"></a>Tools.ini i NMAKE

NMAKE odczytuje Tools.ini przed odczytuje pliki reguł programu make, chyba że używana jest/r. Szuka Tools.ini najpierw w bieżącym katalogu, a następnie w katalogu określonym przez zmienną środowiskową INIT. Zaczyna się w sekcji Ustawienia NMAKE w pliku inicjującym `[NMAKE]` i mogą zawierać wszystkie informacje w pliku reguł programu make. Określ komentarz na oddzielnych wiersz zaczynający się od znaku numeru (#).

## <a name="see-also"></a>Zobacz także

[Uruchomienie NMAKE](running-nmake.md)
