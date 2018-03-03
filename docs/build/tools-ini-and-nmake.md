---
title: Tools.ini i NMAKE | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, reading files
- Tools.ini and NMake
ms.assetid: ebd5eab6-ddf4-430e-bf4a-1db5bb84e344
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0e4516c3206a08c2b9ee32aea4bbb669ce4cdf0d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="toolsini-and-nmake"></a>Tools.ini i NMAKE
NMAKE odczytuje Tools.ini przed odczytuje pliki reguł programu make, chyba że używana jest /R. Szuka Tools.ini najpierw w bieżącym katalogu, a następnie w katalogu określonym przez zmienną środowiskową INIT. W sekcji Ustawienia NMAKE pliku inicjującego rozpoczyna się od `[NMAKE]` i może zawierać żadnych informacji o pliku reguł programu make. Określ komentarz w osobnym wierszu rozpoczynający się od znaku numeru (#).  
  
## <a name="see-also"></a>Zobacz też  
 [Uruchomienie NMAKE](../build/running-nmake.md)