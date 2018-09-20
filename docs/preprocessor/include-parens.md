---
title: include() — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- include()
dev_langs:
- C++
helpviewer_keywords:
- include() attribute
ms.assetid: 86c9dcb2-d9e0-4fd5-97d7-0bb3e23d6ecc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 83f6bf58138a1e36e1c36131a448b456eb691c27
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46407585"
---
# <a name="include"></a>include()
**Określonego język C++**  
  
Wyłącza automatyczne wykluczenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
include("Name1"[,"Name2", ...])  
```  
  
### <a name="parameters"></a>Parametry  
*Nazwa1*  
Pierwszy element wymuszone dołączenia.  
  
*Nazwa2*  
Drugi element do uwzględnienia wymuszone (jeśli jest to konieczne).  
  
## <a name="remarks"></a>Uwagi  
 
Biblioteki typów mogą obejmować definicje elementy zdefiniowane w nagłówkach systemu lub inne biblioteki typów. `#import` próbuje uniknąć wiele błędów definicji wykluczając automatycznie takie elementy. Jeśli elementy zostały wyłączone, wskazane przez [ostrzeżenie kompilatora (poziom 3) C4192](../error-messages/compiler-warnings/compiler-warning-level-3-c4192.md), i nie powinny mieć been, ten atrybut można wyłączyć automatyczne wykluczenia. Ten atrybut może być dowolną liczbę argumentów, każda z nich nazwę element biblioteki typów które mają zostać uwzględnione.  
  
**KONIEC określonego języka C++**  
  
## <a name="see-also"></a>Zobacz też  
 
[atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)