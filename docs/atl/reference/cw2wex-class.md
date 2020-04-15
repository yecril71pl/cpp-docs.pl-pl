---
title: Klasa CW2WEX
ms.date: 11/04/2016
f1_keywords:
- CW2WEX
- ATLCONV/ATL::CW2WEX
- ATLCONV/ATL::CW2WEX::CW2WEX
- ATLCONV/ATL::CW2WEX::m_psz
- ATLCONV/ATL::CW2WEX::m_szBuffer
helpviewer_keywords:
- CW2WEX class
ms.assetid: 46262e56-e0d2-41fe-855b-0b67ecc8fcd7
ms.openlocfilehash: b116775a595f9fb3612d46e19526cf1396f85002
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330346"
---
# <a name="cw2wex-class"></a>Klasa CW2WEX

Ta klasa jest używana przez makra konwersji ciągów CW2TEX i CT2WEX oraz typedef CW2W.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
template <int t_nBufferLength = 128>
class CW2WEX
```

#### <a name="parameters"></a>Parametry

*t_nBufferLength*<br/>
Rozmiar buforu używanego w procesie tłumaczenia. Domyślna długość to 128 bajtów.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CW2WEX::CW2WEX](#cw2wex)|Konstruktor.|
|[CW2WEX::~CW2WEX](#dtor)|Destruktor.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CW2WEX::operator LPWSTR](#operator_lpwstr)|Operator konwersji.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CW2WEX::m_psz](#m_psz)|Element członkowski danych, który przechowuje ciąg źródłowy.|
|[CW2WEX::m_szBuffer](#m_szbuffer)|Bufor statyczny, używany do przechowywania przekonwertowanego ciągu.|

## <a name="remarks"></a>Uwagi

O ile nie jest wymagana dodatkowa funkcjonalność, użyj CW2TEX, CT2WEX lub CW2W w kodzie.

Ta klasa zawiera bufor statyczny o stałym rozmiarze, który jest używany do przechowywania wyniku konwersji. Jeśli wynik jest zbyt duży, aby zmieścić się w buforze statycznym, klasa przydziela pamięć za pomocą **malloc**, zwalniając pamięć, gdy obiekt wykracza poza zakres. Gwarantuje to, że w przeciwieństwie do makr konwersji tekstu dostępnych w poprzednich wersjach ATL, ta klasa jest bezpieczna w użyciu w pętlach i nie przepełnia stosu.

Jeśli klasa próbuje przydzielić pamięć na stercie i `AtlThrow` kończy się niepowodzeniem, wywoła argument E_OUTOFMEMORY.

Domyślnie klasy konwersji ATL i makra używają strony kodowej ANSI bieżącego wątku do konwersji.

Następujące makra są oparte na tej klasie:

- CW2TEX ( CW2TEX )

- 19.00.

Następująca typedef jest oparta na tej klasie:

- CW2W ( CW2W )

Aby zapoznać się z tymi makrami konwersji tekstu, zobacz [Makra konwersji ciągów ATL i MFC](string-conversion-macros.md).

## <a name="example"></a>Przykład

Zobacz [ATL i MFC String Konwersja Makra](string-conversion-macros.md) na przykład przy użyciu tych makr konwersji ciągów.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlconv.h

## <a name="cw2wexcw2wex"></a><a name="cw2wex"></a>CW2WEX::CW2WEX

Konstruktor.

```
CW2WEX(LPCWSTR psz, UINT nCodePage) throw(...);
CW2WEX( LPCWSTR  psz) throw(...);
```

### <a name="parameters"></a>Parametry

*Psz*<br/>
Ciąg tekstowy do konwersji.

*strona nCodePage*<br/>
Strona kodowa. Nie jest używany w tej klasie.

### <a name="remarks"></a>Uwagi

Tworzy bufor wymagany do tłumaczenia.

## <a name="cw2wexcw2wex"></a><a name="dtor"></a>CW2WEX::~CW2WEX

Destruktor..

```
~CW2WEX() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia przydzielony bufor.

## <a name="cw2wexm_psz"></a><a name="m_psz"></a>CW2WEX::m_psz

Element członkowski danych, który przechowuje ciąg źródłowy.

```
LPWSTR m_psz;
```

## <a name="cw2wexm_szbuffer"></a><a name="m_szbuffer"></a>CW2WEX::m_szBuffer

Bufor statyczny, używany do przechowywania przekonwertowanego ciągu.

```
wchar_t m_szBuffer[t_nBufferLength];
```

## <a name="cw2wexoperator-lpwstr"></a><a name="operator_lpwstr"></a>CW2WEX::operator LPWSTR

Operator odlewu.

```
operator LPWSTR() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca ciąg tekstowy jako typ LPWSTR.

## <a name="see-also"></a>Zobacz też

[Klasa CA2AEX](../../atl/reference/ca2aex-class.md)<br/>
[Klasa CA2CAEX](../../atl/reference/ca2caex-class.md)<br/>
[Klasa CA2WEX](../../atl/reference/ca2wex-class.md)<br/>
[Klasa CW2AEX](../../atl/reference/cw2aex-class.md)<br/>
[Klasa CW2CWEX](../../atl/reference/cw2cwex-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
