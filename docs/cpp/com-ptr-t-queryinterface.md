---
title: _com_ptr_t::QueryInterface
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::QueryInterface
- _com_ptr_t.QueryInterface
helpviewer_keywords:
- QueryInterface method [C++]
ms.assetid: d03292f1-6b02-40db-9756-8b0837a97319
ms.openlocfilehash: 26dda2dff83ff0adbb7ef05c5e75f64b44138bd8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170674"
---
# <a name="_com_ptr_tqueryinterface"></a>_com_ptr_t::QueryInterface

**Specyficzne dla firmy Microsoft**

Wywołuje funkcję elementu członkowskiego **QueryInterface** elementu `IUnknown` na wyhermetyzowanym wskaźniku interfejsu.

## <a name="syntax"></a>Składnia

```
template<typename _InterfaceType> HRESULT QueryInterface (
   const IID& iid,
   _InterfaceType*& p
) throw ( );
template<typename _InterfaceType> HRESULT QueryInterface (
   const IID& iid,
   _InterfaceType** p
) throw( );
```

#### <a name="parameters"></a>Parametry

*IID*<br/>
`IID` wskaźnika interfejsu.

*St*<br/>
Pierwotny wskaźnik interfejsu.

## <a name="remarks"></a>Uwagi

Wywołuje `IUnknown::QueryInterface` na hermetyzowanym wskaźniku interfejsu z określonym `IID` i zwraca wynikowy wskaźnik interfejsu w *p*. Ta procedura zwraca wynik HRESULT wskazujący powodzenie lub niepowodzenie.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[_com_ptr_t, klasa](../cpp/com-ptr-t-class.md)
