---
title: Klasa CA2WEX
ms.date: 11/04/2016
f1_keywords:
- CA2WEX
- ATLCONV/ATL::CA2WEX
- ATLCONV/ATL::CA2WEX::CA2WEX
- ATLCONV/ATL::CA2WEX::m_psz
- ATLCONV/ATL::CA2WEX::m_szBuffer
helpviewer_keywords:
- CA2WEX class
ms.assetid: 317d9ffb-e84f-47e8-beda-57e28fb19124
ms.openlocfilehash: c9123e163ca828fa71fe217e46537ceb18e6f549
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319128"
---
# <a name="ca2wex-class"></a>Klasa CA2WEX

Ta klasa jest używana przez makra konwersji ciągów CA2TEX, CA2CTEX, CT2WEX i CT2CWEX oraz typedef CA2W.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
template <int t_nBufferLength = 128>
class CA2WEX
```

#### <a name="parameters"></a>Parametry

*t_nBufferLength*<br/>
Rozmiar buforu używanego w procesie tłumaczenia. Domyślna długość to 128 bajtów.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CA2WEX::CA2WEX](#ca2wex)|Konstruktor.|
|[CA2WEX::~CA2WEX](#dtor)|Destruktor.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CA2WEX::operator LPWSTR](#operator_lpwstr)|Operator konwersji.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CA2WEX::m_psz](#m_psz)|Element członkowski danych, który przechowuje ciąg źródłowy.|
|[CA2WEX::m_szBuffer](#m_szbuffer)|Bufor statyczny, używany do przechowywania przekonwertowanego ciągu.|

## <a name="remarks"></a>Uwagi

Jeśli nie jest wymagana dodatkowa funkcjonalność, użyj ca2TEX, CA2CTEX, CT2WEX, CT2CWEX lub CA2W w kodzie.

Ta klasa zawiera bufor statyczny o stałym rozmiarze, który jest używany do przechowywania wyniku konwersji. Jeśli wynik jest zbyt duży, aby zmieścić się w buforze statycznym, klasa przydziela pamięć za pomocą **malloc**, zwalniając pamięć, gdy obiekt wykracza poza zakres. Gwarantuje to, że w przeciwieństwie do makr konwersji tekstu dostępnych w poprzednich wersjach ATL, ta klasa jest bezpieczna w użyciu w pętlach i nie przepełnia stosu.

Jeśli klasa próbuje przydzielić pamięć na stercie i `AtlThrow` kończy się niepowodzeniem, wywoła argument E_OUTOFMEMORY.

Domyślnie klasy konwersji ATL i makra używają strony kodowej ANSI bieżącego wątku do konwersji. Jeśli chcesz zastąpić to zachowanie dla określonej konwersji, należy określić stronę kodową jako drugi parametr do konstruktora dla klasy.

Następujące makra są oparte na tej klasie:

- Ca2TEX (właswoi

- OKRĘG WYBORCZY CA2CTEX

- 19.00.

- CT2CWEX (CT2CWEX)

Następująca typedef jest oparta na tej klasie:

- Ca2W (jednostka ca2w)

Aby zapoznać się z tymi makrami konwersji tekstu, zobacz [Makra konwersji ciągów ATL i MFC](string-conversion-macros.md).

## <a name="example"></a>Przykład

Zobacz [ATL i MFC String Konwersja Makra](string-conversion-macros.md) na przykład przy użyciu tych makr konwersji ciągów.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlconv.h

## <a name="ca2wexca2wex"></a><a name="ca2wex"></a>CA2WEX::CA2WEX

Konstruktor.

```
CA2WEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2WEX(LPCSTR psz) throw(...);
```

### <a name="parameters"></a>Parametry

*Psz*<br/>
Ciąg tekstowy do konwersji.

*strona nCodePage*<br/>
Strona kodowa używana do przeprowadzania konwersji. Zobacz omówienie parametrów strony kodowej dla funkcji SDK systemu Windows [MultiByteToWideChar,](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar) aby uzyskać więcej szczegółów.

### <a name="remarks"></a>Uwagi

Przydziela bufor używany w procesie tłumaczenia.

## <a name="ca2wexca2wex"></a><a name="dtor"></a>CA2WEX::~CA2WEX

Destruktor.

```
~CA2WEX() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia przydzielony bufor.

## <a name="ca2wexm_psz"></a><a name="m_psz"></a>CA2WEX::m_psz

Element członkowski danych, który przechowuje ciąg źródłowy.

```
LPWSTR m_psz;
```

## <a name="ca2wexm_szbuffer"></a><a name="m_szbuffer"></a>CA2WEX::m_szBuffer

Bufor statyczny, używany do przechowywania przekonwertowanego ciągu.

```
wchar_t m_szBuffer[t_nBufferLength];
```

## <a name="ca2wexoperator-lpwstr"></a><a name="operator_lpwstr"></a>CA2WEX::operator LPWSTR

Operator konwersji.

```
operator LPWSTR() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca ciąg tekstowy jako typ LPWSTR.

## <a name="see-also"></a>Zobacz też

[Klasa CA2AEX](../../atl/reference/ca2aex-class.md)<br/>
[Klasa CA2CAEX](../../atl/reference/ca2caex-class.md)<br/>
[Klasa CW2AEX](../../atl/reference/cw2aex-class.md)<br/>
[Klasa CW2CWEX](../../atl/reference/cw2cwex-class.md)<br/>
[Klasa CW2WEX](../../atl/reference/cw2wex-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
