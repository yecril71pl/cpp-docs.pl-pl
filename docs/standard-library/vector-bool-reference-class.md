---
title: "Wektor&lt;bool&gt;:: klasę referencyjną | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vector/vector<bool>::reference
dev_langs: C++
helpviewer_keywords: vector<bool> reference class
ms.assetid: f27854f9-0ef0-4e7e-ad2e-cd53b6cb3334
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5ebca8cefef2aa53d2726d734932363d54426247
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="vectorltboolgtreference-class"></a>Wektor&lt;bool&gt;:: klasę referencyjną
`vector<bool>::reference` Klasa jest klasą proxy dostarczonych przez [wektor\<bool > klasy](../standard-library/vector-bool-class.md) do symulowania `bool&`.  
  
## <a name="remarks"></a>Uwagi  
 Symulowane odwołanie jest wymagane, ponieważ C++ nie zezwala natywnie na bezpośrednie odwołania do bitów. `vector<bool>`używa tylko jeden bit na element, który można odwoływać się za pomocą tej klasy serwera proxy. Jednakże symulacja odwołania nie jest kompletna, ponieważ niektóre przypisania nie są prawidłowe. Na przykład ponieważ adres `vector<bool>::reference` obiektu nie można wykonywać, następujący kod, który używa [wektor\<bool >:: — operator &#91; &#93;](http://msdn.microsoft.com/Library/97738633-690d-4069-b2d9-8c54104fbfdd) jest nieprawidłowy:  
  
```cpp  
vector<bool> vb;  
// ...  
bool* pb = &vb[1]; // conversion error - do not use  
bool& refb = vb[1];   // conversion error - do not use  
```  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|||  
|-|-|  
|[Przerzuć](../standard-library/vector-bool-reference-flip.md)|Odwraca wartość logiczną elementu wektora.|  
|[bool — operator](../standard-library/vector-bool-reference-operator-bool.md)|Udostępnia niejawna konwersja z `vector<bool>::reference` do `bool`.|  
|[operator =](../standard-library/vector-bool-reference-operator-assign.md)|Przypisuje do bitu wartość logiczną lub wartość przechowywaną przez odnośny element.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek**: \<wektor >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [\<Wektor >](../standard-library/vector.md)   
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)

