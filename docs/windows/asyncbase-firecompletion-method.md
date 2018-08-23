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
ms.openlocfilehash: 19b796b1fbc618bb909b186aa86d3c893c8536c5
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42600259"
---
# <a name="asyncbasefirecompletion-method"></a>AsyncBase::FireCompletion — Metoda

Wywołuje program obsługi zdarzenia zakończenia lub resetuje delegata wewnętrznego postępu.

## <a name="syntax"></a>Składnia

```cpp
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