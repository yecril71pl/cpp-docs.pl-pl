---
title: "const_mem_fun_t — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: xfunctional/std::const_mem_fun_t
dev_langs: C++
helpviewer_keywords: const_mem_fun_t class
ms.assetid: f169d381-019b-4a0e-a9a3-54da6d948270
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9f6d3f685fc4e72b51344ae8c6c6dd383a142445
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="constmemfunt-class"></a>const_mem_fun_t — Klasa
Klasa karty, która umożliwia stałej funkcji członkowskiej, która nie przyjmuje żadnych argumentów do wywołania jako obiekt funkcja jednoargumentowy po zainicjowaniu z argumentem odwołania.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class Result, class Type>
class const_mem_fun_t : public unary_function <Type *, Result>  
{
    explicit const_mem_fun_t(Result (Type::* Pm)() const);
    Result operator()(const Type* Pleft) const;
 };
```  
  
#### <a name="parameters"></a>Parametry  
 `Pm`  
 Wskaźnik do funkcji członkowskiej klasy **typu** do przekonwertowania na obiekt funkcji.  
  
 `Pleft`  
 Obiekt który `Pm` funkcja członkowska jest wywoływana na.  
  
## <a name="return-value"></a>Wartość zwracana  
 Funkcja dostosowywalne jednoargumentowy.  
  
## <a name="remarks"></a>Uwagi  
 Klasy szablonów przechowuje kopię `Pm`, która musi być wskaźnikiem do funkcji członkowskiej klasy **typu**, w obiekcie prywatnego elementu członkowskiego. Definiuje jego funkcji członkowskiej `operator()` jako zwracanie ( `Pleft` -> \* `Pm`) () **const**.  
  
## <a name="example"></a>Przykład  
 Konstruktor obiektu `const_mem_fun_t` nie jest zwykle używana bezpośrednio; funkcja Pomocnika `mem_fun` umożliwia dostosowanie funkcji elementów członkowskich. Zobacz [mem_fun —](../standard-library/functional-functions.md#mem_fun) przykład sposobu użycia karty funkcja elementu członkowskiego.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<funkcjonalności >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)



