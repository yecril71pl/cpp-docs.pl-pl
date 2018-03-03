---
title: Strumienie Byte oraz szerokie | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Byte and Wide Streams
dev_langs:
- C++
helpviewer_keywords:
- byte streams
- wide streams
ms.assetid: 61ef0587-4cbc-4eb8-aae5-4c298dbbc6f9
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4d09e110fd428b13e501647d97a0878df0e9392a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="byte-and-wide-streams"></a>Strumienie byte oraz szerokie
Strumień bajtów traktuje pliku jako sekwencję bajtów. W programie strumień jest identyczne sekwencję bajtów.  
  
 Z kolei szeroki strumienia traktuje pliku jako sekwencję uogólniony wielobajtowe znaki, które mogą mieć szeroki zakres reguły kodowania. (Binarnego i tekstu pliki są nadal odczytać i zapisać w sposób opisany wcześniej.) W programie strumienia wygląda odpowiedniej sekwencji znaki dwubajtowe. Konwersje między dwoma reprezentacje przeprowadzone w ciągu standardowa biblioteka języka C. Reguły konwersji mogą w zasadzie można zmienić przez wywołanie do [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) który zmienia kategorię `LC_CTYPE`. Każdego strumienia szeroki określa jego reguły konwersji w czasie staje się całego obiektowe i zachowa tych zasad, nawet jeśli kategoria `LC_CTYPE` zmienia się później.  
  
 Pozycjonowanie w ramach szerokiej strumienia wystąpi te same ograniczenia jak w przypadku steams tekstu. Ponadto wskaźnika położenia pliku może być również radzenia sobie z kodowanie zależne od stanu. Zwykle obejmuje zarówno Przesunięcie bajtów, w ramach strumienia i typu obiektu `mbstate_t`. W związku z tym tylko niezawodnym sposobem uzyskania położenie pliku, w ramach szerokiej strumień jest wywołując [fgetpos —](../c-runtime-library/reference/fgetpos.md), i tylko niezawodnym sposobem przywrócenia pozycji uzyskane w ten sposób jest wywołując [fsetpos —](../c-runtime-library/reference/fsetpos.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Pliki i strumienie](../c-runtime-library/files-and-streams.md)   
 [setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)