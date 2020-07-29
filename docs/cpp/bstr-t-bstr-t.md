---
title: _bstr_t::_bstr_t
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::_bstr_t
helpviewer_keywords:
- BSTR object
- _bstr_t method [C++]
- _bstr_t class
ms.assetid: 116d994e-5a72-4351-afbe-866c80b4c165
ms.openlocfilehash: 843d6aa0e04595143d7da585e95d58e97fe80db0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221838"
---
# <a name="_bstr_t_bstr_t"></a>_bstr_t::_bstr_t

**Specyficzne dla firmy Microsoft**

Konstruuje `_bstr_t` obiekt.

## <a name="syntax"></a>Składnia

```
_bstr_t( ) throw( );
_bstr_t(
   const _bstr_t& s1
) throw( );
_bstr_t(
   const char* s2
);
_bstr_t(
   const wchar_t* s3
);
_bstr_t(
   const _variant_t& var
);
_bstr_t(
   BSTR bstr,
   bool fCopy
);
```

#### <a name="parameters"></a>Parametry

*S2*<br/>
`_bstr_t`Obiekt do skopiowania.

*S2*<br/>
Ciąg wielobajtowy.

*S3*<br/>
Ciąg Unicode

*funkcję*<br/>
Obiekt [_variant_t](../cpp/variant-t-class.md) .

*bstr*<br/>
Istniejący `BSTR` obiekt.

*fCopy*<br/>
Jeśli **`false`** argument *BSTR* jest dołączony do nowego obiektu bez tworzenia kopii przez wywołanie metody `SysAllocString` .

## <a name="remarks"></a>Uwagi

W poniższej tabeli opisano `_bstr_t` konstruktory.

|Konstruktor|Opis|
|-----------------|-----------------|
|`_bstr_t( )`|Konstruuje `_bstr_t` obiekt domyślny, który hermetyzuje obiekt o wartości null `BSTR` .|
|`_bstr_t( _bstr_t&`  `s1`  `)`|Tworzy `_bstr_t` obiekt jako kopię innej.<br /><br /> Jest to kopia *skrócona* , która zwiększa liczbę odwołań obiektu hermetyzowanego `BSTR` zamiast tworzenia nowego.|
|`_bstr_t( char*`  `s2`  `)`|Konstruuje `_bstr_t` obiekt przez wywołanie, `SysAllocString` Aby utworzyć nowy `BSTR` obiekt, a następnie hermetyzuje go.<br /><br /> Ten konstruktor najpierw wykonuje konwersję wielobajtowego na Unicode.|
|`_bstr_t( wchar_t*`  `s3`  `)`|Konstruuje `_bstr_t` obiekt przez wywołanie, `SysAllocString` Aby utworzyć nowy `BSTR` obiekt, a następnie hermetyzuje go.|
|`_bstr_t( _variant_t&`  `var`  `)`|Konstruuje `_bstr_t` obiekt z `_variant_t` obiektu, najpierw pobierając `BSTR` obiekt z hermetyzowanego obiektu Variant.|
|`_bstr_t( BSTR`  `bstr` `, bool`  `fCopy`  `)`|Konstruuje `_bstr_t` obiekt z istniejącego `BSTR` (w przeciwieństwie do `wchar_t*` ciągu). Jeśli *fCopy* ma wartość false, dostarczony `BSTR` element jest dołączany do nowego obiektu bez tworzenia nowej kopii przy użyciu `SysAllocString` .<br /><br /> Ten konstruktor jest używany przez funkcje otoki w nagłówkach biblioteki typów do hermetyzacji i przejęcia własności `BSTR` zwracanej przez metodę interfejsu.|

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Klasa _bstr_t](../cpp/bstr-t-class.md)<br/>
[Klasa _variant_t](../cpp/variant-t-class.md)
