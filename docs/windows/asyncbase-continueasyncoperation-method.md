---
title: "AsyncBase::ContinueAsyncOperation — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: async/Microsoft::WRL::AsyncBase::ContinueAsyncOperation
dev_langs: C++
helpviewer_keywords: ContinueAsyncOperation method
ms.assetid: ce38181d-2fc3-4579-b0ce-237a3c7648bc
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 976ee601e836bbabbfbf65beca41f6fbd687cebb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="asyncbasecontinueasyncoperation-method"></a>AsyncBase::ContinueAsyncOperation — Metoda
Określa, czy operacja asynchroniczna przetwarzanie powinno być kontynuowane, czy należy zatrzymać.  
  
## <a name="syntax"></a>Składnia  
  
```  
inline bool ContinueAsyncOperation();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli bieżący stan operacji asynchronicznej jest *uruchomiona*, co oznacza operacji powinno być kontynuowane. W przeciwnym razie `false`, co oznacza operacji należy zatrzymać.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** async.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Asyncbase — klasa](../windows/asyncbase-class.md)