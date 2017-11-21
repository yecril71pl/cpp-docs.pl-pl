---
title: "Trigramów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ??) trigraph
- ??- trigraph
- question mark, in trigraphs
- ??= trigraph
- ?? trigraph
- ??< trigraph
- ??/ trigraph
- trigraphs
- '? symbol, trigraph'
- ??> trigraph
- ??! trigraph
- ??' trigraph
ms.assetid: 617f76ec-b8e8-4cfe-916c-4bc32cbd9aeb
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a480a38411536266c8cd4c23f8b29190550d3444
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="trigraphs"></a>Trigramy
Źródłowy zestaw znaków programów źródłowych języka C jest zawarty w 7-bitowym zestawie znaków ASCII, ale jest nadzbiorem niezmiennego zestawu kodów ISO 646-1983. Sekwencje trójznaków pozwalają programom języka C na zapisywanie tylko przy użyciu niezmiennego zestawu kodów ISO (Międzynarodowej Organizacji Normalizacyjnej). Trójznaki są sekwencjami trzech znaków (rozpoczętymi przez dwa kolejne znaki zapytania), które kompilator zamienia na odpowiadający im znak interpunkcyjny. Możesz używać trójznaków w plikach źródłowych języka C z zestawem znaków, który nie zawiera wygodnych reprezentacji graficznych dla niektórych znaków interpunkcyjnych.  
  
 C ++ 17 usuwa trigramów od języka. Implementacje mogą w dalszym ciągu obsługuje trigramów jako część mapowania zdefiniowane w implementacji z pliku fizycznego źródła *zestaw znaków źródła podstawowe*, ale standardowego zachęca implementacji nie robić. Za pomocą języka C ++ 14 trigramów są obsługiwane, jak C.  
  
 Visual C++ w dalszym ciągu obsługuje — trigram podstawienia, ale jest domyślnie wyłączona. Aby uzyskać informacje o sposobie włączania podstawienia — trigram, zobacz [/Zc: trigraphs (podstawianie Trigramów)](../build/reference/zc-trigraphs-trigraphs-substitution.md).  
  
 Poniższa tabela pokazuje dziewięć sekwencji trójznaków. Wszystkie wystąpienia znaków interpunkcyjnych z pierwszej kolumny są zamieniane w pliku źródłowym na odpowiadający znak z drugiej kolumny.  
  
### <a name="trigraph-sequences"></a>Sekwencje trójznakowe  
  
|Trójznak|Znak interpunkcyjny|  
|--------------|---------------------------|  
|??=|#|  
|??(|[|  
|??/|\|  
|??)|]|  
|??'|^|  
|??\<|{|  
|??!|&#124;|  
|??>|}|  
|??-|~|  
  
 Trójznak jest zawsze traktowany jako pojedynczy znak źródłowy. W tłumaczeniu wartości trigramów odbywa się w pierwszym [fazy tłumaczenia](../preprocessor/phases-of-translation.md), przed rozpoznawania znaki specjalne w Literały ciągu i znak stałe. Rozpoznawane jest tylko dziewięć trójznaków pokazanych w powyższej tabeli. Wszystkie inne sekwencje znaków są pozostawiane nieprzetłumaczone.  
  
 Sekwencja ucieczki znaku  **\\?**, uniemożliwia błędnej interpretacji sekwencje znaków — trigram podobne. (Aby uzyskać informacje o sekwencji unikowych, zobacz [sekwencji unikowych](../c-language/escape-sequences.md).) Na przykład, jeśli spróbujesz wydrukować ciąg `What??!` za pomocą instrukcji `printf`  
  
```  
printf( "What??!\n" );  
```  
  
 Parametry podane są `What|` ponieważ `??!` jest sekwencją — trigram, która zostanie zastąpiona `|` znaków. Napisz instrukcję w następujący sposób, aby poprawnie wydrukować ciąg:  
  
```  
printf( "What?\?!\n" );  
```  
  
 W tej instrukcji `printf`, znak ucieczki ukośnika odwrotnego przed drugim znakiem zapytania zapobiega błędnej interpretacji `??!` jako trójznaku.  
  
## <a name="see-also"></a>Zobacz też  
 [/ Zc: trigraphs (podstawianie trigramów)](../build/reference/zc-trigraphs-trigraphs-substitution.md)   
 [Identyfikatory języka C](../c-language/c-identifiers.md)