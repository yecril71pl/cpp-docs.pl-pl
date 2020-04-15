---
title: Klasa CW2AEX
ms.date: 11/04/2016
f1_keywords:
- CW2AEX
- ATLCONV/ATL::CW2AEX
- ATLCONV/ATL::CW2AEX::CW2AEX
- ATLCONV/ATL::CW2AEX::m_psz
- ATLCONV/ATL::CW2AEX::m_szBuffer
helpviewer_keywords:
- CW2AEX class
ms.assetid: 44dc2cf5-dd30-440b-a9b9-b21b43f49843
ms.openlocfilehash: 849cbe5c26d7c7af7a8925a26057b5777554471d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330456"
---
# <a name="cw2aex-class"></a>Klasa CW2AEX

Ta klasa jest używana przez makra konwersji ciągów CT2AEX, CW2TEX, CW2CTEX i CT2CAEX oraz typedef CW2A.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
template<int t_nBufferLength = 128>
class CW2AEX
```

#### <a name="parameters"></a>Parametry

*t_nBufferLength*<br/>
Rozmiar buforu używanego w procesie tłumaczenia. Domyślna długość to 128 bajtów.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CW2AEX::CW2AEX](#cw2aex)|Konstruktor.|
|[CW2AEX::~CW2AEX](#dtor)|Destruktor.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CW2AEX::operator LPSTR](#operator_lpstr)|Operator konwersji.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CW2AEX::m_psz](#m_psz)|Element członkowski danych, który przechowuje ciąg źródłowy.|
|[CW2AEX::m_szBuffer](#m_szbuffer)|Bufor statyczny, używany do przechowywania przekonwertowanego ciągu.|

## <a name="remarks"></a>Uwagi

O ile nie jest wymagana dodatkowa funkcjonalność, użyj CT2AEX, CW2TEX, CW2CTEX, CT2CAEX lub CW2A w kodzie.

Ta klasa zawiera bufor statyczny o stałym rozmiarze, który jest używany do przechowywania wyniku konwersji. Jeśli wynik jest zbyt duży, aby zmieścić się w buforze statycznym, klasa przydziela pamięć za pomocą **malloc**, zwalniając pamięć, gdy obiekt wykracza poza zakres. Gwarantuje to, że w przeciwieństwie do makr konwersji tekstu dostępnych w poprzednich wersjach ATL, ta klasa jest bezpieczna w użyciu w pętlach i nie przepełnia stosu.

Jeśli klasa próbuje przydzielić pamięć na stercie i `AtlThrow` kończy się niepowodzeniem, wywoła argument E_OUTOFMEMORY.

Domyślnie klasy konwersji ATL i makra używają strony kodowej ANSI bieżącego wątku do konwersji. Jeśli chcesz zastąpić to zachowanie dla określonej konwersji, należy określić stronę kodową jako drugi parametr do konstruktora dla klasy.

Następujące makra są oparte na tej klasie:

- 2as

- CW2TEX ( CW2TEX )

- CW2CTEX ( CW2CTEX )

- CT2CAEX (ct2caex)

Następująca typedef jest oparta na tej klasie:

- CW2A ( CW2A )

Aby zapoznać się z tymi makrami konwersji tekstu, zobacz [Makra konwersji ciągów ATL i MFC](string-conversion-macros.md).

## <a name="example"></a>Przykład

Zobacz [ATL i MFC String Konwersja Makra](string-conversion-macros.md) na przykład przy użyciu tych makr konwersji ciągów.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlconv.h

## <a name="cw2aexcw2aex"></a><a name="cw2aex"></a>CW2AEX::CW2AEX

Konstruktor.

```
CW2AEX(LPCWSTR psz, UINT nCodePage) throw(...);
CW2AEX(LPCWSTR psz) throw(...);
```

### <a name="parameters"></a>Parametry

*Psz*<br/>
Ciąg tekstowy do konwersji.

*strona nCodePage*<br/>
Strona kodowa używana do przeprowadzania konwersji. Zobacz omówienie parametrów strony kodowej dla funkcji SDK systemu Windows [MultiByteToWideChar,](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar) aby uzyskać więcej szczegółów.

### <a name="remarks"></a>Uwagi

Przydziela bufor używany w procesie tłumaczenia.

## <a name="cw2aexcw2aex"></a><a name="dtor"></a>CW2AEX::~CW2AEX

Destruktor.

```
~CW2AEX() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia przydzielony bufor.

## <a name="cw2aexm_psz"></a><a name="m_psz"></a>CW2AEX::m_psz

Element członkowski danych, który przechowuje ciąg źródłowy.

```
LPSTR m_psz;
```

## <a name="cw2aexm_szbuffer"></a><a name="m_szbuffer"></a>CW2AEX::m_szBuffer

Bufor statyczny, używany do przechowywania przekonwertowanego ciągu.

```
char m_szBuffer[t_nBufferLength];
```

## <a name="cw2aexoperator-lpstr"></a><a name="operator_lpstr"></a>CW2AEX::operator LPSTR

Operator konwersji.

```
operator LPSTR() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca ciąg tekstowy jako typ LPSTR.

## <a name="see-also"></a>Zobacz też

[Klasa CA2AEX](../../atl/reference/ca2aex-class.md)<br/>
[Klasa CA2CAEX](../../atl/reference/ca2caex-class.md)<br/>
[Klasa CA2WEX](../../atl/reference/ca2wex-class.md)<br/>
[Klasa CW2CWEX](../../atl/reference/cw2cwex-class.md)<br/>
[Klasa CW2WEX](../../atl/reference/cw2wex-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
