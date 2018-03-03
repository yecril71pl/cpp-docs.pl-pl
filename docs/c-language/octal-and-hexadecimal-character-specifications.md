---
title: "Ósemkowe i szesnastkowe specyfikacje znaków | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- octal characters
- hexadecimal characters
ms.assetid: 9264f3ec-46b8-41a5-b21a-8f7ed0a11871
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cf3a27dc61543482d1d6484d0edd4b5e1bb04373
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="octal-and-hexadecimal-character-specifications"></a>Ósemkowe i szesnastkowe specyfikacje znaków
Sekwencja  **\\**  *ooo* zestaw jako kod znaku ósemkowe trzycyfrowa znaków oznacza, że możesz określić znaków ASCII. Liczbowa wartość ósemkowej liczby całkowitej określa wartość wymaganego znaku lub znak dwubajtowy.  
  
 Podobnie, sekwencja **\x***hhh* służy do określenia znaków ASCII jako kod znaków szesnastkowych. Na przykład można podać znaków ASCII backspace jako normalne sekwencji unikowej C (**\b**), lub kodu, jako **\010** (ósemkowe) lub **\x008** (szesnastkowo).  
  
 Można użyć tylko cyfr od 0 do 7 w ósemkowej sekwencji ucieczki. Ósemkowe sekwencje ucieczki nigdy nie mogą być dłuższe niż trzy cyfry i są zakończone pierwszym znakiem, który nie jest cyfrą ósemkową. Chociaż nie trzeba używać wszystkich trzech cyfr, należy użyć co najmniej jednej. Na przykład jest ósemkową reprezentację **\10** backspace znaku ASCII i **\101** litery A podane w formacie ASCII wykresu.  
  
 Podobnie, należy użyć co najmniej jednej cyfry do szesnastkowej sekwencji ucieczki, ale można pominąć drugą i trzecią cyfrę. W związku z tym można określić jako szesnastkowa sekwencja unikowa znaku backspace **\x8**, **\x08**, lub **\x008**.  
  
 Wartość sekwencji unikowej ósemkowe i szesnastkowe musi należeć do zakresu, można przedstawić wartości dla typu **unsigned char** dla stałej znakowej i typu `wchar_t` stałej znaków dwubajtowych. Zobacz [wielobajtowe i dwubajtowe znaki](../c-language/multibyte-and-wide-characters.md) informacji na stałe znaków dwubajtowych.  
  
 W odróżnieniu od ósemkowych stałych wyjścia, nie ma limitu dotyczącego liczby cyfr szesnastkowych w sekwencji wyjścia. Szesnastkowa sekwencja ucieczki kończy się przy pierwszym znaku, który nie jest cyfrą szesnastkową. Ponieważ cyfry szesnastkowe zawierają litery **a** za pośrednictwem **f**, należy zachować ostrożność się upewnić, że sekwencja specjalna kończy się na zamierzone cyfr. Aby uniknąć nieporozumień, można umieścić definicje znaku ósemkowego lub szesnastkowego w definicji makra:  
  
```  
#define Bell '\x07'  
```  
  
 W przypadku wartości szesnastkowych, można podzielić ciąg znaków w celu wyraźnego pokazania poprawnej wartości:  
  
```  
"\xabc"    /* one character  */  
"\xab" "c" /* two characters */  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Stałe znakowe języka C](../c-language/c-character-constants.md)