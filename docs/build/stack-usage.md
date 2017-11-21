---
title: "Stos użycia | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 383f0072-0438-489f-8829-cca89582408c
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c7a74abff7a2971fe66fa2df878078ac95f58fe8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="stack-usage"></a>Wykorzystanie stosu
Cała pamięć poza bieżący adres źródło jest uznawany za volatile: system operacyjny lub debugera, mogą zastąpić tę pamięć podczas sesji debugowania użytkownika lub obsługi przerwań. W związku z tym źródło musi być zawsze ustawiony przed podjęciem próby odczytu lub zapisu wartości do ramki stosu.  
  
 W tej sekcji omówiono alokację miejsca na stosie dla zmiennych lokalnych i **alloca** wewnętrznej.  
  
-   [Alokacja stosu](../build/stack-allocation.md)  
  
-   [Konstrukcja obszaru stosu parametru dynamicznego](../build/dynamic-parameter-stack-area-construction.md)  
  
-   [Typy funkcji](../build/function-types.md)  
  
-   [Wyrównanie — funkcja malloc](../build/malloc-alignment.md)  
  
-   [alloca](../build/alloca.md)  
  
## <a name="see-also"></a>Zobacz też  
 [x64 konwencje kodowania](../build/x64-software-conventions.md)