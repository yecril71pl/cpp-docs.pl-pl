---
title: Przy użyciu tchar —. Typy danych H z kodem _MBCS | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- tchar.h
- TCHAR
dev_langs:
- C++
helpviewer_keywords:
- mapping generic-text
- generic-text data types [C++]
- generic-text mappings [C++]
- MBCS [C++], generic-text mappings
- TCHAR.H data types, mapping
- mappings [C++], TCHAR.H
ms.assetid: 298583c5-22c3-40f6-920e-9ec96d42abd8
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e80ecd123e3fc47705563156e33f46ecd99a0321
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33858357"
---
# <a name="using-tcharh-data-types-with-mbcs-code"></a>Używanie typów danych TCHAR.H z kodem _MBCS
Gdy manifestu stała **_MBCS** jest zdefiniowana, danej procedury zwykłego tekstu mapuje jedną z następujących rodzajów procedury:  
  
-   Procedura SBCS odpowiednio obsługuje wielobajtowe bajtów, znaków i ciągów. W takim przypadku argumenty ciągu powinny być typu **char\***. Na przykład `_tprintf` mapuje `printf`; argumenty ciągu `printf` typu **char\***. Jeśli używasz **_tchar —** typy danych — zwykły tekst typ ciągu, typy formalnego i rzeczywistego parametru dla `printf` zgodna z powodu **_tchar —** \* mapuje **char \***.  
  
-   Procedury dotyczące MBCS. W takim przypadku argumenty ciągu powinny być typu `unsigned` **char\***. Na przykład `_tcsrev` mapuje `_mbsrev`, która oczekuje i zwraca ciąg typu `unsigned` **char\***. Jeśli używasz **_tchar —** danych — zwykły tekst wpisz swój typ string jest potencjalnych konfliktów typu, ponieważ **_tchar —** mapy na typ `char`.  
  
 Poniżej przedstawiono trzy rozwiązania zapobiegania tej konflikt typu (i ostrzeżenia kompilatora C lub C++ błędów, które umożliwiałyby):  
  
-   Zachowanie domyślne. Tchar.h zawiera procedury w bibliotekach środowiska wykonawczego, jak w poniższym przykładzie prototypy rutynowych zwykłego tekstu.  
  
    ```  
    char * _tcsrev(char *);  
    ```  
  
     W przypadku domyślnej prototypu dla `_tcsrev` mapuje `_mbsrev` za pośrednictwem thunk w Libc.lib. Spowoduje to zmianę typów `_mbsrev` parametry przychodzące i wychodzące wartością zwracaną z **_tchar — \***  (to znaczy `char` **\***) do `unsigned` `char` **\***. Ta metoda gwarantuje dopasowania, gdy jest używany typ **_tchar —**, ale jest stosunkowo powolne ze względu na obciążenie wywołania funkcji.  
  
-   Funkcja ze śródwierszowaniem przez włączenie następującą instrukcję preprocesora w kodzie.  
  
    ```  
    #define _USE_INLINING  
    ```  
  
     Ta metoda powoduje thunk funkcji wbudowanej, podany w pliku Tchar.h do mapowania bezpośrednio do odpowiedniej procedury MBCS procedury zwykłego tekstu. Poniższy fragment kodu z Tchar.h zawiera przykład jak to zrobić.  
  
    ```  
    __inline char *_tcsrev(char *_s1)  
    {return (char *)_mbsrev((unsigned char *)_s1);}  
    ```  
  
     W przypadku korzystania ze śródwierszowaniem, jest najlepszym rozwiązaniem, ponieważ gwarantuje to typ dopasowania i ma koszt nie dodatkowy czas.  
  
-   Za pomocą bezpośredniego mapowania zawierających następującą instrukcję preprocesora w kodzie.  
  
    ```  
    #define _MB_MAP_DIRECT  
    ```  
  
     Metoda ta umożliwia szybkie alternatywne, jeśli nie chcesz używać domyślnego zachowania lub nie można użyć ze śródwierszowaniem. Powoduje procedury zwykłego tekstu można mapować przez makro bezpośrednio do wersji MBCS procedury, jak w poniższym przykładzie z Tchar.h.  
  
    ```  
    #define _tcschr _mbschr  
    ```  
  
     Po zastosowaniu takiego podejścia, należy zachować ostrożność upewnić się na użytek typów danych odpowiednie argumenty typu string i zwracanych wartości ciągu. Rzutowanie typów służy do zapewnienia odpowiedniego typu dopasowania lub skorzystać z **_txchar —** — typ danych — zwykły tekst. **_Txchar —** mapy na typ `char` w kodzie SBCS, ale mapy na typ `unsigned` `char` w kodzie MBCS. Aby uzyskać więcej informacji na temat makra zwykłego tekstu, zobacz [mapowania zwykłego tekstu](../c-runtime-library/generic-text-mappings.md) w *odwołanie do biblioteki wykonawczej*.  
  
## <a name="see-also"></a>Zobacz też  
 [Mapowania typ ogólny-tekst w pliku Tchar.h](../text/generic-text-mappings-in-tchar-h.md)