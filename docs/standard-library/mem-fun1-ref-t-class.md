---
title: "mem_fun1_ref_t — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- xfunctional/std::mem_fun1_ref_t
dev_langs:
- C++
helpviewer_keywords:
- mem_fun1_ref_t class
ms.assetid: 7d6742f6-19ba-4523-b3c8-0e5b8f11464f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 35dd25e56ba838864eeeb64d43fc8c2d25cff803
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="memfun1reft-class"></a>mem_fun1_ref_t — Klasa
Klasa karty, który umożliwia **non_const** funkcji członkowskiej, która pobiera jeden argument ma być wywoływana jako obiektu binarnego funkcja po zainicjowaniu z argumentem odwołania.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class Result, class Type, class Arg>
class mem_fun1_ref_t : public binary_function<Type, Arg, Result> {
    explicit mem_fun1_ref_t(
    Result (Type::* _Pm)(Arg));

    Result operator()(
    Type& left,
    Arg right) const;

 };
```  
  
#### <a name="parameters"></a>Parametry  
 `_Pm`  
 Wskaźnik do funkcji członkowskiej klasy **typu** do przekonwertowania na obiekt funkcji.  
  
 `left`  
 Obiekt który `_Pm` funkcja członkowska jest wywoływana na.  
  
 `right`  
 Argument, który są przyznawane `_Pm`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Dostosowywalne funkcja binarnej.  
  
## <a name="remarks"></a>Uwagi  
 Klasy szablonów przechowuje kopię `_Pm`, która musi być wskaźnikiem do funkcji członkowskiej klasy **typu**, w obiekcie prywatnego elementu członkowskiego. Definiuje jego funkcji członkowskiej `operator()` jako zwracanie ( **po lewej stronie**.\* `_Pm`) ( **prawo**).  
  
## <a name="example"></a>Przykład  
 Konstruktor obiektu `mem_fun1_ref_t` nie jest zwykle używana bezpośrednio; funkcja Pomocnika `mem_fun_ref` umożliwia dostosowanie funkcji elementów członkowskich. Zobacz [mem_fun_ref —](../standard-library/functional-functions.md#mem_fun_ref) przykład sposobu użycia karty funkcja elementu członkowskiego.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<funkcjonalności >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)



