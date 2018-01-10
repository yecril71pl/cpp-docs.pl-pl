---
title: '&lt;streambuf&gt; | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: <streambuf>
dev_langs: C++
helpviewer_keywords: streambuf header
ms.assetid: 4365b25c-5831-488b-b9c2-867bfe961b89
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fa3e46d166ca1807d18caadcca94ec72020a1249
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ltstreambufgt"></a>&lt;streambuf&gt;
Dołącz nagłówek standardowy iostream \<streambuf > w celu zdefiniowania szablonu klasy [basic_streambuf —](../standard-library/basic-streambuf-class.md), która jest podstawowe działania w klasach iostream. Ten nagłówek znajduje się zwykle dla Ciebie przez inną nagłówków iostream; rzadko należy dołączyć go bezpośrednio.  
  
## <a name="syntax"></a>Składnia  
  
```  
#include <streambuf>  
  
```  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[streambuf](../standard-library/streambuf-typedefs.md#streambuf)|Specjalizacji `basic_streambuf` używającą `char` jako parametry szablonu.|  
|[wstreambuf](../standard-library/streambuf-typedefs.md#wstreambuf)|Specjalizacji `basic_streambuf` używającą `wchar_t` jako parametry szablonu.|  
  
### <a name="classes"></a>Klasy  
  
|||  
|-|-|  
|[basic_streambuf, klasa](http://msdn.microsoft.com/en-us/d9c706ba-ce01-43e0-b0b2-a558fc53ea8d)|Klasy szablonów opis abstrakcyjną klasę podstawową dla wyprowadzanie buforu strumienia, który kontroluje przesyłania elementów do i z reprezentację określonego strumienia.|  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)   
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream — programowanie](../standard-library/iostream-programming.md)   
 [Konwencje iostream](../standard-library/iostreams-conventions.md)



