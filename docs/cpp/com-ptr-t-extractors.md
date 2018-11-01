---
title: _com_ptr_t — Ekstraktory
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::operatorInterface&
- _com_ptr_t::operatorbool
- _com_ptr_t::operator->
- _com_ptr_t::operator*
helpviewer_keywords:
- operator Interface& [C++]
- '* operator [C++], with specific objects'
- operator& [C++]
- operator* [C++]
- -> operator [C++], with specific objects
- '& operator [C++], with specific objects'
- operator Interface* [C++]
- operator * [C++]
- operator->
- operator bool
- extractors, _com_ptr_t class
- extractors [C++]
ms.assetid: 194b9e0e-123c-49ff-a187-0a7fcd68145a
ms.openlocfilehash: 494507592222a7cd6334f2272c3a306e61e5d47f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50545980"
---
# <a name="comptrt-extractors"></a>_com_ptr_t — Ekstraktory

**Microsoft Specific**

Wyodrębnij zhermetyzowanego wskaźnika interfejsu COM.

## <a name="syntax"></a>Składnia

```
operator Interface*( ) const throw( ); 
operator Interface&( ) const; 
Interface& operator*( ) const; 
Interface* operator->( ) const; 
Interface** operator&( ) throw( ); 
operator bool( ) const throw( );
```

## <a name="remarks"></a>Uwagi

- **Operator interfejsu** <strong>\*</strong> zwraca wskaźnik zhermetyzowany interfejs, który może mieć wartości NULL.

- **Operator interfejs &** zwraca odwołanie do wskaźnika zhermetyzowany interfejs i generuje błąd, jeśli wskaźnik jest pusty.

- **operator** <strong>\*</strong> umożliwia obiekt inteligentny wskaźnik do działania, tak jakby był to rzeczywisty zhermetyzowany interfejs podczas wyłuskiwany.

- **operator ->** umożliwia obiekt inteligentny wskaźnik do działania, tak jakby był to rzeczywisty zhermetyzowany interfejs podczas wyłuskiwany.

- **Operator &** zwalnia dowolny wskaźnik zhermetyzowany interfejs, zastępując wartość NULL i zwraca adres zhermetyzowanego wskaźnika. Umożliwia to inteligentny wskaźnik do przekazania do funkcji, która ma, przy użyciu adresu *się* parametru za pomocą którego funkcja zwraca wskaźnik interfejsu.

- **Operator bool** umożliwia obiekt inteligentny wskaźnik do użycia w wyrażeniu warunkowym. Ten operator zwraca wartość PRAWDA, jeśli wskaźnik nie jest równa NULL.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[_com_ptr_t, klasa](../cpp/com-ptr-t-class.md)