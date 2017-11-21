---
title: Tools.ini i NMAKE | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- NMAKE program, reading files
- Tools.ini and NMake
ms.assetid: ebd5eab6-ddf4-430e-bf4a-1db5bb84e344
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 638132f640fd342a752ec45541275178f6f26692
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="toolsini-and-nmake"></a>Tools.ini i NMAKE
NMAKE odczytuje Tools.ini przed odczytuje pliki reguł programu make, chyba że używana jest /R. Szuka Tools.ini najpierw w bieżącym katalogu, a następnie w katalogu określonym przez zmienną środowiskową INIT. W sekcji Ustawienia NMAKE pliku inicjującego rozpoczyna się od `[NMAKE]` i może zawierać żadnych informacji o pliku reguł programu make. Określ komentarz w osobnym wierszu rozpoczynający się od znaku numeru (#).  
  
## <a name="see-also"></a>Zobacz też  
 [Uruchomienie NMAKE](../build/running-nmake.md)