---
title: _com_ptr_t — Ekstraktory
description: Opisuje operatory wyodrębniania dla klasy _com_ptr_t.
ms.date: 07/07/2020
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
ms.openlocfilehash: e7b06bb11ab34a1a1a7f6fab98d177821f60b20c
ms.sourcegitcommit: e17cc8a478b51739d67304d7d82422967b35f716
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/08/2020
ms.locfileid: "86127861"
---
# <a name="_com_ptr_t-extractors"></a>`_com_ptr_t`Ekstraktory

**specyficzne dla firmy Microsoft**

Wyodrębnij zhermetyzowany wskaźnik interfejsu COM.

## <a name="syntax"></a>Składnia

```c++
operator Interface*( ) const throw( );
operator Interface&( ) const;
Interface& operator*( ) const;
Interface* operator->( ) const;
Interface** operator&( ) throw( );
operator bool( ) const throw( );
```

## <a name="remarks"></a>Uwagi

- **`operator Interface*`** Zwraca wskaźnik interfejsu hermetyzowanego, który może mieć wartość NULL.

- **`operator Interface&`** Zwraca odwołanie do zhermetyzowanego wskaźnika interfejsu i wygeneruje błąd, jeśli wskaźnik ma wartość NULL.

- **`operator*`** Zezwala obiektowi inteligentnego wskaźnika na działanie tak, jakby był rzeczywistym interfejsem hermetyzowanym podczas wypełniania odwołania.

- **`operator->`** Zezwala obiektowi inteligentnego wskaźnika na działanie tak, jakby był rzeczywistym interfejsem hermetyzowanym podczas wypełniania odwołania.

- **`operator&`** Zwalnia wszystkie hermetyzowane wskaźnike interfejsu, zastępując go wartością NULL i zwraca adres zhermetyzowanego wskaźnika. Ten operator umożliwia przekazanie inteligentnego wskaźnika przez adres do funkcji, która ma parametr *out* , za pomocą którego zwraca wskaźnik interfejsu.

- **`operator bool`** Umożliwia użycie obiektu inteligentnego wskaźnika w wyrażeniu warunkowym. Ten operator zwraca wartość TRUE, jeśli wskaźnik nie ma wartości NULL.

  > [!NOTE]
  > Ponieważ **`operator bool`** nie jest zadeklarowany jako **`explicit`** , `_com_ptr_t` jest niejawnie konwertowany na **`bool`** , który jest konwertowany na dowolny typ skalarny. Może to spowodować nieoczekiwane konsekwencje w kodzie. Włącz [Ostrzeżenie kompilatora (poziom 4) C4800](../error-messages/compiler-warnings/compiler-warning-level-3-c4800.md) , aby zapobiec przypadkowemu użyciu tej konwersji.

## <a name="see-also"></a>Zobacz też

[_com_ptr_t — klasa](../cpp/com-ptr-t-class.md)
