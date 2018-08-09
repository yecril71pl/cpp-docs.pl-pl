---
title: SyncLockWithStatusT::GetStatus, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::GetStatus
dev_langs:
- C++
helpviewer_keywords:
- GetStatus method
ms.assetid: d448b51d-a63d-40d9-a9ee-4aad3204118d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4677239bbcaff0c72eb11ade259f47531a616f19
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39649639"
---
# <a name="synclockwithstatustgetstatus-method"></a>SyncLockWithStatusT::GetStatus — Metoda
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
DWORD GetStatus() const;  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Wynik operacji oczekiwania na obiekt, który jest oparty na **synclockwithstatust —** klasy, takie jak [Mutex](../windows/mutex-class1.md) lub [semafora](../windows/semaphore-class.md). Zero (0) oznacza, że operacji oczekiwania zwrócone sygnalizowanego stanu; w przeciwnym razie inny stan wystąpił, takie jak wartość limitu czasu, który upłynął.  
  
## <a name="remarks"></a>Uwagi  
 Pobiera stan oczekiwania bieżącego **synclockwithstatust —** obiektu.  
  
 Funkcja GetStatus() pobiera wartości elementu bazowego [status_ — element](../windows/synclockwithstatust-status-data-member.md) element członkowski danych. Gdy obiekt jest oparty na **synclockwithstatust —** klasy wykonuje operację blokady, obiekt najpierw czeka na udostępnienie obiektu. Wynikiem tej operacji oczekiwania są przechowywane w `status_` element członkowski danych. Możliwe wartości `status_` element członkowski danych są zwracane wartości operacji oczekiwania. Aby uzyskać więcej informacji, zobacz wartości zwracanych metody `WaitForSingleObjectEx()` funkcji w bibliotece MSDN.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>Zobacz też  
 [SyncLockWithStatusT, klasa](../windows/synclockwithstatust-class.md)