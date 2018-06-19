---
title: Klasa Lock | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- msclr::lock
- msclr.lock
- lock
dev_langs:
- C++
helpviewer_keywords:
- lock class
ms.assetid: 5123edd9-6aed-497d-9a0b-f4b6d6c0d666
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a860f79b740e0f34eef33b7a96e0236835f1f6b3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33129700"
---
# <a name="lock-class"></a>Klasa lock
Ta klasa automatyzuje pobranie blokady dla synchronizacji dostępu do obiektu przez wiele wątków.  Gdy utworzony otrzymuje blokady i po zniszczeniu jego wersje blokady.  
  
## <a name="syntax"></a>Składnia  
  
```  
ref class lock;  
```  
  
## <a name="remarks"></a>Uwagi  
 `lock` jest dostępna tylko dla obiektów CLR i można używać tylko w kodzie CLR.  
  
 Wewnętrznie używa klasy blokady <xref:System.Threading.Monitor> synchronizujący dostęp. Zobacz w tym temacie, aby uzyskać szczegółowe informacje o synchronizacji.  
  
## <a name="requirements"></a>Wymagania  
 **Plik nagłówka** \<msclr\lock.h >  
  
 **Namespace** msclr  
  
## <a name="see-also"></a>Zobacz też  
 [blokady](../dotnet/lock.md)   
 [lock, składowe](../dotnet/lock-members.md)