---
title: Na podstawie Pointers (C) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- __based keyword [C]
- based pointers
- pointers, based
- based addressing
ms.assetid: b5446920-89e0-4e2f-91f3-1f2a769a08e8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b414110b0f3367c2b589f82915f417ea7389d738
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32381286"
---
# <a name="based-pointers-c"></a>Wskaźniki bazowe (C)
**Microsoft Specific**  
  
 [__based — (odwołanie w języku C++)](../cpp/based-pointers-cpp.md)  
  
 Kompilatory C Microsoft 32-bitowe i 64-bitowe wskaźnik bazowy jest 32-bitowy lub 64-bitowe przesunięcie z 32-bitowy lub 64-bitowych wskaźnik podstawowy. Adresowanie na podstawie jest przydatne w przypadku sprawowanie kontroli nad sekcje, w których obiekty są przydzielone, a tym samym zmniejszenie rozmiaru pliku wykonywalnego i zwiększenia szybkości wykonywania. Ogólnie rzecz biorąc jest formularz służący do określania oparte na wskaźnik  
  
```  
  
type  
__based(  
base  
)  
declarator  
  
```  
  
 "Na podstawie wskaźnika" wariant oparte na rozwiązaniu umożliwia specyfikacji wskaźnikiem jako podstawy. Wskaźnik bazowy, wówczas przesunięcie w sekcji Pamięć początkowa wskaźnika, na którym jest oparty na początku. Wskaźniki oparte na adresach wskaźnika są jedynymi `__based` — słowo kluczowe prawidłowy w kompilacjach kodu 32-bitowe i 64-bitowych. W takich kompilacje są przemieszczanie 32-bitowy lub 64-bitowym z podstawowej 32-bitowy lub 64-bitowej.  
  
 Jeden na użytek wskaźniki oparte na wskaźnikach jest trwały identyfikatorów, które zawierają wskaźniki. Listy połączonej, która składa się z wskaźniki oparte na wskaźnik można można zapisywane na dysku, a następnie ponownie załadować do innego miejsca w pamięci, za pomocą wskaźniki pozostałych prawidłowe.  
  
 W poniższym przykładzie przedstawiono wskaźnika, w oparciu o wskaźnik.  
  
```  
void *vpBuffer;  
  
struct llist_t  
{  
    void __based( vpBuffer ) *vpData;  
    struct llist_t __based( vpBuffer ) *llNext;  
};  
```  
  
 Wskaźnik `vpBuffer` ma przypisany adres pamięci przydzielonej w pewnym momencie nowsze w programie. Listy połączonej został przeniesiony z uwzględnieniem wartości `vpBuffer`.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Deklaratory i deklaracje zmiennych](../c-language/declarators-and-variable-declarations.md)