---
title: '#undef — dyrektywa (C/C++) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- '#undef'
dev_langs:
- C++
helpviewer_keywords:
- '#undef directive'
- undef directive (#undef)
- preprocessor, directives
ms.assetid: 88900e0e-2c19-4a63-b681-f3d3133c24ca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c98c6559e04f0e89fa4c3501f30cd88d449de306
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/10/2018
ms.locfileid: "42465666"
---
# <a name="undef-directive-cc"></a>#undef — dyrektywa (C/C++)
Usuwa (jedno anulowanie definicji) nazwę wcześniej utworzone za pomocą `#define`.  
  
## <a name="syntax"></a>Składnia  
  
```  
#undef   
identifier  
```  
  
## <a name="remarks"></a>Uwagi 

**#Undef** dyrektywa spowoduje usunięcie bieżącej definicji *identyfikator*. W związku z tym kolejne wystąpienia *identyfikator* są ignorowane przez preprocesor. Można usunąć definicji makra przy użyciu **#undef**, określ tylko makra *identyfikator* ; nie ma listy parametrów.  
  
Można również zastosować **#undef** dyrektywę identyfikator, który nie ma poprzedniego definicji. Zapewnia to, że identyfikator jest niezdefiniowany. Wymiana makra nie jest wykonywana w ramach **#undef** instrukcji.  
  
**#Undef** dyrektywy zwykle jest powiązany z `#define` dyrektywy do tworzenia regionu w programie źródłowym, w którym identyfikator ma specjalne znaczenie. Na przykład określoną funkcję program źródłowy można użyć stałych manifestu do definiowania wartości specyficzne dla środowiska, które nie dotyczą całego programu. **#Undef** dyrektywa działa także w przypadku `#if` dyrektywy do kontrolowania kompilacji warunkowej programu źródłowego. Zobacz [#if, #elif #else i #endif, dyrektywy](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md) Aby uzyskać więcej informacji.  
  
W poniższym przykładzie **#undef** dyrektywy Usuwa definicje symboliczna stała i makra. Pamiętaj, że biorąc pod uwagę tylko identyfikator makra.  
  
```  
#define WIDTH 80  
#define ADD( X, Y ) ((X) + (Y))  
.  
.  
.  
#undef WIDTH  
#undef ADD  
```  
  
**Microsoft Specific**  
  
Makra mogą być niezdefiniowana z wiersza polecenia przy użyciu `/U` opcji, a po niej niezdefiniowanej nazwy makra. Efekt wydaniu tego polecenia jest równoważna z sekwencji `#undef` *Nazwa makra* instrukcji na początku pliku.  
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 
[Dyrektywy preprocesora](../preprocessor/preprocessor-directives.md)