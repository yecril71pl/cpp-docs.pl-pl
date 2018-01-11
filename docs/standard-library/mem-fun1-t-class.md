---
title: "mem_fun1_t — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: xfunctional/std::mem_fun1_t
dev_langs: C++
helpviewer_keywords: mem_fun1_t class
ms.assetid: 01a8c2c2-b2f7-4e3f-869c-5b5b9f06ea54
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: db6449ad7cb350eddaa0abeecd9463fc53407d4a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="memfun1t-class"></a>mem_fun1_t — Klasa
Klasa karty, który umożliwia **non_const** funkcji członkowskiej, która pobiera jeden argument ma być wywoływana jako obiektu binarnego funkcja po zainicjowaniu z argumentem wskaźnika.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class Result, class Type, class Arg>
class mem_fun1_t : public binary_function<Type *, Arg, Result> {
    explicit mem_fun1_t(
    Result (Type::* _Pm)(Arg));

    Result operator()(
    Type* _Pleft,
    Arg right) const;

 };
```  
  
#### <a name="parameters"></a>Parametry  
 `_Pm`  
 Wskaźnik do funkcji członkowskiej klasy **typu** do przekonwertowania na obiekt funkcji.  
  
 `_Pleft`  
 Obiekt który `_Pm` funkcja członkowska jest wywoływana na.  
  
 `right`  
 Argument, który są przyznawane `_Pm`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Dostosowywalne funkcja binarnej.  
  
## <a name="remarks"></a>Uwagi  
 Klasy szablonów przechowuje kopię `_Pm`, która musi być wskaźnikiem do funkcji członkowskiej klasy **typu**, w obiekcie prywatnego elementu członkowskiego. Definiuje jego funkcji członkowskiej `operator()` jako zwracanie ( **_Pleft** -> \* `_Pm`) ( **prawo**).  
  
## <a name="example"></a>Przykład  
  Konstruktor obiektu `mem_fun1_t` nie jest zwykle używana bezpośrednio; funkcja Pomocnika `mem_fun` umożliwia dostosowanie funkcji elementów członkowskich. Zobacz [mem_fun —](../standard-library/functional-functions.md#mem_fun) przykład sposobu użycia karty funkcja elementu członkowskiego.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<funkcjonalności >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)



