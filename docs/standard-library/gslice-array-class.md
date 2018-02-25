---
title: "gslice_array — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- valarray/std::gslice_array
dev_langs:
- C++
helpviewer_keywords:
- gslice_array class
ms.assetid: ad1b4514-b14a-4baf-a293-d5a8e8674c75
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f47b1ce767a2090e718406585d2c40db2c4c8bcb
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="gslicearray-class"></a>gslice_array — Klasa
Klasy wewnętrzne, pomocnicze szablonu, która obsługuje obiekty ogólne wycinek zapewniając operacji między macierzami z podzbioru zdefiniowanych przez ogólne wycinek valarray —.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <class Type>  
class gslice_array : public gsplice {  
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
 Klasa opisuje obiekt, który zawiera odwołanie do obiektu **va** klasy [valarray —](../standard-library/valarray-class.md)**\<typu >**, wraz z obiektem **gs**  klasy [gslice —](../standard-library/gslice-class.md) której przedstawiono sekwencję elementów można wybierać **valarray —\<typu >** obiektu.  
  
 Możesz utworzyć **gslice_array —\<typu >** obiektu Pisząc wyrażenie w postaci [ł &#91; gs &#93;](../standard-library/valarray-class.md#op_at). Funkcje Członkowskie gslice_array — klasa następnie zachowania odpowiedniego sygnatury funkcji zdefiniowane dla **valarray —\<typu >**, ale dotyczy tylko sekwencji wybrane elementy.  
  
 Klasy szablonów jest tworzony pośrednio przez niektóre operacje valarray — i nie można użyć bezpośrednio w programie. Klasa szablonu pomocniczego wewnętrznego zamiast tego jest używana przez operator indeksu dolnego wycinka:  
  
 `gslice_array`\< **Typ** >  `valarray` \< **typu**>:: `operator[]` ( **constgslice &**).  
  
 Możesz utworzyć **gslice_array —\<typu >** obiektu Pisząc wyrażenie w postaci **va [gsl]**, dla wycinek **gsl** z valarray —  **Va**. Funkcje Członkowskie gslice_array — klasa następnie zachowania odpowiedniego sygnatury funkcji zdefiniowane dla **valarray —\<typu >**, ale dotyczy tylko sekwencji wybrane elementy. Sekwencja kontrolowane przez gslice_array — jest definiowana za trzy parametry konstruktora wycinka, indeks pierwszego elementu w pierwszego wycinka liczba elementów w każdej wycinka i odległość między elementami w każdy wycinek.  
  
 W poniższym przykładzie:  
  
```  
const size_t lv[] = {2, 3};  
const size_t dv[] = {7, 2};  
const valarray<size_t> len(lv, 2), str(dv, 2);

// va[gslice(3, len, str)] selects elements with  
//   indices 3, 5, 7, 10, 12, 14  
```  
  
 Indeksy muszą być prawidłowe dla procedury identyfikator był prawidłowy.  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [gslice::gslice](../standard-library/gslice-class.md#gslice) przykład sposobu deklarowanie i użycie slice_array —.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<valarray — >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

