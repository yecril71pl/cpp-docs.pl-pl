---
title: Stos użycia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 383f0072-0438-489f-8829-cca89582408c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b6f711636089a6f2966002002220aac88cebe17a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379861"
---
# <a name="stack-usage"></a>Wykorzystanie stosu
Cała pamięć poza bieżący adres źródło jest uznawany za volatile: system operacyjny lub debugera, mogą zastąpić tę pamięć podczas sesji debugowania użytkownika lub obsługi przerwań. W związku z tym źródło musi być zawsze ustawiony przed podjęciem próby odczytu lub zapisu wartości do ramki stosu.  
  
 W tej sekcji omówiono alokację miejsca na stosie dla zmiennych lokalnych i **alloca** wewnętrznej.  
  
-   [Alokacja stosu](../build/stack-allocation.md)  
  
-   [Konstrukcja obszaru stosu parametru dynamicznego](../build/dynamic-parameter-stack-area-construction.md)  
  
-   [Typy funkcji](../build/function-types.md)  
  
-   [malloc, wyrównanie](../build/malloc-alignment.md)  
  
-   [alloca](../build/alloca.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Konwencje kodowania x64](../build/x64-software-conventions.md)