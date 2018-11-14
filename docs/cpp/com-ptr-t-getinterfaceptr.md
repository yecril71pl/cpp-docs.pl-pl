---
title: _com_ptr_t::GetInterfacePtr
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::GetInterfacePtr
helpviewer_keywords:
- GetInterfacePtr method [C++]
ms.assetid: 55e3e2c7-c939-48b5-a905-4b9cbefeea7e
ms.openlocfilehash: dba5b5e2fcebf87ef196e2f33adedf88cc42b559
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51326176"
---
# <a name="comptrtgetinterfaceptr"></a>_com_ptr_t::GetInterfacePtr

**Microsoft Specific**

Zwraca wskaźnik zhermetyzowany interfejs.

## <a name="syntax"></a>Składnia

```
Interface* GetInterfacePtr( ) const throw( );
Interface*& GetInterfacePtr() throw();
```

## <a name="remarks"></a>Uwagi

Zwraca wskaźnik zhermetyzowany interfejs, który może mieć wartości NULL.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[_com_ptr_t, klasa](../cpp/com-ptr-t-class.md)