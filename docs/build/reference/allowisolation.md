---
title: -ALLOWISOLATION | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /ALLOWISOLATION
dev_langs:
- C++
helpviewer_keywords:
- -ALLOWISOLATION editbin option
- /ALLOWISOLATION editbin option
- ALLOWISOLATION editbin option
ms.assetid: 91430344-f64f-491a-a5a5-7ea3b21cbe68
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5cb92a7f31d48dad4a7fb608703c71ccc661e176
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368977"
---
# <a name="allowisolation"></a>/ALLOWISOLATION
Określa zachowanie wyszukiwania manifestu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
/ALLOWISOLATION[:NO]  
```  
  
## <a name="remarks"></a>Uwagi  
 **/ ALLOWISOLATION** powoduje, że system operacyjny do manifestu wyszukiwań i obciążeń.  
  
 **/ ALLOWISOLATION** jest ustawieniem domyślnym.  
  
 **/ALLOWISOLATION:No** wskazuje, że pliki wykonywalne zostały załadowane, tak jakby nie było żadnych manifestu i przyczyny [odwołanie EDITBIN](../../build/reference/editbin-reference.md) można ustawić `IMAGE_DLLCHARACTERISTICS_NO_ISOLATION` bitu w nagłówku opcjonalne `DllCharacteristics` pola.  
  
 Wyłączenie izolacji pliku wykonywalnego modułu ładującego systemu Windows nie próbuje znaleźć manifest aplikacji dla nowo utworzonego procesu. Nowy proces nie ma domyślny kontekst aktywacji, nawet jeśli brak manifestu w pliku wykonywalnym się lub jeśli brak manifestu, która ma nazwę *nazwę pliku wykonywalnego*. exe.manifest.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje polecenia EDITBIN](../../build/reference/editbin-options.md)   
 [/ ALLOWISOLATION (przeszukiwanie manifestu)](../../build/reference/allowisolation-manifest-lookup.md)   
 [Odwołanie do plików manifestu](http://msdn.microsoft.com/library/aa375632.aspx)