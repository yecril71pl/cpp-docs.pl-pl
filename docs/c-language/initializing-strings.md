---
title: Inicjowanie ciągów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- character arrays, initializing
- strings [C++], initializing
- initializing arrays, strings
ms.assetid: 0ab8079d-d0d3-48f9-afd1-36a7bb439b29
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c01dbea3cbcfaf89280f5fd61a31646b88ac491a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32383982"
---
# <a name="initializing-strings"></a>inicjowanie ciągów
Można zainicjować tablicy znaków (lub znaki dwubajtowe) z ciągiem literału (lub całego literał ciągu). Na przykład:  
  
```  
char code[ ] = "abc";  
```  
  
 Inicjuje `code` jako tablica element czterech znaków. Czwartym elementem jest znakiem pustym, która kończy wszystkie literałów ciągów.  
  
 Lista identyfikatorów można tylko tak długo, jak liczba identyfikatorów do zainicjowania. Dodatkowe znaki są ignorowane, jeśli określono rozmiaru tablicy, która jest krótszy niż ciąg. Na przykład następujące oświadczenie inicjuje `code` jako tablica znaków trzech elementu:  
  
```  
char code[3] = "abcd";  
```  
  
 Pierwsze trzy znaki inicjatora są przypisane do `code`. Znak `d` i znak null przerywanie ciąg zostaną odrzucone. Należy pamiętać, że tworzy niezakończony ciąg (tzn bez wartość 0, aby oznaczyć końca) i generuje diagnostycznych komunikat informujący o tym warunku.  
  
 Deklaracja  
  
```  
char s[] = "abc", t[3] = "abc";  
```  
  
 jest taka sama jak  
  
```  
char s[]  = {'a', 'b', 'c', '\0'},   
     t[3] = {'a', 'b', 'c' };  
```  
  
 Jeśli ten ciąg jest mniejszy niż rozmiar określonej tablicy, pozostałe elementy tablicy są inicjowane na 0.  
  
 **Microsoft Specific**  
  
 W Microsoft C literałów ciągów mogą mieć maksymalnie 2048 bajtów długości.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Inicjowanie](../c-language/initialization.md)