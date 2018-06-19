---
title: LOKALNE (MASM) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- Local
dev_langs:
- C++
helpviewer_keywords:
- LOCAL directive
ms.assetid: 76147e2d-23ca-4f1e-8817-81428becd113
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ed9926d23f2e1e8636f31a6f586609ae22d38acd
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
ms.locfileid: "32053574"
---
# <a name="local-masm"></a>LOCAL (MASM)
W pierwszej dyrektywy wewnątrz makr **lokalnego** definiuje etykiety, które są unikatowe dla każdego wystąpienia makra.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      LOCAL localname [[, localname]]...  
LOCAL label [[ [count ] ]] [[:type]] [[, label [[ [count] ]] [[type]]]]...  
```  
  
## <a name="remarks"></a>Uwagi  
 W drugiej dyrektywy w ramach definicji procedury (**PROC**), **lokalnego** tworzy opartego na stosie zmienne, które istnieją w czasie trwania procedury. *Etykiety* może być prostej zmiennej lub tablica zawierająca *liczba* elementów.  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)