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
ms.openlocfilehash: 3384da733586c828496a8728a0f5855f92eeec35
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190472"
---
# <a name="_bstr_t_bstr_t"></a>_bstr_t::_bstr_t

**Specyficzne dla firmy Microsoft**

Konstruuje obiekt `_bstr_t`.

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
Obiekt `_bstr_t`, który ma zostać skopiowany.

*S2*<br/>
Ciąg wielobajtowy.

*S3*<br/>
Ciąg Unicode

*var*<br/>
Obiekt [_variant_t](../cpp/variant-t-class.md) .

*ani*<br/>
Istniejący obiekt `BSTR`.

*fCopy*<br/>
W przypadku wartości FALSE argument *BSTR* jest dołączany do nowego obiektu bez tworzenia kopii przez wywołanie `SysAllocString`.

## <a name="remarks"></a>Uwagi

W poniższej tabeli opisano konstruktory `_bstr_t`.

|Konstruktor|Opis|
|-----------------|-----------------|
|`_bstr_t( )`|Konstruuje domyślny obiekt `_bstr_t`, który hermetyzuje obiekt `BSTR` o wartości null.|
|`_bstr_t( _bstr_t&`  `s1`  `)`|Konstruuje obiekt `_bstr_t` jako kopię innej.<br /><br /> Jest to kopia *skrócona* , która zwiększa liczbę odwołań obiektu `BSTR` hermetyzowane zamiast tworzenia nowego.|
|`_bstr_t( char*`  `s2`  `)`|Konstruuje obiekt `_bstr_t`, wywołując `SysAllocString` do utworzenia nowego obiektu `BSTR`, a następnie hermetyzuje go.<br /><br /> Ten konstruktor najpierw wykonuje konwersję wielobajtowego na Unicode.|
|`_bstr_t( wchar_t*`  `s3`  `)`|Konstruuje obiekt `_bstr_t`, wywołując `SysAllocString` do utworzenia nowego obiektu `BSTR`, a następnie hermetyzuje go.|
|`_bstr_t( _variant_t&`  `var`  `)`|Konstruuje obiekt `_bstr_t` z obiektu `_variant_t`, pobierając obiekt `BSTR` z hermetyzowanego obiektu VARIANT.|
|`_bstr_t( BSTR``bstr` `, bool``fCopy``)`|Konstruuje obiekt `_bstr_t` z istniejącej `BSTR` (w przeciwieństwie do ciągu `wchar_t*`). Jeśli *fCopy* ma wartość false, dostarczona `BSTR` jest dołączona do nowego obiektu bez tworzenia nowej kopii z `SysAllocString`.<br /><br /> Ten konstruktor jest używany przez funkcje otoki w nagłówkach biblioteki typów do hermetyzacji i przejęcia własności `BSTR`, która jest zwracana przez metodę interfejsu.|

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[_bstr_t, klasa](../cpp/bstr-t-class.md)<br/>
[_variant_t, klasa](../cpp/variant-t-class.md)
