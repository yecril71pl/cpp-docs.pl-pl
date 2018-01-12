---
title: embedded_idl | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: embedded_idl
dev_langs: C++
helpviewer_keywords: embedded_idl attribute
ms.assetid: f1c1c2e8-3872-4172-8795-8d1288a20452
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0a83b635dc7d408b6296c0407984ddfb9a9f3659
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="embeddedidl"></a>embedded_idl
**Określonego języka C++**  
  
 Określa, czy biblioteki typów są zapisywane do pliku danych .tlh — kod wygenerowany przez atrybut zachowane.  
  
## <a name="syntax"></a>Składnia  
  
```  
embedded_idl[("param")]  
```  
  
#### <a name="parameters"></a>Parametry  
 `param`  
 Może być jedną z dwóch wartości:  
  
-   emitidl: informacje o typie zaimportowany z biblioteki typów będą znajdować się we IDL wygenerowany dla projektu oparte na atrybutach.  To jest domyślna i będzie obowiązywać jeśli nie określisz parametr `embedded_idl`.  
  
-   no_emitidl: informacje o typie zaimportowany z biblioteki typów nie są obecne w IDL wygenerowany dla projektu oparte na atrybutach.  
  
## <a name="example"></a>Przykład  
  
```  
// import_embedded_idl.cpp  
// compile with: /LD  
#include <windows.h>  
[module(name="MyLib2")];  
#import "\school\bin\importlib.tlb" embedded_idl("no_emitidl")  
```  
  
## <a name="remarks"></a>Uwagi  
 **KOŃCOWY określonego języka C++**  
  
## <a name="see-also"></a>Zobacz też  
 [atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)   
 [#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)