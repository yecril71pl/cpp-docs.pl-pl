---
title: "#<a name=\"undef-directive-cc--microsoft-docs\"></a>undef — dyrektywa (C/C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: '#undef'
dev_langs: C++
helpviewer_keywords:
- '#undef directive'
- undef directive (#undef)
- preprocessor, directives
ms.assetid: 88900e0e-2c19-4a63-b681-f3d3133c24ca
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: aee7babf895b72a5ff4f5fb1485e4bb118e95889
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="undef-directive-cc"></a>#undef — dyrektywa (C/C++)
Usuwa (anulowanie definicji) nazwa wcześniej utworzona z `#define`.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
#undef   
identifier  
  
```  
  
## <a name="remarks"></a>Uwagi  
 `#undef` Dyrektywy spowoduje usunięcie bieżącej definicji *identyfikator*. W rezultacie kolejne wystąpienia *identyfikator* są ignorowane przez preprocesora. Aby usunąć definicji makra za pomocą `#undef`, określ tylko makra *identyfikator* ; nie ma listy parametrów.  
  
 Można także zastosować `#undef` dyrektywy do identyfikatora, który nie ma poprzedniej definicji. Dzięki temu, że identyfikator jest niezdefiniowany. Makro zamiany nie jest wykonywane w ramach `#undef` instrukcje.  
  
 `#undef` Dyrektywy zwykle łączyć się z `#define` dyrektywy, aby utworzyć region w programie źródła, w którym identyfikator ma specjalnego znaczenia. Na przykład określoną funkcję programu źródłowego umożliwia stałe manifestu: definiowanie wartości określonego środowiska, które nie mają wpływu na pozostałe program. `#undef` Dyrektywy współdziała również z `#if` dyrektywy do kontrolowania kompilacja warunkowa programu źródłowego. Zobacz [#if, #elif, #else i #endif — dyrektywy](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md) Aby uzyskać więcej informacji.  
  
 W poniższym przykładzie `#undef` dyrektywy Usuwa definicje stałą symboliczne i makr. Należy pamiętać, że podano tylko identyfikator makra.  
  
```  
#define WIDTH 80  
#define ADD( X, Y ) ((X) + (Y))  
.  
.  
.  
#undef WIDTH  
#undef ADD  
```  
  
 **Dotyczące firmy Microsoft**  
  
 Makra może być niezdefiniowana w wierszu polecenia z opcją /U, następuje niezdefiniowanej nazwy makra. To polecenie powoduje odpowiednikiem sekwencji `#undef` *nazwy makra* instrukcje na początku pliku.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Dyrektywy preprocesora](../preprocessor/preprocessor-directives.md)