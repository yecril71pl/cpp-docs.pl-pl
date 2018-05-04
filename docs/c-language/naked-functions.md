---
title: Funkcje naked | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- naked functions
- functions [C++], naked
- prolog code
- epilog code
ms.assetid: 2543c8af-00d4-4a2a-8a87-e746da1f9929
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5ce7eeaf94bf23bcee67650b3074f2f9b622c0fe
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="naked-functions"></a>Funkcje Naked
**Microsoft Specific**  
  
 `naked` Atrybuty klasy magazynu to rozszerzenie specyficzne dla firmy Microsoft dla języka C. Dla funkcji zadeklarowana z `naked` atrybuty klasy magazynu, kompilator generuje kod bez prolog i epilog kodu. Ta funkcja umożliwia pisanie własnych sekwencji kodu prologu/epilogu przy użyciu kodu wbudowanego asemblera. Gołe funkcje są szczególnie przydatne w pisaniu sterowniki urządzeń wirtualnych.  
  
 Ponieważ `naked` atrybut dotyczy tylko do definicji funkcji i nie jest modyfikator typu, używania funkcji naked użyj składni rozszerzonych atrybutów, opisanego w [rozszerzone atrybuty klasy magazynu](../c-language/c-extended-storage-class-attributes.md).  
  
 W poniższym przykładzie zdefiniowano funkcję z `naked` atrybutu:  
  
```  
__declspec( naked ) int func( formal_parameters )  
{  
   /* Function body */  
}  
```  
  
 Lub też:  
  
```  
#define Naked   __declspec( naked )  
  
Naked int func( formal_parameters )  
{  
   /* Function body */  
}  
```  
  
 `naked` Atrybut ma wpływ tylko rodzaj generowania kodu kompilator funkcji prolog i epilog sekwencji. Nie ma ona wpływu na kod, który zostanie wygenerowany dla wywołania funkcji. W związku z tym `naked` atrybut nie jest uznawany za część typu funkcji i nie może mieć wskaźników funkcji `naked` atrybutu. Ponadto `naked` atrybutu nie można zastosować do definicji danych. Na przykład następujący kod generuje błędy:  
  
```  
__declspec( naked ) int i;  /* Error--naked attribute not */  
                            /* permitted on data declarations. */  
```  
  
 `naked` Atrybut ma zastosowanie tylko w definicji funkcji i nie można określić w prototypu funkcji. Następujące oświadczenie generuje błąd kompilatora:  
  
```  
__declspec( naked ) int func();   /* Error--naked attribute not */  
                     /* permitted on function declarations.    */   \  
```  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Definicje funkcji języka C](../c-language/c-function-definitions.md)