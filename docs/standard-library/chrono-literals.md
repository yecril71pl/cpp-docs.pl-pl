---
title: "literały chrono | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 1a9e23b1-256f-4570-8226-5fa7364fb032
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7a470c96670753fd98b97f9b9d5daffbb8c3eba0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="chrono-literals"></a>literały chrono
(C ++ 14) \<Chrono > nagłówka definiuje 12 [literały definiowane przez użytkownika](../cpp/user-defined-literals-cpp.md) ułatwiające przy użyciu literałów, które reprezentują godzin, minut, sekund, w milisekundach, mikrosekundach i nanosekundach. Każdy literału zdefiniowanego przez użytkownika ma całkowitych i zmiennoprzecinkowych przeciążenia. Literały są zdefiniowane w przestrzeni nazw wbudowanego literals::chrono_literals, który wejścia zakresu automatycznie po std::chrono znajduje się w zakresie.  
  
## <a name="syntax"></a>Składnia  
  
```  
inline namespace literals {  
    inline namespace chrono_literals {  
 // return integral hours  
    constexpr chrono::hours operator"" h(unsigned long long Val);

 // return floating-point hours  
    constexpr chrono::duration<double, ratio<3600>> operator"" h(long double Val);

 // return integral minutes  
    constexpr chrono::minutes(operator"" min)(unsigned long long Val);

 // return floating-point minutes  
    constexpr chrono::duration<double, ratio<60>>(operator"" min)(long double Val);

 // return integral seconds  
    constexpr chrono::seconds operator"" s(unsigned long long Val);

 // return floating-point seconds  
    constexpr chrono::duration<double> operator"" s(long double Val);

 // return integral milliseconds  
    constexpr chrono::milliseconds operator"" ms(unsigned long long Val);

 // return floating-point milliseconds  
    constexpr chrono::duration<double, milli> operator"" ms(long double Val);

 // return integral microseconds      
    constexpr chrono::microseconds operator"" us(unsigned long long Val);

 // return floating-point microseconds  
    inline constexpr chrono::duration<double, micro> operator"" us(long double Val);

 // return integral nanoseconds  
    inline constexpr chrono::nanoseconds operator"" ns(unsigned long long Val);

 // return floating-point nanoseconds  
    constexpr chrono::duration<double, nano> operator"" ns(long double Val);

 }// inline namespace chrono_literals  
}// inline namespace literals  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Literały, które przyjmują `long long` argument zwracać wartość lub odpowiedniego typu. Literały, które przyjmują zmiennoprzecinkową punktu argument zwracany [czas trwania](../standard-library/duration-class.md).  
  
## <a name="example"></a>Przykład  
 Poniższe przykłady zasiewu sposób użycia literały chrono.  
  
```cpp  
constexpr auto day = 24h;  
constexpr auto week = 24h* 7;  
constexpr auto my_duration_unit = 108ms;  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek**: \<chrono >  
  
 **Namespace**: std::literals::chrono_literals  
  
## <a name="see-also"></a>Zobacz też  
 [\<chrono >](../standard-library/chrono.md)

