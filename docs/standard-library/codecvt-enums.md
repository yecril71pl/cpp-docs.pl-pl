---
title: "&lt;codecvt —&gt; wyliczenia | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: codecvt/std::codecvt_mode
ms.assetid: 46a8b073-01bc-46d3-b3d3-a8540f9422c1
helpviewer_keywords: std::codecvt_mode
caps.latest.revision: "10"
manager: ghogen
ms.openlocfilehash: bba1b53abb7286c64bdaf79ec8cb2004ba67a9dd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ltcodecvtgt-enums"></a>&lt;codecvt —&gt; wyliczenia
  
##  <a name="codecvt_mode"></a>codecvt_mode — wyliczenie  
 Określa informacje o konfiguracji [ustawień regionalnych](../standard-library/locale-class.md) aspektami.  
  
```  
enum codecvt_mode {  
    consume_header = 4,  
    generate_header = 2,  
    little_endian = 1  
 };  
```  
  
### <a name="remarks"></a>Uwagi  
 Wyliczanie definiuje trzy stałe, które dostarczają informacje dotyczące ustawień regionalnych aspektami zadeklarowany w konfiguracji [ \<codecvt >](../standard-library/codecvt.md). Różne wartości to:  
  
- `consume_header`, do wykorzystania sekwencji początkowej nagłówka, podczas odczytywania wielobajtowych sekwencji i ustalić kolejności bajtów kolejnych wielobajtowych sekwencji do odczytu  
  
- `generate_header`, można wygenerować sekwencję początkowej nagłówka podczas zapisywania wielobajtowych sekwencji anonsowanie kolejności bajtów kolejnych wielobajtowych sekwencji do zapisania  
  
- `little_endian`, aby wygenerować wielobajtowych sekwencji w kolejności little endian, zamiast domyślnej kolejności big endian  
  
 Te stałe może być operacja logiczna ze sobą w dowolnej kombinacji.  
  
## <a name="see-also"></a>Zobacz też  
 [\<codecvt — >](../standard-library/codecvt.md)

