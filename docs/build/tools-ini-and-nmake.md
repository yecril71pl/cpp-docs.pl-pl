---
title: Tools.ini i NMAKE
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, reading files
- Tools.ini and NMake
ms.assetid: ebd5eab6-ddf4-430e-bf4a-1db5bb84e344
ms.openlocfilehash: 1a8673741cb49c504855fb1af00dbdc06379210d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50654418"
---
# <a name="toolsini-and-nmake"></a>Tools.ini i NMAKE

NMAKE odczytuje Tools.ini przed odczytuje pliki reguł programu make, chyba że używana jest/r. Szuka Tools.ini najpierw w bieżącym katalogu, a następnie w katalogu określonym przez zmienną środowiskową INIT. Zaczyna się w sekcji Ustawienia NMAKE w pliku inicjującym `[NMAKE]` i mogą zawierać wszystkie informacje w pliku reguł programu make. Określ komentarz na oddzielnych wiersz zaczynający się od znaku numeru (#).

## <a name="see-also"></a>Zobacz też

[Uruchomienie NMAKE](../build/running-nmake.md)