---
title: Typ float | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- type float
- exponent length
- float keyword [C]
- mantissas, length
- floating-point numbers, float type
- ranges, floating-point types
- floating-point numbers, variables
- lengths, mantissa
- double data type, type float
- IEEE floating-point representation
- lengths, exponent
ms.assetid: 706e332b-17a0-4a30-b7d8-5d6cd372524b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e218f7b5025de10dc06bf20fc759aed93189ec53
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32390938"
---
# <a name="type-float"></a>Typ float
Liczby zmiennoprzecinkowe formatu IEEE (Institute of Electrical and Electronics Engineers). Wartości o pojedynczej precyzji z typem float mieć 4 bajty, składające się z bitu znaku, 8-bitową 127 nadmiarowe binarne wykładnik i mantysy 23-bitowych. Mantysa reprezentuje liczbą z zakresu od 1.0 i 2.0. Ponieważ bit znaczącymi bitami mantysa ma zawsze numer 1, nie są przechowywane w kodzie. Taka reprezentacja zapewnia szereg około 3.4E-38 do 3.4E + 38 na typ float.  
  
 Zmienne można zadeklarować jako float lub double, w zależności od potrzeb aplikacji. Główne różnice między tymi dwoma typami są znaczenie, które reprezentują, magazynu, które wymagają one i ich zakresu. W poniższej tabeli przedstawiono relację między znaczenie i wymagania dotyczące magazynu.  
  
### <a name="floating-point-types"></a>Typy zmiennoprzecinkowe  
  
|Typ|Cyfr znaczących|Liczba bajtów|  
|----------|------------------------|---------------------|  
|float|6 - 7|4|  
|double|15 - 16|8|  
  
 Zmienne zmiennoprzecinkowe są reprezentowane przez mantysy, zawiera wartość numeru i wykładnik, zawierającej wielkość liczby.  
  
 W poniższej tabeli przedstawiono liczbę bitów przydzielone do mantysa i wykładnik dla poszczególnych typów zmiennoprzecinkowych. Najbardziej znaczącego bitu dowolnego typu float lub double jest zawsze znaku. Jeśli ma wartość 1, kod jest traktowany jako negatywne; w przeciwnym razie uważa się liczbą dodatnią.  
  
### <a name="lengths-of-exponents-and-mantissas"></a>Długość Wykładniki i mantysy  
  
|Typ|Długość wykładnika|Długość mantysy|  
|----------|---------------------|---------------------|  
|float|8 bitów|bity 23|  
|double|bity 11|52 bitów|  
  
 Ponieważ wykładniki są przechowywane w postaci bez znaku, wykładnik jest ukierunkowane połowa możliwych wartości. Dla typu zmiennoprzecinkowego odchylenia to 127; dla typu double jest 1023. Bieżąca wartość wykładnika można obliczyć przez odjęcie wartość odchylenia od wartości wykładnika.  
  
 Mantysa jest przechowywany jako ułamek binarne większa lub równa 1 i mniejsza niż wartość 2. Dla typów zmiennoprzecinkowych i typu double dorozumianych 1 wiodące mantysa w jest pozycji najbardziej znaczącego bitu tak mantysy są faktycznie 24 i 53 bitów długości, odpowiednio, nawet najbardziej znaczącego bitu nigdy nie są przechowywane w pamięci.  
  
 Zamiast metody magazynu tylko opisanej zmiennoprzecinkowych pakietu można przechowywać binarne liczb zmiennoprzecinkowych jako liczby nieznormalizowany. "Nieznormalizowany liczby" są niezerowe liczb zmiennoprzecinkowych z zastrzeżone wartości wykładnika, w których najbardziej znaczącego bitu mantysa jest 0. Przy użyciu formatu nieznormalizowany, można rozszerzyć zakres liczba zmiennoprzecinkowa kosztem dokładności. Nie można kontrolować, czy liczba zmiennoprzecinkowa jest wyświetlana w postaci znormalizowane lub nieznormalizowany; zmiennoprzecinkowe pakiet określa reprezentacji. Zmiennoprzecinkowe pakiet nigdy nie używa nieznormalizowany formularza, chyba że wykładnik staje się mniej niż wartość minimalna, który może być reprezentowany w znormalizowana postać.  
  
 W poniższej tabeli przedstawiono minimalne i maksymalne wartości, można przechowywać w zmiennych poszczególnych typów zmiennoprzecinkowych. Wartości wymienionych w poniższej tabeli dotyczą wyłącznie znormalizowane liczb zmiennoprzecinkowych; liczby zmiennoprzecinkowe nieznormalizowany miał mniejszą wartość minimalna. Należy pamiętać, że numery przechowywane w 80*x*87 rejestrów zawsze są wyświetlane w programie 80-bitowa znormalizowana postać; numery tylko może być reprezentowany w postaci nieznormalizowany, gdy przechowywana w 32-bitowy lub 64-bitowych zmienne zmiennoprzecinkowe (zmienne typu zmiennoprzecinkowego i typu long).  
  
### <a name="range-of-floating-point-types"></a>Zakres wartości zmiennoprzecinkowych  
  
|Typ|Wartość minimalna|Wartość maksymalna|  
|----------|-------------------|-------------------|  
|float|1.175494351 E - 38|3.402823466 E + 38|  
|double|2.2250738585072014 E - 308|1.7976931348623158 E + 308|  
  
 Jeśli dokładności mniejsze znaczenie niż w przypadku magazynu, należy rozważyć użycie typu zmiennoprzecinkowego zmiennoprzecinkowe zmiennych. Z drugiej strony Jeśli dokładności najważniejszych kryterium, użyj typu double.  
  
 Zmienne zmiennoprzecinkowe może być podwyższony do typu większe znaczenie (z typu zmiennoprzecinkowego do typu double). Podwyższanie poziomu często występuje, gdy wykonać arytmetyki na zmienne zmiennoprzecinkowe. Ta operacja arytmetyczna wykonywana w jako wysoki stopień dokładności jako zmienną o najwyższym stopniu dokładności. Na przykład wziąć pod uwagę następujące deklaracje typu:  
  
```  
float f_short;  
double f_long;  
long double f_longer;  
  
f_short = f_short * f_long;  
```  
  
 W powyższym przykładzie zmienna `f_short` jest podwyższany do typu double i pomnożona przez `f_long`; a następnie wynik jest zaokrąglana do typu float przed przypisaniem do `f_short`.  
  
 W poniższym przykładzie (który używa deklaracji z poprzedniego przykładu), czy arytmetyczną została wykonana w dokładności float (32-bitowy) na zmiennych; wynik jest następnie podwyższony do typu double:  
  
```  
f_longer = f_short * f_short;  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Magazyn typów podstawowych](../c-language/storage-of-basic-types.md)