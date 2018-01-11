---
title: '&lt;IStream&gt; | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- istream/std::<istream>
- <istream>
- std::<istream>
dev_langs: C++
helpviewer_keywords: istream header
ms.assetid: efcf24e4-05d1-4719-ab0b-9e7ebe845d89
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 570a23dff65c6c4838d85083b25507bbf0f68e44
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ltistreamgt"></a>&lt;IStream&gt;
Definiuje basic_istream szablonu klasy —, które przekazuje ekstrakcje dla iostream, i basic_iostream szablonu klasy —, które przekazuje zarówno wstawienia i ekstrakcje. Nagłówek definiuje również manipulatora pokrewne. Ten plik nagłówka jest zwykle dołączone dla Ciebie przez inny nagłówek iostream; rzadko musi zawierać go bezpośrednio.  
  
## <a name="syntax"></a>Składnia  
  
```  
#include <istream>  
  
```  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[iostream](../standard-library/istream-typedefs.md#iostream)|Typ `basic_iostream` specjalne na `char`.|  
|[IStream](../standard-library/istream-typedefs.md#istream)|Typ `basic_istream` specjalne na `char`.|  
|[wiostream](../standard-library/istream-typedefs.md#wiostream)|Typ `basic_iostream` specjalne na **wchar**.|  
|[wistream](../standard-library/istream-typedefs.md#wistream)|Typ `basic_istream` specjalne na **wchar**.|  
  
### <a name="manipulators"></a>Manipulatory  
  
|||  
|-|-|  
|[ws](../standard-library/istream-functions.md#ws)|Pomija biały znak w strumieniu.|  
|[swap](../standard-library/istream-functions.md#istream_swap)|Zamienia dwa obiekty stream.|  
  
### <a name="operators"></a>Operatory  
  
|||  
|-|-|  
|[operator >>](../standard-library/istream-operators.md#op_gt_gt)|Wyodrębnia znaki i ciągi ze strumienia.|  
  
### <a name="classes"></a>Klasy  
  
|||  
|-|-|  
|[basic_iostream —](../standard-library/basic-iostream-class.md)|Klasy strumienia, który można wykonać obie czynności danych wejściowych i wyjściowych.|  
|[basic_istream —](../standard-library/basic-istream-class.md)|Klasy szablonu opisuje obiekt, który kontroluje wyodrębniania elementów i zakodowanego obiektów z buforu strumienia elementami typu **elementu**, znanej także jako [char_type](../standard-library/basic-ios-class.md#char_type), są którego cech znaków Określona klasa **Tr**, znanej także jako [traits_type](../standard-library/basic-ios-class.md#traits_type).|  
  
## <a name="see-also"></a>Zobacz też  
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream — programowanie](../standard-library/iostream-programming.md)   
 [Konwencje iostream](../standard-library/iostreams-conventions.md)



