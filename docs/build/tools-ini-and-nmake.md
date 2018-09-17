---
title: Tools.ini i NMAKE | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, reading files
- Tools.ini and NMake
ms.assetid: ebd5eab6-ddf4-430e-bf4a-1db5bb84e344
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 84406886c9aa0c0053ed7c183912bf8a7f1f4771
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45723583"
---
# <a name="toolsini-and-nmake"></a>Tools.ini i NMAKE

NMAKE odczytuje Tools.ini przed odczytuje pliki reguł programu make, chyba że używana jest/r. Szuka Tools.ini najpierw w bieżącym katalogu, a następnie w katalogu określonym przez zmienną środowiskową INIT. Zaczyna się w sekcji Ustawienia NMAKE w pliku inicjującym `[NMAKE]` i mogą zawierać wszystkie informacje w pliku reguł programu make. Określ komentarz na oddzielnych wiersz zaczynający się od znaku numeru (#).

## <a name="see-also"></a>Zobacz też

[Uruchomienie NMAKE](../build/running-nmake.md)