---
title: "Atomic — struktura | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: atomic/std::atomic
dev_langs: C++
ms.assetid: 261628ed-7049-41ac-99b9-cfe49f696b44
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3299f1bad01427723d3fcfabefd7924913d5690f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="atomic-structure"></a>atomic — Struktura
Zawiera opis obiektu, który wykonuje niepodzielne operacje na przechowywana wartość typu `Ty`.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class Ty>
struct atomic;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[niepodzielne](http://msdn.microsoft.com/Library/a538c43f-4d48-4308-ae1b-bab1839bccb8)|Tworzy obiekt atomic.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Atomic::operator Ty — Operator](http://msdn.microsoft.com/Library/a366c700-c7a0-4bcb-8eb4-4b57dfaea065)|Odczytuje i zwraca wartość przechowywana. ([atomic::load](http://msdn.microsoft.com/Library/05212726-cf8a-46fe-83d2-c16ac2abb7d1))|  
|[Atomic::operator = — Operator](http://msdn.microsoft.com/Library/fe161d57-47ae-4bad-92bf-ce32ac8d5953)|Używa określonej wartości w celu zastąpienia przechowywanej wartości. ([atomic::store](http://msdn.microsoft.com/Library/84759413-d664-47ef-a1f3-a73c5a62007b))|  
|[Atomic::operator ++ — Operator](http://msdn.microsoft.com/Library/492959e9-1ea8-4e02-a031-82b1b92e91a0)|Zwiększa wartość przechowywana. Używany tylko przez specjalizacje całkowite i wskaźnika.|  
|[Atomic::operator += — Operator](http://msdn.microsoft.com/Library/9ec97aa2-c9d7-436b-943d-2989eb2617dd)|Dodaje określoną wartość do przechowywanej wartości. Używany tylko przez specjalizacje całkowite i wskaźnika.|  
|[Atomic::operator — Operator](http://msdn.microsoft.com/Library/ad7c1ea7-1f6d-4a54-bf26-07630f749864)|Zmniejsza przechowywanej wartości. Używany tylko przez specjalizacje całkowite i wskaźnika.|  
|[Atomic::operator-= — Operator](http://msdn.microsoft.com/Library/902d0d9f-88fd-4500-aa2d-1e50f443e77c)|Odejmuje określoną wartość z wartością przechowywaną. Używany tylko przez specjalizacje całkowite i wskaźnika.|  
|[Atomic::operator & = — Operator](http://msdn.microsoft.com/Library/90e730ac-12e1-4abb-98f5-4eadd6861a89)|Wykonuje bitowej `and` na określoną wartość i przechowywana wartość. Używany tylko przez specjalizacje wartości całkowitych.|  
|[Atomic::operator &#124; = — Operator](http://msdn.microsoft.com/Library/f105eacc-31a6-4906-abba-f1cf013599b2)|Wykonuje bitowej `or` na określoną wartość i przechowywana wartość. Używany tylko przez specjalizacje wartości całkowitych.|  
|[Atomic::operator ^ = — Operator](http://msdn.microsoft.com/Library/f2a4da9d-67e8-4249-9161-9998e72a33c2)|Wykonuje bitowej `exclusive or` na określoną wartość i przechowywana wartość. Używany tylko przez specjalizacje wartości całkowitych.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[compare_exchange_strong](http://msdn.microsoft.com/Library/47bbf894-b28c-4ece-959e-67b3863cf4ed)|Wykonuje `atomic_compare_and_exchange` operacji na `this` i zwraca wynik.|  
|[compare_exchange_weak](http://msdn.microsoft.com/Library/e15e421a-f7a3-4272-993a-f487d2242e4f)|Wykonuje `weak_atomic_compare_and_exchange` operacji na `this` i zwraca wynik.|  
|[fetch_add](http://msdn.microsoft.com/Library/c68b91f2-6e8a-4ffa-8991-6bb6d466e1f3)|Dodaje określoną wartość do przechowywanej wartości.|  
|[fetch_and](http://msdn.microsoft.com/Library/a9c83001-b72c-4085-9640-f63f866714b9)|Wykonuje bitowej `and` na określoną wartość i przechowywana wartość.|  
|[fetch_or](http://msdn.microsoft.com/Library/4c532f7f-80c5-432a-b34b-48feacab8dca)|Wykonuje bitowej `or` na określoną wartość i przechowywana wartość.|  
|[fetch_sub](http://msdn.microsoft.com/Library/8cc80d4b-0942-45a3-9db8-bbf339a903e4)|Odejmuje określoną wartość z wartością przechowywaną.|  
|[fetch_xor](http://msdn.microsoft.com/Library/92bbaff8-ee29-4a1e-aee4-d9d405285bfe)|Wykonuje bitowej `exclusive or` na określoną wartość i przechowywana wartość.|  
|[is_lock_free](http://msdn.microsoft.com/Library/b99d5130-cdda-40a2-b14c-152b13a8ba45)|Określa, czy niepodzielne operacje na `this` są *nieblokującą*. Jest typem niepodzielnym *nieblokującą* blokad użycie żadne niepodzielne operacje tego typu.|  
|[obciążenia](http://msdn.microsoft.com/Library/05212726-cf8a-46fe-83d2-c16ac2abb7d1)|Odczytuje i zwraca wartość przechowywana.|  
|[Magazyn](http://msdn.microsoft.com/Library/84759413-d664-47ef-a1f3-a73c5a62007b)|Używa określonej wartości w celu zastąpienia przechowywanej wartości.|  
  
## <a name="remarks"></a>Uwagi  
 Typ `Ty` musi być *trivially copyable*. Oznacza to, za pomocą [memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md) Aby kopiować bajty jego musi mieć prawidłową `Ty` obiekt, który porównuje taki sam jak oryginalny obiekt. `compare_exchange_weak` i `compare_exchange_strong` Użyj funkcje Członkowskie [funkcji memcmp](../c-runtime-library/reference/memcmp-wmemcmp.md) do ustalenia, czy dwa `Ty` wartości są równe. Te funkcje nie będą używać `Ty`-zdefiniowany `operator==`. Funkcje Członkowskie `atomic` użyj `memcpy` można skopiować wartości typu `Ty`.  
  
 Częściowa specjalizacja, `atomic<Ty *>`, istnieje dla wszystkich typów wskaźnika. Specjalizacja umożliwia dodanie przesunięcia wartości wskaźnika zarządzanych lub odejmowania przesunięcie od niego. Operacje arytmetyczne przyjmuje argumentu typu `ptrdiff_t` i dostosować ten argument na podstawie rozmiaru `Ty` aby były spójne z adresem zwykłej arytmetyczne.  
  
 Dla każdego typu całkowitego, z wyjątkiem istnieje specjalizacji `bool`. Każdy specjalizacji zawiera bogaty zestaw metod niepodzielne operacje arytmetyczne i logicznych.  
  
||||  
|-|-|-|  
|`atomic<char>`|`atomic<signed char>`|`atomic<unsigned char>`|  
|`atomic<char16_t>`|`atomic<char32_t>`|`atomic<wchar_t>`|  
|`atomic<short>`|`atomic<unsigned short>`|`atomic<int>`|  
|`atomic<unsigned int>`|`atomic<long>`|`atomic<unsigned long>`|  
|`atomic<long long>`|`atomic<unsigned long long>`|  
  
 Całkowite specjalizacje pochodzą od odpowiadającego `atomic_integral` typów. Na przykład `atomic<unsigned int>` jest pochodną `atomic_uint`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<atomic >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [\<niepodzielne >](../standard-library/atomic.md)   
 [Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)



