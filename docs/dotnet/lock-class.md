---
title: Klasa Lock | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- msclr::lock
- msclr.lock
- lock
dev_langs: C++
helpviewer_keywords: lock class
ms.assetid: 5123edd9-6aed-497d-9a0b-f4b6d6c0d666
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: c2f2a8e371803d33a2c42508ec595681ada3bab8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="lock-class"></a>Klasa lock
Ta klasa automatyzuje pobranie blokady dla synchronizacji dostępu do obiektu przez wiele wątków.  Gdy utworzony otrzymuje blokady i po zniszczeniu jego wersje blokady.  
  
## <a name="syntax"></a>Składnia  
  
```  
ref class lock;  
```  
  
## <a name="remarks"></a>Uwagi  
 `lock`jest dostępna tylko dla obiektów CLR i można używać tylko w kodzie CLR.  
  
 Wewnętrznie używa klasy blokady <xref:System.Threading.Monitor> synchronizujący dostęp. Zobacz w tym temacie, aby uzyskać szczegółowe informacje o synchronizacji.  
  
## <a name="requirements"></a>Wymagania  
 **Plik nagłówka** \<msclr\lock.h >  
  
 **Namespace** msclr  
  
## <a name="see-also"></a>Zobacz też  
 [blokady](../dotnet/lock.md)   
 [lock, składowe](../dotnet/lock-members.md)