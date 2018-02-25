---
title: include() | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- include()
dev_langs:
- C++
helpviewer_keywords:
- include() attribute
ms.assetid: 86c9dcb2-d9e0-4fd5-97d7-0bb3e23d6ecc
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: da6a8bfc67f63caa8ee1f2699c8bb8675dbae775
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="include"></a>include()
**Określonego języka C++**  
  
 Wyłącza automatyczne wyłączenie.  
  
## <a name="syntax"></a>Składnia  
  
```  
include("Name1"[,"Name2", ...])  
```  
  
#### <a name="parameters"></a>Parametry  
 `Name1`  
 Pierwszy element do uwzględnienia wymuszone.  
  
 `Name2`  
 Drugi element do uwzględnienia wymuszanie (Jeśli to konieczne).  
  
## <a name="remarks"></a>Uwagi  
 Biblioteki typów może obejmować definicje elementów zdefiniowanych w nagłówkach systemu lub innych bibliotek typów. `#import` podejmuje próbę uniknięcia wiele błędów definicji automatycznie wyłączając takie elementy. Jeśli elementy zostały wyłączone, co wynika z [C4192 ostrzeżenie kompilatora (poziom 3)](../error-messages/compiler-warnings/compiler-warning-level-3-c4192.md), i nie powinny mieć zostały, ten atrybut można wyłączyć automatyczne wyłączenie. Ten atrybut może być dowolną liczbę argumentów jest nazwa elementu biblioteki typów, które zostaną uwzględnione.  
  
 KOŃCOWY określonego języka C++  
  
## <a name="see-also"></a>Zobacz też  
 [atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)   
 [#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)