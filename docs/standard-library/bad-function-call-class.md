---
title: "bad_function_call — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- functional/std::bad_function_call
dev_langs:
- C++
helpviewer_keywords:
- bad_function_call class
ms.assetid: b70a0268-43ff-4f3b-a283-faf1cb172d4c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1093181108a63a1b7ba2457ff412eb97ed6a9edf
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="badfunctioncall-class"></a>bad_function_call — Klasa
Raporty wywołanie funkcji uszkodzone.  
  
## <a name="syntax"></a>Składnia  
  
```  
class bad_function_call  
 : public std::exception {  
 };  
```  
  
## <a name="remarks"></a>Uwagi  
 Klasa opisuje wyjątek, aby wskazać, że wywołanie `operator()` na [funkcji klasy](../standard-library/function-class.md)
