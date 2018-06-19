---
title: Ostrzeżenie LNK4006 narzędzi konsolidatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4006
dev_langs:
- C++
helpviewer_keywords:
- LNK4006
ms.assetid: 3a637d17-1676-4ea6-bd8b-290137d28d3b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 261d5dcc27c44291ddc6de4a6440cde040a84ed7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33302558"
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