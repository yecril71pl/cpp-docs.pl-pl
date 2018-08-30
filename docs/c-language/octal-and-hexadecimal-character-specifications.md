---
title: Ósemkowe i szesnastkowe specyfikacje znaków | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- octal characters
- hexadecimal characters
ms.assetid: 9264f3ec-46b8-41a5-b21a-8f7ed0a11871
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eeb1f8e08fbb1d4f30517485c9296febab5a0de0
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43198759"
---
# <a name="octal-and-hexadecimal-character-specifications"></a>Ósemkowe i szesnastkowe specyfikacje znaków
Sekwencja **\\** <em>ooo</em> oznacza, że można określić dowolny znak ASCII znak zestawu jako trzycyfrowy ósemkowy kod znaku. Liczbowa wartość ósemkowej liczby całkowitej określa wartość wymaganego znaku lub znak dwubajtowy.  
  
 Podobnie, sekwencja **\x**<em>hhh</em> umożliwia określenie dowolnego znaku ASCII jako szesnastkowego kodu znaku. Na przykład można podać znaku backspace ASCII jako normalnego sekwencja ucieczki C (**\b**), lub zakodować go jako **\010** (ósemkowo) lub **\x008** (szesnastkowo).  
  
 Można użyć tylko cyfr od 0 do 7 w ósemkowej sekwencji ucieczki. Ósemkowe sekwencje ucieczki nigdy nie mogą być dłuższe niż trzy cyfry i są zakończone pierwszym znakiem, który nie jest cyfrą ósemkową. Chociaż nie trzeba używać wszystkich trzech cyfr, należy użyć co najmniej jednej. Na przykład, ósemkowe reprezentacje to **\10** dla znaku backspace ASCII i **\101** dla litery A, jak podano ASCII wykresu.  
  
 Podobnie, należy użyć co najmniej jednej cyfry do szesnastkowej sekwencji ucieczki, ale można pominąć drugą i trzecią cyfrę. W związku z tym można określić szesnastkową sekwencję ucieczki dla znaku backspace jako **\x8**, **\x08**, lub **\x008**.  
  
 Wartość ósemkowej lub szesnastkowej sekwencji ucieczki musi być w zakresie reprezentowanych wartości dla typu **unsigned char** dla stałej znakowej i typu `wchar_t` dla dwubajtowej stałej znakowej. Zobacz [wielobajtowe i dwubajtowe znaki](../c-language/multibyte-and-wide-characters.md) uzyskać informacji na temat dwubajtowych stałych znakowych.  
  
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