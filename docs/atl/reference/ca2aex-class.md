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
ms.openlocfilehash: dfd8967d21005d83b38eeae36cfc147051d7beaf
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168530"
---
# <a name="ca2aex-class"></a>Klasa CA2AEX

Ta klasa jest używana przez makra konwersji ciągów CA2TEX i CT2AEX oraz typedef CA2A.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```cpp
template <int t_nBufferLength = 128>
class CA2AEX
```

### <a name="parameters"></a>Parametry

*t_nBufferLength*<br/>
Rozmiar buforu używany w procesie tłumaczenia. Domyślna długość to 128 bajtów.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CA2AEX::CA2AEX](#ca2aex)|Konstruktor.|
|[CA2AEX:: ~ CA2AEX](#dtor)|Destruktor.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CA2AEX:: operator LPSTR](#operator_lpstr)|Operator konwersji.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CA2AEX:: m_psz](#m_psz)|Element członkowski danych przechowujący ciąg źródłowy.|
|[CA2AEX:: m_szBuffer](#m_szbuffer)|Bufor statyczny używany do przechowywania przekonwertowanego ciągu.|

## <a name="remarks"></a>Uwagi

O ile nie jest wymagana dodatkowa funkcjonalność, użyj CA2TEX, CT2AEX lub CA2A w własnym kodzie.

Ta klasa zawiera bufor statyczny o stałym rozmiarze, który jest używany do przechowywania wyniku konwersji. Jeśli wynik jest zbyt duży, aby zmieścił się w buforze statycznym, Klasa przydziela pamięć przy użyciu **malloc**, zwalniając pamięć, gdy obiekt wykracza poza zakres. Dzięki temu, w przeciwieństwie do makr konwersji tekstu dostępnych we wcześniejszych wersjach ATL, ta klasa jest bezpieczna do użycia w pętlach i nie przechodzą stosu.

Jeśli klasa próbuje przydzielić pamięć na stercie i kończy się niepowodzeniem, `AtlThrow` wywoła z argumentem E_OUTOFMEMORY.

Domyślnie klasy konwersji ATL i makra używają strony kodowej ANSI bieżącego wątku dla konwersji.

Następujące makra są oparte na tej klasie:

- CA2TEX

- CT2AEX

Następujący element typedef jest oparty na tej klasie:

- CA2A

Aby zapoznać się z tymi makrami konwersji tekstu, zobacz [makra konwersji ATL i MFC String](string-conversion-macros.md).

## <a name="example"></a>Przykład

Zobacz [makra konwersji ciągów ATL i MFC,](string-conversion-macros.md) aby zapoznać się z przykładem użycia tych makr konwersji ciągów.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlconv. h

## <a name="ca2aexca2aex"></a><a name="ca2aex"></a>CA2AEX::CA2AEX

Konstruktor.

```cpp
CA2AEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2AEX(LPCSTR psz) throw(...);
```

### <a name="parameters"></a>Parametry

*psz*<br/>
Ciąg tekstowy do przekonwertowania.

*nCodePage*<br/>
Nieużywane w tej klasie.

### <a name="remarks"></a>Uwagi

Tworzy bufor wymagany do tłumaczenia.

## <a name="ca2aexca2aex"></a><a name="dtor"></a>CA2AEX:: ~ CA2AEX

Destruktor.

```cpp
~CA2AEX() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia przydzieloną bufor.

## <a name="ca2aexm_psz"></a><a name="m_psz"></a>CA2AEX:: m_psz

Element członkowski danych przechowujący ciąg źródłowy.

```cpp
LPSTR m_psz;
```

## <a name="ca2aexm_szbuffer"></a><a name="m_szbuffer"></a>CA2AEX:: m_szBuffer

Bufor statyczny używany do przechowywania przekonwertowanego ciągu.

```cpp
char m_szBuffer[ t_nBufferLength];
```

## <a name="ca2aexoperator-lpstr"></a><a name="operator_lpstr"></a>CA2AEX:: operator LPSTR

Operator konwersji.

```cpp
operator LPSTR() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca ciąg tekstowy jako typ LPSTR.

## <a name="see-also"></a>Zobacz także

[Klasa CA2CAEX](../../atl/reference/ca2caex-class.md)<br/>
[Klasa CA2WEX](../../atl/reference/ca2wex-class.md)<br/>
[Klasa CW2AEX](../../atl/reference/cw2aex-class.md)<br/>
[Klasa CW2CWEX](../../atl/reference/cw2cwex-class.md)<br/>
[Klasa CW2WEX](../../atl/reference/cw2wex-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
