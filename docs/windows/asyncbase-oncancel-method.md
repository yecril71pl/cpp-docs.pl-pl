---
title: AsyncBase::OnCancel, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::OnCancel
dev_langs:
- C++
helpviewer_keywords:
- OnCancel method
ms.assetid: 4bd0b68e-a9df-4913-9f6c-e093ed55c3f9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 346cb4049f0833bdbc950b6806177321d107db28
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46380739"
---
# <a name="asyncbaseoncancel-method"></a>AsyncBase::OnCancel — Metoda

W przypadku przesłonięcia w klasie pochodnej, anuluje operację asynchroniczną.

## <a name="syntax"></a>Składnia

```cpp
virtual void OnCancel(
   void
) = 0;
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** async.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też

[AsyncBase, klasa](../windows/asyncbase-class.md)<br/>
[AsyncBase::Cancel, metoda](../windows/asyncbase-cancel-method.md)