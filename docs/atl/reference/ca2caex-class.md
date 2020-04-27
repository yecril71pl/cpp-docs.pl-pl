---
title: Klasa CA2CAEX
ms.date: 11/04/2016
f1_keywords:
- CA2CAEX
- ATLCONV/ATL::CA2CAEX
- ATLCONV/ATL::CA2CAEX::CA2CAEX
- ATLCONV/ATL::CA2CAEX::m_psz
helpviewer_keywords:
- CA2CAEX class
ms.assetid: 388e7c1d-a144-474c-a182-b15f69a74bd8
ms.openlocfilehash: 505c1e369bc5949fea291a2172c16d5e52c75567
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168517"
---
# <a name="ca2caex-class"></a>Klasa CA2CAEX

Ta klasa jest używana przez makra konwersji ciągów CA2CTEX i CT2CAEX oraz typedef CA2CA.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```cpp
template<int t_nBufferLength = 128>
class CA2CAEX
```

### <a name="parameters"></a>Parametry

*t_nBufferLength*<br/>
Rozmiar buforu używany w procesie tłumaczenia. Domyślna długość to 128 bajtów.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CA2CAEX::CA2CAEX](#ca2caex)|Konstruktor.|
|[CA2CAEX:: ~ CA2CAEX](#dtor)|Destruktor.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CA2CAEX:: operator LPCSTR](#operator_lpcstr)|Operator konwersji.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CA2CAEX:: m_psz](#m_psz)|Element członkowski danych przechowujący ciąg źródłowy.|

## <a name="remarks"></a>Uwagi

O ile nie jest wymagana dodatkowa funkcjonalność, użyj CA2CTEX, CT2CAEX lub CA2CA w własnym kodzie.

Ta klasa jest bezpieczna do użycia w pętlach i nie przechodzą na stos. Domyślnie klasy konwersji ATL i makra będą używały strony kodowej ANSI bieżącego wątku dla konwersji.

Następujące makra są oparte na tej klasie:

- CA2CTEX

- CT2CAEX

Następujący element typedef jest oparty na tej klasie:

- CA2CA

Aby zapoznać się z tymi makrami konwersji tekstu, zobacz [makra konwersji ATL i MFC String](string-conversion-macros.md).

## <a name="example"></a>Przykład

Zobacz [makra konwersji ciągów ATL i MFC,](string-conversion-macros.md) aby zapoznać się z przykładem użycia tych makr konwersji ciągów.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlconv. h

## <a name="ca2caexca2caex"></a><a name="ca2caex"></a>CA2CAEX::CA2CAEX

Konstruktor.

```cpp
CA2CAEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2CAEX(LPCSTR psz) throw(...);
```

### <a name="parameters"></a>Parametry

*psz*<br/>
Ciąg tekstowy do przekonwertowania.

*nCodePage*<br/>
Nieużywane w tej klasie.

### <a name="remarks"></a>Uwagi

Tworzy bufor wymagany do tłumaczenia.

## <a name="ca2caexca2caex"></a><a name="dtor"></a>CA2CAEX:: ~ CA2CAEX

Destruktor.

```cpp
~CA2CAEX() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia przydzieloną bufor.

## <a name="ca2caexm_psz"></a><a name="m_psz"></a>CA2CAEX:: m_psz

Element członkowski danych przechowujący ciąg źródłowy.

```cpp
LPCSTR m_psz;
```

## <a name="ca2caexoperator-lpcstr"></a><a name="operator_lpcstr"></a>CA2CAEX:: operator LPCSTR

Operator konwersji.

```cpp
operator LPCSTR() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca ciąg tekstowy jako typ LPCSTR.

## <a name="see-also"></a>Zobacz także

[Klasa CA2AEX](../../atl/reference/ca2aex-class.md)<br/>
[Klasa CA2WEX](../../atl/reference/ca2wex-class.md)<br/>
[Klasa CW2AEX](../../atl/reference/cw2aex-class.md)<br/>
[Klasa CW2CWEX](../../atl/reference/cw2cwex-class.md)<br/>
[Klasa CW2WEX](../../atl/reference/cw2wex-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
