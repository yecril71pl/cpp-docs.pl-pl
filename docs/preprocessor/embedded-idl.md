---
title: embedded_idl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- embedded_idl
dev_langs:
- C++
helpviewer_keywords:
- embedded_idl attribute
ms.assetid: f1c1c2e8-3872-4172-8795-8d1288a20452
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9ad4a58cf02522eb7ca1c00055c73ff921e92b11
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46386122"
---
# <a name="embeddedidl"></a>embedded_idl
**Określonego język C++**  
  
Określa, czy biblioteki typów są zapisywane do pliku .tlh, z zachowanym kodem generowanych atrybutów.  
  
## <a name="syntax"></a>Składnia  
  
```  
embedded_idl[("param")]  
```  
  
### <a name="parameters"></a>Parametry  
*param*  
Może być jedną z dwóch wartości:  
  
- emitidl: informacje o typie zaimportowany z biblioteki typów będą znajdować się we IDL wygenerowany w projekcie z atrybutami.  To jest ustawieniem domyślnym i będą obowiązywać w przypadku nieokreślenia parametru, aby `embedded_idl`.  
  
- no_emitidl: informacje o typie zaimportowany z biblioteki typów nie będą obecne w pliku IDL wygenerowany w projekcie z atrybutami.  
  
## <a name="example"></a>Przykład  
  
```cpp  
// import_embedded_idl.cpp  
// compile with: /LD  
#include <windows.h>  
[module(name="MyLib2")];  
#import "\school\bin\importlib.tlb" embedded_idl("no_emitidl")  
```  
  
## <a name="remarks"></a>Uwagi  
 
**KONIEC określonego języka C++**  
  
## <a name="see-also"></a>Zobacz też  
 
[atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)