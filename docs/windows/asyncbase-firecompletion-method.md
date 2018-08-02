---
title: AsyncBase::FireCompletion, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::FireCompletion
dev_langs:
- C++
helpviewer_keywords:
- FireCompletion method
ms.assetid: b5e29d6d-52e7-4148-a7f3-a313b1359819
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fa5988516f3836749357b15295ac228b78fe3f04
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/02/2018
ms.locfileid: "39467244"
---
# <a name="asyncbasefirecompletion-method"></a>AsyncBase::FireCompletion — Metoda
Wywołuje program obsługi zdarzenia zakończenia lub resetuje delegata wewnętrznego postępu.  
  
## <a name="syntax"></a>Składnia  
  
```  
void FireCompletion(  
   void  
) override;  
  
virtual void FireCompletion();  
```  
  
## <a name="remarks"></a>Uwagi  
 Pierwsza wersja **FireCompletion()** resetuje zmiennej delegata wewnętrznego postępu. Druga wersja wywołuje program obsługi zdarzeń uzupełniania, jeśli operacja asynchroniczna została zakończona.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** async.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [AsyncBase, klasa](../windows/asyncbase-class.md)