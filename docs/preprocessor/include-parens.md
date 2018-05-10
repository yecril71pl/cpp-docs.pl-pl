---
title: include() | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 756aea4400d98b2bf061a54955b3df4b4eddd993
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
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
  
 **KOŃCOWY określonego języka C++**  
  
## <a name="see-also"></a>Zobacz też  
 [atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)   
 [#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)