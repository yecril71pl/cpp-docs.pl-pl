---
title: Znaki specjalne w pliku reguł programu make | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, special characters
- makefiles, special characters
- special characters, in NMAKE macros
- macros, special characters
ms.assetid: 92c34ab5-ca6b-4fc0-bcf4-3172eaeda9f0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3ae77e769672dcc88a9dd41c901424c8c8150e6b
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45709367"
---
# <a name="special-characters-in-a-makefile"></a>Znaki specjalne w pliku reguł programu Make

Aby użyć znaków specjalnych NMAKE jako znak literałowy, należy umieścić znak daszka (^) przed nim. NMAKE ignoruje są daszka, które poprzedzają innych znaków. Znaki specjalne są:

`:  ;  #  (  )  $  ^  \  {  }  !  @  —`

Daszek (^) w ramach ciągów w cudzysłowach jest traktowana jako znak daszka literału. Karetkę na koniec wiersza Wstawia znak nowego wiersza literału ciągu lub makro.

W makrach, kreski ułamkowej odwróconej (\\) i nowego wiersza znakiem został zastąpiony spacją.

W poleceniach symbol procentu (%) jest określenie pliku. Do reprezentowania % dosłownie w poleceniu, należy określić podwójnego znaku procentu (%) zamiast jednego. W innych sytuacjach NMAKE interpretuje pojedynczego % dosłownie, ale zawsze interpretuje wartość o podwójnej precyzji %% jako pojedynczy %. W związku z tym do reprezentowania literału %%, określ albo znaki procentu trzech, %%%, lub symptomów cztery procent %%%.

Aby znak dolara ($) jest używany jako znak literałowy, za pomocą polecenia, należy określić dwa dolara ($). Ta metoda umożliwia także w innych sytuacjach, w którym ^ $ działa.

## <a name="see-also"></a>Zobacz też

[Zawartość pliku reguł programu Make](../build/contents-of-a-makefile.md)