---
title: no_auto_exclude | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- no_auto_exclude
dev_langs:
- C++
helpviewer_keywords:
- no_auto_exclude attribute
ms.assetid: 3241ef9c-758a-4e86-bdc5-37da6072430f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 67d077ca620661ffda2e8664b2a4fb9ef5ea7168
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46408261"
---
# <a name="noautoexclude"></a>no_auto_exclude
**Określonego język C++**  
  
Wyłącza automatyczne wykluczenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
no_auto_exclude  
```  
  
## <a name="remarks"></a>Uwagi  
 
Biblioteki typów mogą obejmować definicje elementy zdefiniowane w nagłówkach systemu lub inne biblioteki typów. `#import` próbuje uniknąć wiele błędów definicji wykluczając automatycznie takie elementy. Po zakończeniu tej operacji [ostrzeżenie kompilatora (poziom 3) C4192](../error-messages/compiler-warnings/compiler-warning-level-3-c4192.md) będą wystawiane dla każdego elementu, które mają być wykluczone. To wykluczenie automatycznego można wyłączyć za pomocą tego atrybutu.  
  
**KONIEC określonego języka C++**  
  
## <a name="see-also"></a>Zobacz też  
 
[atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)