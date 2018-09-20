---
title: Wykluczanie (#import) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- exclude
dev_langs:
- C++
helpviewer_keywords:
- exclude attribute
ms.assetid: 0883248a-d4bf-420e-9848-807b28fa976e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e5798c7515c411b9abf9d10229a6185e01bb92f7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46400201"
---
# <a name="exclude-import"></a>wykluczanie (#import)
**Określonego język C++**  
  
Pomija pliki nagłówkowe biblioteki typów generowanych elementów.  
  
## <a name="syntax"></a>Składnia  
  
```  
exclude("Name1"[, "Name2",...])  
```  
  
### <a name="parameters"></a>Parametry  
*Nazwa1*  
Pierwszy element do wykluczenia.  
  
*Nazwa2*  
Drugi element do wykluczenia (jeśli jest to konieczne).  
  
## <a name="remarks"></a>Uwagi  
 
Biblioteki typów mogą obejmować definicje elementy zdefiniowane w nagłówkach systemu lub inne biblioteki typów. Ten atrybut może być dowolną liczbę argumentów, jest element najwyższego poziomu typu biblioteki do wykluczenia.  
  
**KONIEC określonego języka C++**  
  
## <a name="see-also"></a>Zobacz też  
 
[atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)