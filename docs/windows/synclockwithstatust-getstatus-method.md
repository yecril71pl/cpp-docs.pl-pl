---
title: "SyncLockWithStatusT::GetStatus — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::GetStatus
dev_langs: C++
helpviewer_keywords: GetStatus method
ms.assetid: d448b51d-a63d-40d9-a9ee-4aad3204118d
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 181735766e62aa1bf8c306bd425c6e6b03b2066d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="synclockwithstatustgetstatus-method"></a>SyncLockWithStatusT::GetStatus — Metoda
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
DWORD GetStatus() const;  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Wynik operacji oczekiwania na obiekt, który jest oparty na klasie synclockwithstatust — takie jak [obiektu Mutex](../windows/mutex-class1.md) lub [semafora](../windows/semaphore-class.md). Zero (0) oznacza operacji oczekiwania zwrócił stan sygnałowego; w przeciwnym razie innego stanu wystąpił, takie jak limit czasu upłynął.  
  
## <a name="remarks"></a>Uwagi  
 Pobiera bieżący obiekt synclockwithstatust — stan oczekiwania.  
  
 Funkcja GetStatus() pobiera wartości podstawowych [status_ —](../windows/synclockwithstatust-status-data-member.md) element członkowski danych. Gdy obiekt oparty na klasie synclockwithstatust — operacja wykonywana przez blokady, obiekt najpierw czeka na udostępnienie obiektu. Wynik tej operacji oczekiwania są przechowywane w `status_` element członkowski danych. Możliwe wartości `status_` element członkowski danych są zwracane wartości operacji oczekiwania. Aby uzyskać więcej informacji, zobacz zwracane wartości **WaitForSingleObjectEx()** funkcji w bibliotece MSDN.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>Zobacz też  
 [SyncLockWithStatusT, klasa](../windows/synclockwithstatust-class.md)