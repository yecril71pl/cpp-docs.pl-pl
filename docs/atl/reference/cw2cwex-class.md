---
title: Klasa CW2CWEX
ms.date: 11/04/2016
f1_keywords:
- CW2CWEX
- ATLCONV/ATL::CW2CWEX
- ATLCONV/ATL::CW2CWEX::CW2CWEX
- ATLCONV/ATL::CW2CWEX::m_psz
helpviewer_keywords:
- CW2CWEX class
ms.assetid: d654b22b-05a6-410f-a0ec-9a2cbbb4cca7
ms.openlocfilehash: 07dd0319586054403d8ed0c8efc813b4061e355a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330432"
---
# <a name="cw2cwex-class"></a>Klasa CW2CWEX

Ta klasa jest używana przez makra konwersji ciągów CW2CTEX i CT2CWEX oraz typedef CW2W.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
template<int t_nBufferLength = 128>
class CW2CWEX
```

#### <a name="parameters"></a>Parametry

*t_nBufferLength*<br/>
Rozmiar buforu używanego w procesie tłumaczenia. Domyślna długość to 128 bajtów.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CW2CWEX::CW2CWEX](#cw2cwex)|Konstruktor.|
|[CW2CWEX::~CW2CWEX](#dtor)|Destruktor.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CW2CWEX::operator LPCWSTR](#operator_lpcwstr)|Operator konwersji.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CW2CWEX::m_psz](#m_psz)|Element członkowski danych, który przechowuje ciąg źródłowy.|

## <a name="remarks"></a>Uwagi

O ile nie jest wymagana dodatkowa funkcjonalność, użyj CW2CTEX, CT2CWEX lub CW2W w kodzie.

Ta klasa jest bezpieczny w użyciu w pętlach i nie przepełnia stosu. Domyślnie klasy konwersji ATL i makra używają strony kodowej ANSI bieżącego wątku do konwersji.

Następujące makra są oparte na tej klasie:

- CW2CTEX ( CW2CTEX )

- CT2CWEX (CT2CWEX)

Następująca typedef jest oparta na tej klasie:

- CW2W ( CW2W )

Aby zapoznać się z tymi makrami konwersji tekstu, zobacz [Makra konwersji ciągów ATL i MFC](string-conversion-macros.md).

## <a name="example"></a>Przykład

Zobacz [ATL i MFC String Konwersja Makra](string-conversion-macros.md) na przykład przy użyciu tych makr konwersji ciągów.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlconv.h

## <a name="cw2cwexcw2cwex"></a><a name="cw2cwex"></a>CW2CWEX::CW2CWEX

Konstruktor.

```
CW2CWEX(LPCWSTR psz, UINT nCodePage) throw(...);
CW2CWEX(LPCWSTR psz) throw(...);
```

### <a name="parameters"></a>Parametry

*Psz*<br/>
Ciąg tekstowy do konwersji.

*strona nCodePage*<br/>
Strona kodowa. Nie jest używany w tej klasie.

### <a name="remarks"></a>Uwagi

Przydziela bufor używany w procesie tłumaczenia.

## <a name="cw2cwexcw2cwex"></a><a name="dtor"></a>CW2CWEX::~CW2CWEX

Destruktor.

```
~CW2CWEX() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia przydzielony bufor.

## <a name="cw2cwexm_psz"></a><a name="m_psz"></a>CW2CWEX::m_psz

Element członkowski danych, który przechowuje ciąg źródłowy.

```
LPCWSTR m_psz;
```

## <a name="cw2cwexoperator-lpcwstr"></a><a name="operator_lpcwstr"></a>CW2CWEX::operator LPCWSTR

Operator konwersji.

```
operator LPCWSTR() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca ciąg tekstowy jako typ LPCWSTR.

## <a name="see-also"></a>Zobacz też

[Klasa CA2AEX](../../atl/reference/ca2aex-class.md)<br/>
[Klasa CA2CAEX](../../atl/reference/ca2caex-class.md)<br/>
[Klasa CA2WEX](../../atl/reference/ca2wex-class.md)<br/>
[Klasa CW2AEX](../../atl/reference/cw2aex-class.md)<br/>
[Klasa CW2WEX](../../atl/reference/cw2wex-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
