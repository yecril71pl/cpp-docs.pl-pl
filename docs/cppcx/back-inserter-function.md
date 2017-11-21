---
title: "back_inserter — funkcja | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: collection/Windows::Foundation::Collections::back_inserter
dev_langs: C++
helpviewer_keywords: back_inserter Function
ms.assetid: 91476338-5548-44b7-bc7e-2150f4fbe31a
caps.latest.revision: "4"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: eb2b4925ba1b0c6c9a8728b66c338ea50229d0f2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="backinserter-function"></a>back_inserter — funkcja
Zwraca iterację, który służy do wstawiania elementów na końcu określonej kolekcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
template <typename T>
Platform::BackInsertIterator<T>   
    back_inserter(IVector<T>^ v);  
  
template<typename T>  
Platform::BackInsertIterator<T>   
   back_inserter(IObservableVector<T>^ v);  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Parametr typu szablonu.  
  
 `v`  
 Wskaźnik interfejsu, zapewniający dostęp do kolekcji źródłowej.  
  
### <a name="return-value"></a>Wartość zwracana  
 Iteratora.  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** collection.h  
  
 **Namespace:** Windows::Foundation::Collections  
  
## <a name="see-also"></a>Zobacz też  
 [Namespace Windows::Foundation::Collections](../cppcx/windows-foundation-collections-namespace-c-cx.md)