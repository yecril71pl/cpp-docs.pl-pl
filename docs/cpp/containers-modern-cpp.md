---
title: Kontenery (Modern C++) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 6e10b758-e928-4827-9c3f-86cafe54bf5b
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8617bf35f3de0575c365f57ba78edbc8a79cc0e6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="containers-modern-c"></a>Kontenery (Modern C++)  
  
Domyślnie używają [wektor](../standard-library/vector-class.md) jako preferowany sekwencyjnych kontenera w języku C++. Jest to równoważne `List<T>` w językach .NET.  
  
```cpp  
vector<string> apples;  
apples.push_back("Granny Smith");  
```  
  
Użyj [mapy](../standard-library/map-class.md) (nie `unordered_map`) jako domyślny kontener asocjacyjnej. Użyj [ustawić](../standard-library/set-class.md), [multimap](../standard-library/multimap-class.md), i [multiset](../standard-library/multiset-class.md) wymiar degeneracji & w wielu przypadkach.  
  
```cpp  
map<string, string> apple_color;  
// ...  
apple_color["Granny Smith"] = "Green";  
```  
  
W razie potrzeby optymalizacji wydajności wziąć pod uwagę:  
  
1.  [Tablicy](../standard-library/array-class-stl.md) wpisz podczas osadzania jest ważne, na przykład jako element członkowski klasy.  
  
2.  Nieuporządkowane asocjacyjnej kontenerów, takich jak [unordered_map] ((.. /Standard-Library/unordered-map-Class.MD). Mają one element niższe obciążenie i stała czas wyszukiwania, ale może być trudniejsza umożliwia prawidłowe i efektywne.  
  
3.  Sortowane `vector`. Aby uzyskać więcej informacji, zobacz [algorytmy](../cpp/algorithms-modern-cpp.md).  
  
Nie używaj tablic w stylu języka C. Dla starszych interfejsów API, które wymagają bezpośredni dostęp do danych, użyj metody dostępu takiego jak `f(vec.data(), vec.size());` zamiast tego.  
  
Aby uzyskać więcej informacji na temat kontenerów, zobacz [standardowe kontenery biblioteki C++](../standard-library/stl-containers.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zapraszamy ponownie do języka C++](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [Dokumentacja języka C++](../cpp/cpp-language-reference.md)   
 [Standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md)
