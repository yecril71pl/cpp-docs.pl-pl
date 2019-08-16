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
ms.openlocfilehash: 927b9f5031bb6262c2f4a071b535802eb9e6990a
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497955"
---
# <a name="ca2wex-class"></a>Klasa CA2WEX

Ta klasa jest używana przez makra konwersji ciągów CA2TEX, CA2CTEX, CT2WEX i CT2CWEX oraz typedef CA2W.

> [!IMPORTANT]
>  Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```
template <int t_nBufferLength = 128>
class CA2WEX
```

#### <a name="parameters"></a>Parametry

*t_nBufferLength*<br/>
Rozmiar buforu używany w procesie tłumaczenia. Domyślna długość to 128 bajtów.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CA2WEX::CA2WEX](#ca2wex)|Konstruktor.|
|[CA2WEX:: ~ CA2WEX](#dtor)|Destruktor.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CA2WEX:: operator LPWSTR](#operator_lpwstr)|Operator konwersji.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CA2WEX::m_psz](#m_psz)|Element członkowski danych przechowujący ciąg źródłowy.|
|[CA2WEX::m_szBuffer](#m_szbuffer)|Bufor statyczny używany do przechowywania przekonwertowanego ciągu.|

## <a name="remarks"></a>Uwagi

O ile nie jest wymagana dodatkowa funkcjonalność, użyj CA2TEX, CA2CTEX, CT2WEX, CT2CWEX lub CA2W w kodzie.

Ta klasa zawiera bufor statyczny o stałym rozmiarze, który jest używany do przechowywania wyniku konwersji. Jeśli wynik jest zbyt duży, aby zmieścił się w buforze statycznym, Klasa przydziela pamięć przy użyciu **malloc**, zwalniając pamięć, gdy obiekt wykracza poza zakres. Dzięki temu, w przeciwieństwie do makr konwersji tekstu dostępnych we wcześniejszych wersjach ATL, ta klasa jest bezpieczna do użycia w pętlach i nie przechodzą stosu.

Jeśli klasa próbuje przydzielić pamięć na stercie i kończy się niepowodzeniem, `AtlThrow` wywoła z argumentem E_OUTOFMEMORY.

Domyślnie klasy konwersji ATL i makra używają strony kodowej ANSI bieżącego wątku dla konwersji. Jeśli chcesz przesłonić to zachowanie dla określonej konwersji, określ stronę kodową jako drugi parametr konstruktora dla klasy.

Następujące makra są oparte na tej klasie:

- CA2TEX

- CA2CTEX

- CT2WEX

- CT2CWEX

Następujący element typedef jest oparty na tej klasie:

- CA2W

Aby zapoznać się z tymi makrami konwersji tekstu, zobacz [makra konwersji ATL i MFC String](string-conversion-macros.md).

## <a name="example"></a>Przykład

Zobacz [makra konwersji ciągów ATL i MFC,](string-conversion-macros.md) aby zapoznać się z przykładem użycia tych makr konwersji ciągów.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlconv. h

##  <a name="ca2wex"></a>CA2WEX::CA2WEX

Konstruktor.

```
CA2WEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2WEX(LPCSTR psz) throw(...);
```

### <a name="parameters"></a>Parametry

*psz*<br/>
Ciąg tekstowy do przekonwertowania.

*nCodePage*<br/>
Strona kodowa użyta do przeprowadzenia konwersji. Aby uzyskać więcej informacji, zobacz Omówienie parametrów strony kodowej dla funkcji Windows SDK [MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar) .

### <a name="remarks"></a>Uwagi

Przypisuje bufor używany w procesie tłumaczenia.

##  <a name="dtor"></a>CA2WEX:: ~ CA2WEX

Destruktor.

```
~CA2WEX() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia przydzieloną bufor.

##  <a name="m_psz"></a>CA2WEX::m_psz

Element członkowski danych przechowujący ciąg źródłowy.

```
LPWSTR m_psz;
```

##  <a name="m_szbuffer"></a>CA2WEX::m_szBuffer

Bufor statyczny używany do przechowywania przekonwertowanego ciągu.

```
wchar_t m_szBuffer[t_nBufferLength];
```

##  <a name="operator_lpwstr"></a>CA2WEX:: operator LPWSTR

Operator konwersji.

```
operator LPWSTR() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca ciąg tekstowy jako typ LPWSTR.

## <a name="see-also"></a>Zobacz także

[Klasa CA2AEX](../../atl/reference/ca2aex-class.md)<br/>
[Klasa CA2CAEX](../../atl/reference/ca2caex-class.md)<br/>
[Klasa CW2AEX](../../atl/reference/cw2aex-class.md)<br/>
[Klasa CW2CWEX](../../atl/reference/cw2cwex-class.md)<br/>
[Klasa CW2WEX](../../atl/reference/cw2wex-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
