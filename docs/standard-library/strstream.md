---
title: "&lt;strstream —&gt; | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: <strstream>
dev_langs: C++
helpviewer_keywords: strstream header
ms.assetid: eaa9d0d4-d217-4f28-8a68-9b9ad7b1c0f5
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0487fc2aa09568523c6a7d0bbcf4973beee309ed
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ltstrstreamgt"></a>&lt;strstream —&gt;
Definiuje kilka klas, które obsługują operacje iostream sekwencji przechowywane w tablicy przydzielone `char` obiektu. Takie sekwencje są łatwo konwertowane do i z ciągów C.  
  
## <a name="syntax"></a>Składnia  
  
```  
#include <strstream>  
  
```  
  
## <a name="remarks"></a>Uwagi  
 Obiekty typu `strstream` współpracują `char` *, które są ciągami C. Użyj [ \<sstream — >](../standard-library/sstream.md) do pracy z obiektami typu [basic_string —](../standard-library/basic-string-class.md).  
  
> [!NOTE]
>  Klasy w `<strstream>` są przestarzałe. Rozważ użycie klasy w `<sstream>` zamiast tego.  
  
### <a name="classes"></a>Klasy  
  
|||  
|-|-|  
|[strstreambuf — klasa](../standard-library/strstreambuf-class.md)|Klasa opisuje buforu strumienia, który kontroluje przesyłania elementów do i z sekwencję elementy przechowywane w `char` tablicy obiektów.|  
|[istrstream — klasa](../standard-library/istrstream-class.md)|Klasa opisuje obiekt, który kontroluje wyodrębniania elementów i zakodowanego obiektów z buforu strumienia klasy [strstreambuf —](../standard-library/strstreambuf-class.md).|  
|[ostrstream — klasa](../standard-library/ostrstream-class.md)|Klasa opisuje obiekt, który kontroluje wstawiania elementów i obiektów zakodowanych do buforu strumienia klasy [strstreambuf —](../standard-library/strstreambuf-class.md).|  
|[strstream — klasa](../standard-library/strstream-class.md)|Klasa opisuje obiekt, który kontroluje wstawiania i wyodrębniania elementów i obiektów zakodowany przy użyciu buforu strumienia klasy [strstreambuf —](../standard-library/strstreambuf-class.md).|  
  
## <a name="see-also"></a>Zobacz też  
 [\<strstream — >](../standard-library/strstream.md)   
 [Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)   
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream — programowanie](../standard-library/iostream-programming.md)   
 [Konwencje iostream](../standard-library/iostreams-conventions.md)



