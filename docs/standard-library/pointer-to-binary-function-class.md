---
title: "pointer_to_binary_function — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: xfunctional/std::pointer_to_binary
dev_langs: C++
helpviewer_keywords:
- pointer_to_binary_function function
- pointer_to_binary_function class
ms.assetid: fb50599f-bcb3-4076-a669-6dcc3eb189a5
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 70c9d0a54976e8aa69175a730b1fcc747065d849
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="pointertobinaryfunction-class"></a>pointer_to_binary_function — Klasa
Konwertuje wskaźnika funkcji binarne dostosowywalne funkcja binarnej.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class Arg1, class Arg2, class Result>
class pointer_to_binary_function
    : public binary_function <Arg1, Arg2, Result>
{
public:
    explicit pointer_to_binary_function(
        Result(*pfunc)(Arg1, Arg2));
    Result operator()(Arg1 left, Arg2 right) const;
};
```  
  
#### <a name="parameters"></a>Parametry  
 `pfunc`  
 Funkcja binarnej ma zostać przekonwertowany.  
  
 `left`  
 Po lewej stronie obiekt, który  *\*pfunc* jest wywoływana na.  
  
 `right`  
 Prawo obiekt, który  *\*pfunc* jest wywoływana na.  
  
## <a name="return-value"></a>Wartość zwracana  
 Klasy szablonów przechowuje kopię **pfunc**. Definiuje jego funkcji członkowskiej `operator()` jako zwracanie (\* **pfunc**) (_ *lewej*, \_ *prawej*).  
  
## <a name="remarks"></a>Uwagi  
 Wskaźnik funkcji binarny jest obiektem funkcji i mogą być przekazywane do dowolnego algorytmu standardowa biblioteka C++, która oczekuje binarne funkcji jako parametr, ale nie jest to dostosowywalne. Aby używać go z karty, takie jak powiązania wartości do niego lub użyciu negator, musi być zasilane zagnieżdżone typy **first_argument_type**, **second_argument_type**, i **result_type**  który umożliwiają takie dostosowanie. Konwersja poprzez `pointer_to_binary_function` umożliwia adapterów funkcja do wykonania wskaźniki funkcji binarnego.  
  
## <a name="example"></a>Przykład  
 Konstruktor obiektu `pointer_to_binary_function` jest rzadko używana bezpośrednio. Zobacz opis funkcji pomocnika [ptr_fun —](../standard-library/functional-functions.md#ptr_fun) przykład sposobu deklarowanie i użycie `pointer_to_binary_function` predykatu karty.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<funkcjonalności >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do biblioteki C++ Standard](../standard-library/cpp-standard-library-reference.md)



