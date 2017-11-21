---
title: "const_mem_fun_ref_t — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: xfunctional/std::const_mem_fun_ref_t
dev_langs: C++
helpviewer_keywords: const_mem_fun_ref_t class
ms.assetid: 316ddbaa-9f46-4931-8eba-ea4ca66360ef
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: dd90f1417f977680b99a1762834fd91dc7513152
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="constmemfunreft-class"></a>const_mem_fun_ref_t — Klasa
Klasa karty, który umożliwia **const** funkcji członkowskiej, która nie przyjmuje żadnych argumentów do wywołania jako obiekt funkcja jednoargumentowy po zainicjowaniu z argumentem odwołania.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class Result, class Type>
class const_mem_fun_ref_t
 : public unary_function<Type, Result>  
{
    explicit const_mem_fun_t(Result (Type::* Pm)() const);
    Result operator()(const Type& left) const;
 };
```  
  
#### <a name="parameters"></a>Parametry  
 `Pm`  
 Wskaźnik do funkcji członkowskiej klasy **typu** do przekonwertowania na obiekt funkcji.  
  
 `left`  
 Obiekt który `Pm` funkcja członkowska jest wywoływana na.  
  
## <a name="return-value"></a>Wartość zwracana  
 Funkcja dostosowywalne jednoargumentowy.  
  
## <a name="remarks"></a>Uwagi  
 Klasy szablonów przechowuje kopię `Pm`, która musi być wskaźnikiem do funkcji członkowskiej klasy **typu**, w obiekcie prywatnego elementu członkowskiego. Definiuje jego funkcji członkowskiej `operator()` jako zwracanie ( **po lewej stronie**.\* `Pm`) () **const**.  
  
## <a name="example"></a>Przykład  
 Konstruktor obiektu `const_mem_fun_ref_t` nie jest zwykle używana bezpośrednio; funkcja Pomocnika `mem_fun_ref` umożliwia dostosowanie funkcji elementów członkowskich. Zobacz [mem_fun_ref —](../standard-library/functional-functions.md#mem_fun_ref) przykład sposobu użycia karty funkcja elementu członkowskiego.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<funkcjonalności >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Odwołanie do biblioteki C++ Standard](../standard-library/cpp-standard-library-reference.md)



