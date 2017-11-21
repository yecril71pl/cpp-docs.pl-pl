---
title: Formaty daty godziny 32-bitowym systemie Windows | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.time
dev_langs: C++
helpviewer_keywords: 32-bit Windows
ms.assetid: ef1589db-84d7-4b24-8799-7c7a22cfe2bf
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 23f56a9ef86a33b99f1014cb2cf18a92bdfbd753
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="32-bit-windows-timedate-formats"></a>32-bitowe formaty daty/godziny systemu Windows
Data i godzina pliku są przechowywane oddzielnie, używając jako pól bitowych liczb całkowitych bez znaku. Data i godzina pliku są pakowane w następujący sposób:  
  
### <a name="time"></a>Godzina  
  
|Pozycja bitu:|0   1   2   3   4|5 6 7 8 9 A|B C D E F|  
|-------------------|-----------------------|---------------------------|-----------------------|  
|Długość:|5|6|5|  
|Zawartość:|godziny|minuty|zwiększa 2 sekundy|  
|Zakres wartości:|0-23|0-59|0-29 w 2-drugie odstępach czasu|  
  
### <a name="date"></a>Data  
  
|Pozycja bitu:|0   1   2   3   4   5   6|7 8 9 A|B C D E F|  
|-------------------|-------------------------------|-------------------|-----------------------|  
|Długość:|7|4|5|  
|Zawartość:|Roku|Miesiąc|dzień|  
|Zakres wartości:|0-119|1-12|1-31|  
||(względem 1980)|||  
  
## <a name="see-also"></a>Zobacz też  
 [Stałe globalne](../c-runtime-library/global-constants.md)