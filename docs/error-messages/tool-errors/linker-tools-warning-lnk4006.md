---
title: "Ostrzeżenie LNK4006 narzędzi konsolidatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK4006
dev_langs:
- C++
helpviewer_keywords:
- LNK4006
ms.assetid: 3a637d17-1676-4ea6-bd8b-290137d28d3b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 021961029d274172119ae92aa10cc6a236dd973b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4006"></a>Ostrzeżenie LNK4006 narzędzi konsolidatora
symbol już zdefiniowany w obiekcie; druga definicja została zignorowana  
  
 Podany `symbol`, wyświetlane w postaci ozdobione, został zdefiniowany wiele razy. W przypadku tego ostrzeżenia `symbol` zostaną dodane dwa razy, ale jego pierwszy formularz, który będzie używany.  
  
 To ostrzeżenie można uzyskać, Jeśli spróbujesz scalić dwóch biblioteki importu do jednej.  
  
 Odbudowywania biblioteki wykonawczej języka C, możesz zignorować ten komunikat.  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Aby rozwiązać problem przy użyciu następujących możliwych rozwiązań  
  
1.  Podany `symbol` może być spakowanych funkcji utworzone przez kompilowania przy użyciu [/Gy](../../build/reference/gy-enable-function-level-linking.md). Ten symbol został uwzględniony w więcej niż jeden plik, ale został zmieniony między kompilacji. Skompiluj ponownie wszystkie pliki, które obejmują `symbol`.  
  
2.  Podany `symbol` mogły być zdefiniowane inaczej w dwóch obiektów w różne biblioteki.  
  
3.  Bezwzględnym może zdefiniowano dwa razy, podając inną wartość w każdej definicji.  
  
4.  Odebranie komunikat o błędzie w przypadku łączenia bibliotek, `symbol` już istnieje w bibliotece, którego jest dodawany.