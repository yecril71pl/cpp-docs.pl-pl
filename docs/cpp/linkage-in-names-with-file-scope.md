---
title: Połączenia nazw z zakresem pliku | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 770b30516d16cf9ffccaae4724b368ca8fa33be0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32419784"
---
# <a name="linkage-in-names-with-file-scope"></a>Połączenia nazw z zakresem pliku
Mają zastosowanie następujące reguły połączenie nazwy (inne niż `typedef` i nazwy modułu wyliczającego) z zakresem pliku:  
  
-   Nazwa jest jawnie zadeklarowana jako **statycznych**, ma połączenie zewnętrzne i identyfikuje element program wewnątrz własnej jednostce tłumaczenia.  
  
-   Moduł wyliczający nazwy i `typedef` nazwy mają bez połączenia.  
  
-   Innych nazw z zakresem pliku ma połączenie zewnętrzne.  
  
 **Microsoft Specific**  
  
-   Jeśli nazwy funkcji z zakresem pliku jest jawnie zadeklarowana jako **wbudowanego**, ma połączenie zewnętrzne, jeśli zostanie on uruchomiony lub odwołanie do jego adres. W związku z tym jest możliwe w dla funkcji z zakresem pliku mieć powiązanie wewnętrzne lub zewnętrzne.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
 Klasa ma zewnętrzne, jeśli go:  
  
-   Używa żadne funkcje języka C++ (na przykład kontroli dostępu do elementu członkowskiego, funkcje Członkowskie konstruktorów, destruktory i tak dalej).  
  
-   Nie jest używany w deklaracji inną nazwę, która ma połączenie zewnętrzne. To ograniczenie oznacza, że obiekty typu klasy, które są przekazywane do funkcji z zewnętrznym powiązaniem spowodować klasę, aby mieć zewnętrzne połączenie.  
  
## <a name="see-also"></a>Zobacz też  
 [Program i połączenie](../cpp/program-and-linkage-cpp.md)