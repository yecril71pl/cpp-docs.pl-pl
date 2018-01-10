---
title: "Połączenia nazw z zakresem pliku | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- scope [C++], linkage rules
- linkage [C++], scope linkage rules
- names [C++], scope linkage rules
- static modifier, file scope
- static names and file scope
- file scope [C++]
- declarations [C++], external
- external linkage, scope linkage rules
- static variables, external declarations
ms.assetid: 38d3fa5e-1861-466e-a590-84b86f7b184e
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 581d7798f4f3aaa409d843f8b7f3b5869b47407e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="linkage-in-names-with-file-scope"></a>Połączenia nazw z zakresem pliku
Mają zastosowanie następujące reguły połączenie nazwy (inne niż `typedef` i nazwy modułu wyliczającego) z zakresem pliku:  
  
-   Nazwa jest jawnie zadeklarowana jako **statycznych**, ma połączenie zewnętrzne i identyfikuje element program wewnątrz własnej jednostce tłumaczenia.  
  
-   Moduł wyliczający nazwy i `typedef` nazwy mają bez połączenia.  
  
-   Innych nazw z zakresem pliku ma połączenie zewnętrzne.  
  
 **Dotyczące firmy Microsoft**  
  
-   Jeśli nazwy funkcji z zakresem pliku jest jawnie zadeklarowana jako **wbudowanego**, ma połączenie zewnętrzne, jeśli zostanie on uruchomiony lub odwołanie do jego adres. W związku z tym jest możliwe w dla funkcji z zakresem pliku mieć powiązanie wewnętrzne lub zewnętrzne.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
 Klasa ma zewnętrzne, jeśli go:  
  
-   Używa żadne funkcje języka C++ (na przykład kontroli dostępu do elementu członkowskiego, funkcje Członkowskie konstruktorów, destruktory i tak dalej).  
  
-   Nie jest używany w deklaracji inną nazwę, która ma połączenie zewnętrzne. To ograniczenie oznacza, że obiekty typu klasy, które są przekazywane do funkcji z zewnętrznym powiązaniem spowodować klasę, aby mieć zewnętrzne połączenie.  
  
## <a name="see-also"></a>Zobacz też  
 [Program i połączenie](../cpp/program-and-linkage-cpp.md)