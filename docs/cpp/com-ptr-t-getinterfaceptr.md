---
title: _com_ptr_t::GetInterfacePtr
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::GetInterfacePtr
helpviewer_keywords:
- GetInterfacePtr method [C++]
ms.assetid: 55e3e2c7-c939-48b5-a905-4b9cbefeea7e
ms.openlocfilehash: f3244d59159855ff4060c944874e859cb5ec23ab
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170738"
---
# <a name="_com_ptr_tgetinterfaceptr"></a>_com_ptr_t::GetInterfacePtr

**Specyficzne dla firmy Microsoft**

Zwraca wskaźnik interfejsu hermetyzowanego.

## <a name="syntax"></a>Składnia

```
Interface* GetInterfacePtr( ) const throw( );
Interface*& GetInterfacePtr() throw();
```

## <a name="remarks"></a>Uwagi

Zwraca wskaźnik interfejsu hermetyzowanego, który może mieć wartość NULL.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[_com_ptr_t, klasa](../cpp/com-ptr-t-class.md)
