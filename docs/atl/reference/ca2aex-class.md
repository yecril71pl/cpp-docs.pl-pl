---
title: Klasa CA2AEX
ms.date: 11/04/2016
f1_keywords:
- CA2AEX
- ATLCONV/ATL::CA2AEX
- ATLCONV/ATL::CA2AEX::CA2AEX
- ATLCONV/ATL::CA2AEX::m_psz
- ATLCONV/ATL::CA2AEX::m_szBuffer
helpviewer_keywords:
- CA2AEX class
ms.assetid: 57dc65df-d9cf-4a84-99d3-6e031dde3664
ms.openlocfilehash: 4f8b9f91e9bc499523fe3484bc76325e2efb8140
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319181"
---
# <a name="ca2aex-class"></a>Klasa CA2AEX

Ta klasa jest używana przez makra konwersji ciągów CA2TEX i CT2AEX oraz typedef CA2A.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
template <int t_nBufferLength = 128>
class CA2AEX
```

#### <a name="parameters"></a>Parametry

*t_nBufferLength*<br/>
Rozmiar buforu używanego w procesie tłumaczenia. Domyślna długość to 128 bajtów.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CA2AEX::CA2AEX](#ca2aex)|Konstruktor.|
|[CA2AEX::~CA2AEX](#dtor)|Destruktor.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CA2AEX::operator LPSTR](#operator_lpstr)|Operator konwersji.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CA2AEX::m_psz](#m_psz)|Element członkowski danych, który przechowuje ciąg źródłowy.|
|[CA2AEX::m_szBuffer](#m_szbuffer)|Bufor statyczny, używany do przechowywania przekonwertowanego ciągu.|

## <a name="remarks"></a>Uwagi

O ile nie jest wymagana dodatkowa funkcjonalność, użyj CA2TEX, CT2AEX lub CA2A we własnym kodzie.

Ta klasa zawiera bufor statyczny o stałym rozmiarze, który jest używany do przechowywania wyniku konwersji. Jeśli wynik jest zbyt duży, aby zmieścić się w buforze statycznym, klasa przydziela pamięć za pomocą **malloc**, zwalniając pamięć, gdy obiekt wykracza poza zakres. Gwarantuje to, że w przeciwieństwie do makr konwersji tekstu dostępnych w poprzednich wersjach ATL, ta klasa jest bezpieczna w użyciu w pętlach i nie przepełnia stosu.

Jeśli klasa próbuje przydzielić pamięć na stercie i `AtlThrow` kończy się niepowodzeniem, wywoła argument E_OUTOFMEMORY.

Domyślnie klasy konwersji ATL i makra używają strony kodowej ANSI bieżącego wątku do konwersji.

Następujące makra są oparte na tej klasie:

- Ca2TEX (właswoi

- 2as

Następująca typedef jest oparta na tej klasie:

- Ca2A (jednostka ca2a)

Aby zapoznać się z tymi makrami konwersji tekstu, zobacz [Makra konwersji ciągów ATL i MFC](string-conversion-macros.md).

## <a name="example"></a>Przykład

Zobacz [ATL i MFC String Konwersja Makra](string-conversion-macros.md) na przykład przy użyciu tych makr konwersji ciągów.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlconv.h

## <a name="ca2aexca2aex"></a><a name="ca2aex"></a>CA2AEX::CA2AEX

Konstruktor.

```
CA2AEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2AEX(LPCSTR psz) throw(...);
```

### <a name="parameters"></a>Parametry

*Psz*<br/>
Ciąg tekstowy do konwersji.

*strona nCodePage*<br/>
Nieużywane w tej klasie.

### <a name="remarks"></a>Uwagi

Tworzy bufor wymagany do tłumaczenia.

## <a name="ca2aexca2aex"></a><a name="dtor"></a>CA2AEX::~CA2AEX

Destruktor.

```
~CA2AEX() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia przydzielony bufor.

## <a name="ca2aexm_psz"></a><a name="m_psz"></a>CA2AEX::m_psz

Element członkowski danych, który przechowuje ciąg źródłowy.

```
LPSTR m_psz;
```

## <a name="ca2aexm_szbuffer"></a><a name="m_szbuffer"></a>CA2AEX::m_szBuffer

Bufor statyczny, używany do przechowywania przekonwertowanego ciągu.

```
char m_szBuffer[ t_nBufferLength];
```

## <a name="ca2aexoperator-lpstr"></a><a name="operator_lpstr"></a>CA2AEX::operator LPSTR

Operator konwersji.

```
operator LPSTR() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca ciąg tekstowy jako typ LPSTR.

## <a name="see-also"></a>Zobacz też

[Klasa CA2CAEX](../../atl/reference/ca2caex-class.md)<br/>
[Klasa CA2WEX](../../atl/reference/ca2wex-class.md)<br/>
[Klasa CW2AEX](../../atl/reference/cw2aex-class.md)<br/>
[Klasa CW2CWEX](../../atl/reference/cw2cwex-class.md)<br/>
[Klasa CW2WEX](../../atl/reference/cw2wex-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
