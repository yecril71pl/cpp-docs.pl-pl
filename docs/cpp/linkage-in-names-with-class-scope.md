---
title: Połączenia nazw z zakresem klasy | Dokumentacja firmy Microsoft
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
- classes [C++], scope
- external linkage, scope linkage rules
- class names [C++], linkage
- classes [C++], names
- scope [C++], class names
- class scope [C++], linkage in names with
ms.assetid: 45275ff3-6e94-4967-82c8-ba540ef4da28
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9eb58f87e998fbe1eeeb9b26eb0da75046a9079d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="linkage-in-names-with-class-scope"></a>Połączenia nazw z zakresem klasy
Mają zastosowanie następujące reguły połączenia nazw z zakresem klasy:  
  
-   Członkowie klasy statycznej mają połączenie zewnętrzne.  
  
-   Funkcje elementów członkowskich klasy ma połączenie zewnętrzne.  
  
-   Moduły wyliczające i `typedef` nazwy mają bez połączenia.  
  
 **Microsoft Specific**  
  
-   Funkcje deklarowane jako `friend` funkcji musi mieć zewnętrzne połączenie. Deklarowanie funkcji statycznej jako `friend` generuje błąd.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Program i połączenie](../cpp/program-and-linkage-cpp.md)