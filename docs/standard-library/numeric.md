---
title: '&lt;liczbowa&gt; | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: <numeric>
dev_langs: C++
helpviewer_keywords: <numeric> header
ms.assetid: 6d6ccb94-48cc-479b-b4a9-bd9c78d4896a
caps.latest.revision: "23"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1a4ffc7ad1e7fa512a51169e4155b54b7eca3194
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ltnumericgt"></a>&lt;numeryczne&gt;
Definiuje funkcje szablonu kontenera, które wykonują algorytmy dla przetwarzania numerycznego.  
  
## <a name="syntax"></a>Składnia  
  
```  
#include <numeric>  
```  
  
## <a name="remarks"></a>Uwagi  
Numeryczne algorytmów przypominać algorytmy standardowa biblioteka C++ [ \<algorytm >](algorithm.md)i może działać na różnych struktury danych. Należą do klasy kontenerów biblioteki standardowej — na przykład [wektor](../standard-library/vector-class.md) i [listy](../standard-library/list-class.md)i struktur danych programu i tablice elementów, które spełniają wymagania dotyczące konkretnego algorytmu. Te algorytmy osiągają ten poziom ogólności przez dostęp i przechodzenie przez elementy kontenera pośrednio poprzez iteratory. Te algorytmy przetwarzają zakresy iteratorów, które zazwyczaj są określane przez ich początkową lub końcową pozycję. Odnośne zakresy muszą być prawidłowe w tym sensie, że wszystkie wskaźniki w zakresach muszą być wyłuskiwalne i znajdować się w ramach sekwencji każdego zakresu, a ostatnia pozycja musi być osiągalna od pierwszej przez inkrementację.  
  
 Algorytmy rozszerzyć akcje, które są obsługiwane przez operacje i funkcje Członkowskie każdego kontenery standardowa biblioteka C++ i włączyć współdziałanie z różnymi typami obiektów kontenera w tym samym czasie.  
  
### <a name="functions"></a>Funkcje  
  
|||  
|-|-|  
|[accumulate](../standard-library/numeric-functions.md#accumulate)|Oblicza sumę wszystkich elementów w określonym zakresie — w tym niektóre wartości początkowe — przez obliczanie kolejnych sum częściowych, lub oblicza kolejne wyniki częściowe, które są uzyskiwane przy użyciu określonej operacji binarnej zamiast operacji sumowania.|  
|[adjacent_difference](../standard-library/numeric-functions.md#adjacent_difference)|Oblicza kolejne różnice między każdym elementem i jego poprzednikiem w zakresie wejściowym i generuje wyjściowe wyniki do zakresu docelowego, lub oblicza wynik ogólnej procedury, gdzie operacja różnicy zostaje zastąpiona przez inną określoną operację binarną.|  
|[inner_product](../standard-library/numeric-functions.md#inner_product)|Oblicza sumę wyników mnożenia elementów z dwóch zakresów i dodaje ją do określonej wartości początkowej lub oblicza wynik opis ogólnej procedury, gdzie operacje sumowania i mnożenia są zastępowane przez inne określone operacje binarne.|  
|[iota](../standard-library/numeric-functions.md#iota)|Przechowuje wartość początkową, zaczynając od pierwszego elementu i wypełnianie kolejne przyrosty wartości (`value++`) w każdym z elementów w interwale `[first, last)`.|  
|[partial_sum](../standard-library/numeric-functions.md#partial_sum)|Oblicza szereg sum zakresu wejściowego od pierwszego elementu za pomocą *i*th element i zapisuje wynik każdego Suma w *i*element th zakresu docelowego, lub oblicza wynik ogólnych gdzie operacji suma zostanie zastąpiony przez inną operację binarną określona.|  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)   
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Odwołanie do biblioteki C++ Standard](../standard-library/cpp-standard-library-reference.md)

