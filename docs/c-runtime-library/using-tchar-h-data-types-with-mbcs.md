---
title: "Przy użyciu tchar —. Typy danych H z _MBCS | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _mbcs
dev_langs:
- C++
helpviewer_keywords:
- TCHAR.H data types
- MBCS data type
- _MBCS data type
ms.assetid: 48f471e7-9d2b-4a39-b841-16a0e15c0a18
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 05f2a5ae3ccf2ec8b9d9c1766bd5b02ed43dfbf7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="using-tcharh-data-types-with-mbcs"></a>Używanie typów danych TCHAR.H z _MBCS
**Dotyczące firmy Microsoft**  
  
 Jak wskazuje tabeli rutynowych mapowania zwykłego tekstu (zobacz [mapowania zwykłego tekstu](../c-runtime-library/generic-text-mappings.md)), gdy manifestu stała `_MBCS` jest zdefiniowana, danej procedury zwykłego tekstu mapuje jedną z następujących rodzajów procedury:  
  
-   Procedura SBCS odpowiednio obsługuje wielobajtowe bajtów, znaków i ciągów. W takim przypadku argumenty ciągu powinny być typu `char*`. Na przykład `_tprintf` mapuje `printf`; argumenty ciągu `printf` typu `char*`. Jeśli używasz `_TCHAR` typy danych — zwykły tekst typ ciągu, typy formalnego i rzeczywistego parametru dla `printf` zgodna z powodu `_TCHAR*` mapuje `char*`.  
  
-   Procedury dotyczące MBCS. W takim przypadku argumenty ciągu powinny być typu `unsigned char*`. Na przykład `_tcsrev` mapuje `_mbsrev`, która oczekuje i zwraca ciąg typu `unsigned char*`. Ponownie Jeśli używasz `_TCHAR` danych — zwykły tekst wpisz swój typ string jest potencjalnych konfliktów typu, ponieważ `_TCHAR` mapy na typ `char`.  
  
 Poniżej przedstawiono trzy rozwiązania zapobiegania tej konflikt typu (i ostrzeżenia kompilatora C lub C++ błędów, które umożliwiałyby):  
  
-   Zachowanie domyślne. TCHAR —. H przewiduje procedury w bibliotekach środowiska wykonawczego, jak w poniższym przykładzie prototypy rutynowych zwykłego tekstu.  
  
    ```  
    char *_tcsrev(char *);  
    ```  
  
     W przypadku domyślnej prototypu dla `_tcsrev` mapuje `_mbsrev` za pośrednictwem thunk w Biblioteka LIBC. LIB. Spowoduje to zmianę typów `_mbsrev` parametry przychodzące i wychodzące wartością zwracaną z `_TCHAR *` (takich jak `char *`) do `unsigned char *`. Ta metoda gwarantuje dopasowania, gdy jest używany typ `_TCHAR`, ale jest stosunkowo powolne ze względu na obciążenie wywołania funkcji.  
  
-   Funkcja ze śródwierszowaniem przez włączenie następującą instrukcję preprocesora w kodzie.  
  
    ```  
    #define _USE_INLINING  
    ```  
  
     Ta metoda powoduje thunk funkcji wbudowanej, podany w tchar —. H do mapowania bezpośrednio do odpowiedniej procedury MBCS procedury zwykłego tekstu. Poniższy fragment kodu z tchar —. H przykład jak to zrobić.  
  
    ```  
    __inline char *_tcsrev(char *_s1)  
    {return (char *)_mbsrev((unsigned char *)_s1);}  
    ```  
  
     W przypadku korzystania ze śródwierszowaniem, jest najlepszym rozwiązaniem, ponieważ gwarantuje to typ dopasowania i ma koszt nie dodatkowy czas.  
  
-   Aby użyć "bezpośredniego mapowania" Dołączanie następującą instrukcję preprocesora w kodzie.  
  
    ```  
    #define _MB_MAP_DIRECT  
    ```  
  
     Metoda ta umożliwia szybkie alternatywne, jeśli nie chcesz używać domyślnego zachowania lub nie można użyć ze śródwierszowaniem. Powoduje procedury zwykłego tekstu można mapować przez makro bezpośrednio do wersji MBCS procedury, jak w poniższym przykładzie z tchar —. H.  
  
    ```  
    #define _tcschr _mbschr  
    ```  
  
 Po zastosowaniu takiego podejścia, należy zachować ostrożność upewnić się, że odpowiedni typ danych używane są argumenty typu string i zwracanych wartości ciągu. Rzutowanie typów służy do zapewnienia odpowiedniego typu dopasowania lub skorzystać z `_TXCHAR` typ danych — zwykły tekst. `_TXCHAR`mapy na typ `char` w kodzie SBCS, ale mapy na typ `unsigned char` w kodzie MBCS. Aby uzyskać więcej informacji na temat makra zwykłego tekstu, zobacz [mapowania zwykłego tekstu](../c-runtime-library/generic-text-mappings.md).  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Przystosowywanie do warunków międzynarodowych](../c-runtime-library/internationalization.md)   
 [Procedury czasu wykonywania według kategorii](../c-runtime-library/run-time-routines-by-category.md)