---
title: Przy użyciu tchar —. Typy danych H z _MBCS | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
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
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 20079fcaae1124fa97a1e66a787bfb68e607564c
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="using-tcharh-data-types-with-mbcs"></a>Używanie typów danych TCHAR.H z _MBCS

**Microsoft Specific**

Jak wskazuje tabeli rutynowych mapowania zwykłego tekstu (zobacz [mapowania zwykłego tekstu](../c-runtime-library/generic-text-mappings.md)), gdy manifestu stała **_MBCS** jest zdefiniowana, danej procedury zwykłego tekstu mapuje jedną z następujących rodzajów z procedury:

- Procedura SBCS odpowiednio obsługuje wielobajtowe bajtów, znaków i ciągów. W takim przypadku argumenty ciągu powinny być typu **char&#42;**. Na przykład **_tprintf —** mapuje **printf**; argumenty ciągu **printf** typu **char&#42;**. Jeśli używasz **_tchar —** typy danych — zwykły tekst typ ciągu, typy formalnego i rzeczywistego parametru dla **printf** zgodna z powodu **_tchar —&#42;**  mapuje **char&#42;**.

- Procedury dotyczące MBCS. W takim przypadku argumenty ciągu powinny być typu __unsigned char&#42;__. Na przykład **_tcsrev —** mapuje **_mbsrev —**, która oczekuje i zwraca ciąg typu __unsigned char&#42;__. Ponownie Jeśli używasz **_tchar —** danych — zwykły tekst wpisz swój typ string jest potencjalnych konfliktów typu, ponieważ **_tchar —** mapy na typ **char**.

 Poniżej przedstawiono trzy rozwiązania zapobiegania tej konflikt typu (i ostrzeżenia kompilatora C lub C++ błędów, które umożliwiałyby):

- Zachowanie domyślne. TCHAR —. H przewiduje procedury w bibliotekach środowiska wykonawczego, jak w poniższym przykładzie prototypy rutynowych zwykłego tekstu.

   ```C
   char *_tcsrev(char *);
   ```

   W przypadku domyślnej prototypu dla **_tcsrev —** mapuje **_mbsrev —** za pośrednictwem thunk w Biblioteka LIBC. LIB. Spowoduje to zmianę typów **_mbsrev —** parametry przychodzące i wychodzące wartością zwracaną z **_tchar — &#42;**  (takich jak **char &#42;** ) do **unsigned char &#42;**. Ta metoda gwarantuje dopasowania, gdy jest używany typ **_tchar —**, ale jest stosunkowo powolne ze względu na obciążenie wywołania funkcji.

- Funkcja ze śródwierszowaniem przez włączenie następującą instrukcję preprocesora w kodzie.

   ```C
   #define _USE_INLINING
   ```

   Ta metoda powoduje thunk funkcji wbudowanej, podany w tchar —. H do mapowania bezpośrednio do odpowiedniej procedury MBCS procedury zwykłego tekstu. Poniższy fragment kodu z tchar —. H przykład jak to zrobić.

   ```C
   __inline char *_tcsrev(char *_s1)
   {return (char *)_mbsrev((unsigned char *)_s1);}
   ```

   W przypadku korzystania ze śródwierszowaniem, jest najlepszym rozwiązaniem, ponieważ gwarantuje to typ dopasowania i ma koszt nie dodatkowy czas.

- Aby użyć "bezpośredniego mapowania" Dołączanie następującą instrukcję preprocesora w kodzie.

   ```C
   #define _MB_MAP_DIRECT
   ```

   Metoda ta umożliwia szybkie alternatywne, jeśli nie chcesz używać domyślnego zachowania lub nie można użyć ze śródwierszowaniem. Powoduje procedury zwykłego tekstu można mapować przez makro bezpośrednio do wersji MBCS procedury, jak w poniższym przykładzie z tchar —. H.

   ```C
   #define _tcschr _mbschr
   ```

Po zastosowaniu takiego podejścia, należy zachować ostrożność upewnić się, że odpowiedni typ danych używane są argumenty typu string i zwracanych wartości ciągu. Rzutowanie typów służy do zapewnienia odpowiedniego typu dopasowania lub skorzystać z **_txchar —** — typ danych — zwykły tekst. **_Txchar —** mapy na typ **char** w kodzie SBCS, ale mapy na typ **unsigned char** w kodzie MBCS. Aby uzyskać więcej informacji na temat makra zwykłego tekstu, zobacz [mapowania zwykłego tekstu](../c-runtime-library/generic-text-mappings.md).

**KOŃCOWY określonych firmy Microsoft**

## <a name="see-also"></a>Zobacz też

[Internacjonalizacja](../c-runtime-library/internationalization.md)<br/>
[Universal C procedury czasu wykonywania według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
