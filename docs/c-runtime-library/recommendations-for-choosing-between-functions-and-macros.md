---
title: Zalecenia dotyczące wybierania pomiędzy funkcjami i makrami | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.functions
dev_langs:
- C++
helpviewer_keywords:
- functions [CRT], vs. macros
- macros, vs. functions
ms.assetid: 18a633d6-cf1c-470c-a649-fa7677473e2b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4577ac1a0e1cac90a3436809722978d119c6b557
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32389637"
---
# <a name="recommendations-for-choosing-between-functions-and-macros"></a>Zalecenia dotyczące wybierania pomiędzy funkcjami i makrami
Większość procedury biblioteki wykonawczej firmy Microsoft są kompilowane lub złożonego funkcji, ale niektóre procedury są zaimplementowane jako makra. Gdy plik nagłówka deklaruje zarówno funkcję, jak i wersji makro procedury, definicji makra ma pierwszeństwo, ponieważ zawsze jest wyświetlany po deklaracji funkcji. Po wywołaniu procedury, który jest implementowany jako funkcję i makra, możesz wymusić kompilatora, aby korzystać z funkcji wersji na dwa sposoby:  
  
-   Rutynowe nazwę należy ująć w nawias.  
  
    ```  
    #include <ctype.h>  
    a = _toupper(a);    // Use macro version of toupper.  
    a = (_toupper)(a);  // Force compiler to use   
                        // function version of toupper.  
    ```  
  
-   "Usuń" definicji makra z `#undef` dyrektywy:  
  
    ```  
    #include <ctype.h>  
    #undef _toupper  
    ```  
  
 Musisz wybrać jedną z funkcji i makra stosowania procedury biblioteki, należy wziąć pod uwagę następujące możliwości:  
  
-   **Szybkość i rozmiar** Największą zaletą przy użyciu makra jest krótszy czas wykonywania. Podczas przetwarzania wstępnego, makro jest rozwinięta (zastąpionych przez jego definicję) wbudowany zawsze jest używany. Definicja funkcji występuje tylko jeden raz, niezależnie od tego, ile razy jest wywoływana. Makra może zwiększyć rozmiar kodu, ale nie mają obciążenia związanego z wywołania funkcji.  
  
-   **Obliczanie funkcji** funkcji obliczane jako adres; nie obsługuje makra. W związku z tym nie można użyć nazwy makra w kontekstach wymagające wskaźnik. Na przykład można zadeklarować wskaźnika do funkcji, ale nie wskaźnika do makra.  
  
-   **Sprawdzanie typu** zadeklarowania funkcji, kompilator sprawdzić typy argumentów. Ponieważ nie można zadeklarować makra, kompilator nie może sprawdzić typy argumentów makra; Mimo że można sprawdzić liczbę argumentów przekazywane do makra.  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteka CRT, funkcje](../c-runtime-library/crt-library-features.md)