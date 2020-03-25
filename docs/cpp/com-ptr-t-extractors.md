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
ms.openlocfilehash: 31ac39104c041d1d119f6cd06de5f9c4a620dac0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190030"
---
# <a name="_com_ptr_t-extractors"></a>_com_ptr_t — Ekstraktory

**Specyficzne dla firmy Microsoft**

Wyodrębnij zhermetyzowany wskaźnik interfejsu COM.

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

- **interfejs operatora** <strong>\*</strong> zwraca zhermetyzowany wskaźnik interfejsu, który może mieć wartość null.

- **interfejs operatora &** Zwraca odwołanie do zhermetyzowanego wskaźnika interfejsu i wygeneruje błąd, jeśli wskaźnik ma wartość NULL.

- **operator** <strong>\*</strong> umożliwia obiektowi inteligentnego wskaźnika, aby działał tak, jakby był rzeczywistym interfejsem hermetyzowanym podczas wypełniania odwołania.

- **operator — >** Zezwala obiektowi inteligentnego wskaźnika na działanie tak, jakby był rzeczywistym interfejsem hermetyzowanym podczas wypełniania odwołania.

- **& operatora** Zwalnia wszystkie hermetyzowane wskaźnike interfejsu, zastępując go wartością NULL i zwraca adres zhermetyzowanego wskaźnika. Pozwala to na przekazanie inteligentnego wskaźnika przez adres do funkcji, która ma parametr *out* , za pomocą którego zwraca wskaźnik interfejsu.

- wartość **logiczna operatora** Umożliwia użycie obiektu inteligentnego wskaźnika w wyrażeniu warunkowym. Ten operator zwraca wartość TRUE, jeśli wskaźnik nie ma wartości NULL.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[_com_ptr_t, klasa](../cpp/com-ptr-t-class.md)
