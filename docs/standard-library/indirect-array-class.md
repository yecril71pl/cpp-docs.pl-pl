---
title: "indirect_array — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: valarray/std::indirect_array
dev_langs: C++
helpviewer_keywords: indirect_array class
ms.assetid: 10e1eaea-ba5a-405c-a25e-7bdd3eee7fc7
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6479dbdf8e3da19581f3acbfcb9fa64f42b335cd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="indirectarray-class"></a>indirect_array — Klasa
Klasy wewnętrzne, pomocnicze szablonu, która obsługuje obiekty, które są podzbiorem valarrays zapewniając operacji między macierzami podzbioru zdefiniowanych przez określenie podzbiór indeksów valarray — nadrzędnego.  
  
## <a name="syntax"></a>Składnia  
  
  
  
## <a name="remarks"></a>Uwagi  
 Klasa opisuje obiekt, który zawiera odwołanie do obiektu **va** klasy [valarray —](../standard-library/valarray-class.md)**\<typu >**, wraz z obiektem **xa**  klasy **valarray — < size_t >**, która opisuje kolejność elementów, aby dokonać wyboru spośród **valarray —\<typu >** obiektu.  
  
 Możesz utworzyć **indirect_array —\<typu >** obiektu Pisząc wyrażenie w postaci **va [xa]**. Funkcje Członkowskie indirect_array — klasa następnie zachowania odpowiedniego sygnatury funkcji zdefiniowane dla **valarray —\<typu >**, ale dotyczy tylko sekwencji wybrane elementy.  
  
 Sekwencja składa się z **xa.** [rozmiar](../standard-library/valarray-class.md#size) elementów, gdy element `I` staje się indeks **xa**[ `I`] w **va**.  
  
## <a name="example"></a>Przykład:  
  
```  
// indirect_array.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> va ( 10 );  
   for ( i = 0 ; i < 10 ; i += 2 )  
      va [ i ] =  i;  
   for ( i = 1 ; i < 10 ; i += 2 )  
      va [ i ] =  -1;  
  
   cout << "The initial operand valarray is:  ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << va [ i ] << " ";  
   cout << ")." << endl;  
  
   // Select 2nd, 4th & 6th elements  
   // and assign a value of 10 to them  
   valarray<size_t> indx ( 3 );  
   indx [0] = 2;  
   indx [1] = 4;  
   indx [2] = 6;  
   va[indx] = 10;  
  
   cout << "The modified operand valarray is:  ( ";  
      for (i = 0 ; i < 10 ; i++ )  
         cout << va [ i ] << " ";  
   cout << ")." << endl;  
}  
```  
  
### <a name="output"></a>Dane wyjściowe  
  
```  
The initial operand valarray is:  (0 -1 2 -1 4 -1 6 -1 8 -1).  
The modified operand valarray is:  (0 -1 10 -1 10 -1 10 -1 8 -1).  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<valarray — >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

