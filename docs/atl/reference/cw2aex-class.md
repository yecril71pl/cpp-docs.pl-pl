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
ms.openlocfilehash: 4dda1cb9e54c44f7940475660bc629192b9ead61
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496266"
---
# <a name="cw2aex-class"></a>Klasa CW2AEX

Ta klasa jest używana przez makra konwersji ciągów CT2AEX, CW2TEX, CW2CTEX i CT2CAEX oraz typedef CW2A.

> [!IMPORTANT]
>  Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```
template<int t_nBufferLength = 128>
class CW2AEX
```

#### <a name="parameters"></a>Parametry

*t_nBufferLength*<br/>
Rozmiar buforu używany w procesie tłumaczenia. Domyślna długość to 128 bajtów.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CW2AEX::CW2AEX](#cw2aex)|Konstruktor.|
|[CW2AEX::~CW2AEX](#dtor)|Destruktor.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CW2AEX:: operator LPSTR](#operator_lpstr)|Operator konwersji.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CW2AEX::m_psz](#m_psz)|Element członkowski danych przechowujący ciąg źródłowy.|
|[CW2AEX::m_szBuffer](#m_szbuffer)|Bufor statyczny używany do przechowywania przekonwertowanego ciągu.|

## <a name="remarks"></a>Uwagi

O ile nie jest wymagana dodatkowa funkcjonalność, użyj CT2AEX, CW2TEX, CW2CTEX, CT2CAEX lub CW2A w kodzie.

Ta klasa zawiera bufor statyczny o stałym rozmiarze, który jest używany do przechowywania wyniku konwersji. Jeśli wynik jest zbyt duży, aby zmieścił się w buforze statycznym, Klasa przydziela pamięć przy użyciu **malloc**, zwalniając pamięć, gdy obiekt wykracza poza zakres. Dzięki temu, w przeciwieństwie do makr konwersji tekstu dostępnych we wcześniejszych wersjach ATL, ta klasa jest bezpieczna do użycia w pętlach i nie przechodzą stosu.

Jeśli klasa próbuje przydzielić pamięć na stercie i kończy się niepowodzeniem, `AtlThrow` wywoła z argumentem E_OUTOFMEMORY.

Domyślnie klasy konwersji ATL i makra używają strony kodowej ANSI bieżącego wątku dla konwersji. Jeśli chcesz przesłonić to zachowanie dla określonej konwersji, określ stronę kodową jako drugi parametr konstruktora dla klasy.

Następujące makra są oparte na tej klasie:

- CT2AEX

- CW2TEX

- CW2CTEX

- CT2CAEX

Następujący element typedef jest oparty na tej klasie:

- CW2A

Aby zapoznać się z tymi makrami konwersji tekstu, zobacz [makra konwersji ATL i MFC String](string-conversion-macros.md).

## <a name="example"></a>Przykład

Zobacz [makra konwersji ciągów ATL i MFC,](string-conversion-macros.md) aby zapoznać się z przykładem użycia tych makr konwersji ciągów.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlconv. h

##  <a name="cw2aex"></a>CW2AEX::CW2AEX

Konstruktor.

```
CW2AEX(LPCWSTR psz, UINT nCodePage) throw(...);
CW2AEX(LPCWSTR psz) throw(...);
```

### <a name="parameters"></a>Parametry

*psz*<br/>
Ciąg tekstowy do przekonwertowania.

*nCodePage*<br/>
Strona kodowa użyta do przeprowadzenia konwersji. Aby uzyskać więcej informacji, zobacz Omówienie parametrów strony kodowej dla funkcji Windows SDK [MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar) .

### <a name="remarks"></a>Uwagi

Przypisuje bufor używany w procesie tłumaczenia.

##  <a name="dtor"></a>CW2AEX:: ~ CW2AEX

Destruktor.

```
~CW2AEX() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia przydzieloną bufor.

##  <a name="m_psz"></a>CW2AEX::m_psz

Element członkowski danych przechowujący ciąg źródłowy.

```
LPSTR m_psz;
```

##  <a name="m_szbuffer"></a>CW2AEX::m_szBuffer

Bufor statyczny używany do przechowywania przekonwertowanego ciągu.

```
char m_szBuffer[t_nBufferLength];
```

##  <a name="operator_lpstr"></a>CW2AEX:: operator LPSTR

Operator konwersji.

```
operator LPSTR() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca ciąg tekstowy jako typ LPSTR.

## <a name="see-also"></a>Zobacz także

[Klasa CA2AEX](../../atl/reference/ca2aex-class.md)<br/>
[Klasa CA2CAEX](../../atl/reference/ca2caex-class.md)<br/>
[Klasa CA2WEX](../../atl/reference/ca2wex-class.md)<br/>
[Klasa CW2CWEX](../../atl/reference/cw2cwex-class.md)<br/>
[Klasa CW2WEX](../../atl/reference/cw2wex-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
