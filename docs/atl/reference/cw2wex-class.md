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
ms.openlocfilehash: 647d233f25f27c96eeb3281272c1542057cabd4d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50468097"
---
# <a name="cw2wex-class"></a>Klasa CW2WEX

Ta klasa jest używana przez makra konwersji ciągów CW2TEX i CT2WEX i typedef CW2W.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
template <int t_nBufferLength = 128>
class CW2WEX
```

#### <a name="parameters"></a>Parametry

*t_nBufferLength*<br/>
Rozmiar buforu używany w procesie tłumaczenia. Domyślna długość to 128 bajtów.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CW2WEX::CW2WEX](#cw2wex)|Konstruktor.|
|[CW2WEX:: ~ CW2WEX](#dtor)|Destruktor.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CW2WEX::operator LPWSTR](#operator_lpwstr)|Operator konwersji.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CW2WEX::m_psz](#m_psz)|Element członkowski danych, który przechowuje ciąg źródłowy.|
|[CW2WEX::m_szBuffer](#m_szbuffer)|Bufor statyczne, używane do przechowywania przekonwertowany ciąg.|

## <a name="remarks"></a>Uwagi

O ile nie jest wymagane dodatkowe funkcje, należy użyć CW2TEX, CT2WEX lub CW2W w kodzie.

Ta klasa zawiera buforu statyczne stałym rozmiarze, który jest używany do przechowywania wynik konwersji. Jeśli wynik jest za duży, aby mieściły się w statycznych buforu, klasa przydziela pamięć przy użyciu **— funkcja malloc**, zwalniając pamięć, gdy obiekt wykracza poza zakres. Dzięki temu, w przeciwieństwie do tekstu makra konwersji dostępne w poprzednich wersjach biblioteki ATL, ta klasa bezpiecznym rozwiązaniem jest użycie w pętli i że nie będzie to przepełnienia stosu.

Jeśli klasa próbuje przydzielić pamięci na stosie i kończy się niepowodzeniem, wywoła `AtlThrow` z nieprawidłowym argumentem E_OUTOFMEMORY.

Domyślnie klasy konwersji ATL i makra stronę kodową ANSI bieżącego wątku na użytek konwersji.

Następujące makra są oparte na tej klasy:

- CW2TEX

- CT2WEX

Następujący element typedef opiera się na tej klasy:

- CW2W

Omówienie tych makr konwersji tekstu, zobacz [ATL i makr konwersji ciągu MFC](string-conversion-macros.md).

## <a name="example"></a>Przykład

Zobacz [ATL i makr konwersji ciągu MFC](string-conversion-macros.md) na przykład używanie makr konwersji tych parametrów.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlconv.h

##  <a name="cw2wex"></a>  CW2WEX::CW2WEX

Konstruktor.

```
CW2WEX(LPCWSTR psz, UINT nCodePage) throw(...);
CW2WEX( LPCWSTR  psz) throw(...);
```

### <a name="parameters"></a>Parametry

*psz*<br/>
Ciąg tekstowy, który ma zostać przekonwertowany.

*nCodePage*<br/>
Strona kodowa. Nie jest używany w tej klasie.

### <a name="remarks"></a>Uwagi

Tworzy buforu wymagane do tłumaczenia.

##  <a name="dtor"></a>  CW2WEX:: ~ CW2WEX

Destruktor...

```
~CW2WEX() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia przydzielonego buforu.

##  <a name="m_psz"></a>  CW2WEX::m_psz

Element członkowski danych, który przechowuje ciąg źródłowy.

```
LPWSTR m_psz;
```

##  <a name="m_szbuffer"></a>  CW2WEX::m_szBuffer

Bufor statyczne, używane do przechowywania przekonwertowany ciąg.

```
wchar_t m_szBuffer[t_nBufferLength];
```

##  <a name="operator_lpwstr"></a>  CW2WEX::operator LPWSTR

Operator rzutowania.

```
operator LPWSTR() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca ciąg tekstowy, ponieważ typ LPWSTR.

## <a name="see-also"></a>Zobacz też

[Klasa CA2AEX](../../atl/reference/ca2aex-class.md)<br/>
[Klasa CA2CAEX](../../atl/reference/ca2caex-class.md)<br/>
[Klasa CA2WEX](../../atl/reference/ca2wex-class.md)<br/>
[Klasa CW2AEX](../../atl/reference/cw2aex-class.md)<br/>
[Klasa CW2CWEX](../../atl/reference/cw2cwex-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
