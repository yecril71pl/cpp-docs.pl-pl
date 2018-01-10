---
title: "slice_array — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: valarray/std::slice_array
dev_langs: C++
helpviewer_keywords: slice_array class
ms.assetid: a182d5f7-f35c-4e76-86f2-b5ac64ddc846
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2935ec42892c2d28d7e0ccab1a8222bdb771e944
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="slicearray-class"></a>slice_array — Klasa
Klasy wewnętrzne, pomocnicze szablonu, która obsługuje obiekty wycinek zapewniając operacji między macierzami z podzbioru zdefiniowanych przez wycinka valarray —.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <class Type>  
class slice_array : public slice {  
public:  
    typedef Type value_type;  
    void operator=(const valarray<Type>& x) const;

 
    void operator=(const Type& x) const;

 
    void operator*=(const valarray<Type>& x) const;

 
    void operator/=(const valarray<Type>& x) const;

 
    void operator%=(const valarray<Type>& x) const;

 
    void operator+=(const valarray<Type>& x) const;

 
    void operator-=(const valarray<Type>& x) const;

 
    void operator^=(const valarray<Type>& x) const;

 
    void operator&=(const valarray<Type>& x) const;

 
    void operator|=(const valarray<Type>& x) const;

 
    void operator<<=(const valarray<Type>& x) const;

 
    void operator>>=(const valarray<Type>& x) const;

 
// The rest is private or implementation defined  
}  
```  
  
## <a name="remarks"></a>Uwagi  
 Klasa opisuje obiekt, który zawiera odwołanie do obiektu klasy [valarray —](../standard-library/valarray-class.md)**\<typu >**, wraz z obiektu klasy [wycinka](../standard-library/slice-class.md), która Zawiera opis sekwencji elementów można wybierać **valarray —\<typu >** obiektu.  
  
 Klasy szablonów jest tworzony pośrednio przez niektóre operacje valarray — i nie można użyć bezpośrednio w programie. Klasy wewnętrzne, pomocnicze szablonu używanego przez operator indeksu dolnego wycinka:  
  
 `slice_array`\<**Typu**> `valarray`< **typu**:: `operator[]` ( `slice`).  
  
 Możesz utworzyć **slice_array —\<typu >** obiektu Pisząc wyrażenie w postaci [ł &#91; sl &#93;](../standard-library/valarray-class.md#op_at), dla wycinek **sl** z valarray — **va**. Funkcje Członkowskie slice_array — klasa następnie zachowania odpowiedniego sygnatury funkcji zdefiniowane dla **valarray —\<typu >**, ale dotyczy tylko sekwencji wybrane elementy. Sekwencja kontrolowane przez slice_array — jest definiowana za trzy parametry konstruktora wycinka, indeks pierwszego elementu w wycinka, liczba elementów i odległość między elementami. Slice_array — obcięty z valarray — **va** deklarowana przez **va**[ `slice`(2, 5, 3)] wybiera elementy indeksami 2, 5, 8, 11 i 14 z **va**. Indeksy muszą być prawidłowe dla procedury identyfikator był prawidłowy.  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [slice::slice](../standard-library/slice-class.md#slice) przykład sposobu deklarowanie i użycie slice_array —.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<valarray — >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

