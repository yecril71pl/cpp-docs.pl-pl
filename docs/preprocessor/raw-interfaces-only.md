---
title: raw_interfaces_only — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- raw_interfaces_only
dev_langs:
- C++
helpviewer_keywords:
- raw_interfaces_only attribute
ms.assetid: 87056c6d-3f34-4248-af58-f5775a35bfb7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8f217c0dad3bf74ab930cf1f66392fe22d9df832
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46446557"
---
# <a name="rawinterfacesonly"></a>raw_interfaces_only
**Określonego język C++**  
  
Pomija generację funkcje otoki obsługi błędów i [właściwość](../cpp/property-cpp.md) deklaracji, korzystających z tych funkcji otoki.  
  
## <a name="syntax"></a>Składnia  
  
```  
raw_interfaces_only  
```  
  
## <a name="remarks"></a>Uwagi  
 
**Raw_interfaces_only —** atrybut również powoduje, że domyślny prefiks używany w nazwach funkcji inną niż właściwość, które mają zostać usunięte. Zazwyczaj jest prefiks **raw_**. Jeśli ten atrybut jest określony, nazwy funkcji są bezpośrednio z biblioteki typów.  
  
Ten atrybut umożliwia uwidocznienie niskiego poziomu zawartość biblioteki typów.  
  
**KONIEC określonego języka C++**  
  
## <a name="see-also"></a>Zobacz też  
 
[atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)