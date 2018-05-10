---
title: AsyncBase::FireCompletion — metoda | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 0cd18d340a11575ed9f6f52d92a5910dcee1faec
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="asyncbasefirecompletion-method"></a>AsyncBase::FireCompletion — Metoda
Wywołuje program obsługi zdarzeń zakończenia lub resetuje delegata wewnętrzny postępu.  
  
## <a name="syntax"></a>Składnia  
  
```  
void FireCompletion(  
   void  
) override;  
  
virtual void FireCompletion();  
```  
  
## <a name="remarks"></a>Uwagi  
 Pierwszą wersję FireCompletion() resetuje zmiennej delegata wewnętrzny postępu. Druga wersja wywołuje program obsługi zdarzeń zakończenia, jeśli operacja asynchroniczna została ukończona.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** async.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [AsyncBase, klasa](../windows/asyncbase-class.md)