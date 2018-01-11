---
title: "no_auto_exclude — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: no_auto_exclude
dev_langs: C++
helpviewer_keywords: no_auto_exclude attribute
ms.assetid: 3241ef9c-758a-4e86-bdc5-37da6072430f
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 981b67a27533f5015435965e831f7d2a86aa9948
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="noautoexclude"></a>no_auto_exclude
**Określonego języka C++**  
  
 Wyłącza automatyczne wyłączenie.  
  
## <a name="syntax"></a>Składnia  
  
```  
no_auto_exclude  
```  
  
## <a name="remarks"></a>Uwagi  
 Biblioteki typów może obejmować definicje elementów zdefiniowanych w nagłówkach systemu lub innych bibliotek typów. `#import`podejmuje próbę uniknięcia wiele błędów definicji automatycznie wyłączając takie elementy. Po zakończeniu [C4192 ostrzeżenie kompilatora (poziom 3)](../error-messages/compiler-warnings/compiler-warning-level-3-c4192.md) będą wystawiane dla każdego elementu mają być wykluczone. To wykluczenie automatycznego można wyłączyć za pomocą tego atrybutu.  
  
 **KOŃCOWY określonego języka C++**  
  
## <a name="see-also"></a>Zobacz też  
 [atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)   
 [#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)