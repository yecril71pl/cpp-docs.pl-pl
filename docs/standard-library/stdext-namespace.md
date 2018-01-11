---
title: "stdext — Namespace | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 09/06/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: stdext
dev_langs: C++
helpviewer_keywords:
- _DEFINE_DEPRECATED_HASH_CLASSES symbol
- stdext namespace
ms.assetid: 3e94fc89-0584-424f-bc09-081b73379545
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 59da07c0cea58e9fc4b544b9f3bad937b2951f9e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="stdext-namespace"></a>stdext — Przestrzeń nazw

Elementy członkowskie [ \<hash_map >](../standard-library/hash-map.md) i [ \<hash_set >](../standard-library/hash-set.md) pliki nagłówkowe nie są obecnie częścią norma ISO C++. W związku z tym te typy i składniki zostały przeniesione z `std` przestrzeni nazw do przestrzeni nazw `stdext`, aby pozostać zgodność ze standardem C++.

Podczas kompilowania za pomocą [/Ze](../build/reference/za-ze-disable-language-extensions.md), co jest ustawieniem domyślnym kompilatora ostrzega na korzystanie z `std` dla członków \<hash_map > i \<hash_set > Pliki nagłówków. Aby wyłączyć ostrzeżenia, należy użyć [ostrzeżenie](../preprocessor/warning.md) pragma.

Mieć kompilator generuje błąd stosowania `std` dla członków \<hash_map > i \<hash_set > pliki nagłówkowe z **/Ze**, Dodaj następujące dyrektywy przed `#include` wszystkie pliki nagłówkowe standardowej biblioteki C++.

```cpp  
#define _DEFINE_DEPRECATED_HASH_CLASSES 0  
```  

Podczas kompilowania za pomocą **/Za**, kompilator generuje błąd.  

## <a name="see-also"></a>Zobacz też

[Standardowa biblioteka C++ — przegląd](../standard-library/cpp-standard-library-overview.md)

