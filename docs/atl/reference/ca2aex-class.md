---
title: CA2AEX Class
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
ms.openlocfilehash: 712e663ab58e2c9de4e2f25090b84b35d0bced71
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57293826"
---
# <a name="ca2aex-class"></a>CA2AEX Class

Ta klasa jest używana przez makra konwersji ciągów CA2TEX i CT2AEX i typedef CA2A.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
template <int t_nBufferLength = 128>
class CA2AEX
```

#### <a name="parameters"></a>Parametry

*t_nBufferLength*<br/>
Rozmiar buforu używany w procesie tłumaczenia. Domyślna długość to 128 bajtów.

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
|[CA2AEX::m_szBuffer](#m_szbuffer)|Bufor statyczne, używane do przechowywania przekonwertowany ciąg.|

## <a name="remarks"></a>Uwagi

O ile nie jest wymagane dodatkowe funkcje, należy użyć CA2TEX, CT2AEX lub CA2A we własnym kodzie.

Ta klasa zawiera buforu statyczne stałym rozmiarze, który jest używany do przechowywania wynik konwersji. Jeśli wynik jest za duży, aby mieściły się w statycznych buforu, klasa przydziela pamięć przy użyciu **— funkcja malloc**, zwalniając pamięć, gdy obiekt wykracza poza zakres. Dzięki temu, w przeciwieństwie do tekstu makra konwersji dostępne w poprzednich wersjach biblioteki ATL, ta klasa bezpiecznym rozwiązaniem jest użycie w pętli i że nie będzie to przepełnienia stosu.

Jeśli klasa próbuje przydzielić pamięci na stosie i kończy się niepowodzeniem, wywoła `AtlThrow` z nieprawidłowym argumentem E_OUTOFMEMORY.

Domyślnie klasy konwersji ATL i makra stronę kodową ANSI bieżącego wątku na użytek konwersji.

Następujące makra są oparte na tej klasy:

- CA2TEX

- CT2AEX

Następujący element typedef opiera się na tej klasy:

- CA2A

Omówienie tych makr konwersji tekstu, zobacz [ATL i makr konwersji ciągu MFC](string-conversion-macros.md).

## <a name="example"></a>Przykład

Zobacz [ATL i makr konwersji ciągu MFC](string-conversion-macros.md) na przykład używanie makr konwersji tych parametrów.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlconv.h

##  <a name="ca2aex"></a>  CA2AEX::CA2AEX

Konstruktor.

```
CA2AEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2AEX(LPCSTR psz) throw(...);
```

### <a name="parameters"></a>Parametry

*psz*<br/>
Ciąg tekstowy, który ma zostać przekonwertowany.

*nCodePage*<br/>
Nieużywane w tej klasie.

### <a name="remarks"></a>Uwagi

Tworzy buforu wymagane do tłumaczenia.

##  <a name="dtor"></a>  CA2AEX:: ~ CA2AEX

Destruktor.

```
~CA2AEX() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia przydzielonego buforu.

##  <a name="m_psz"></a>  CA2AEX::m_psz

Element członkowski danych, który przechowuje ciąg źródłowy.

```
LPSTR m_psz;
```

##  <a name="m_szbuffer"></a>  CA2AEX::m_szBuffer

Bufor statyczne, używane do przechowywania przekonwertowany ciąg.

```
char m_szBuffer[ t_nBufferLength];
```

##  <a name="operator_lpstr"></a>  CA2AEX::operator LPSTR

Operator konwersji.

```
operator LPSTR() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca ciąg tekstowy jako typu LPSTR.

## <a name="see-also"></a>Zobacz także

[Klasa CA2CAEX](../../atl/reference/ca2caex-class.md)<br/>
[Klasa CA2WEX](../../atl/reference/ca2wex-class.md)<br/>
[Klasa CW2AEX](../../atl/reference/cw2aex-class.md)<br/>
[Klasa CW2CWEX](../../atl/reference/cw2cwex-class.md)<br/>
[Klasa CW2WEX](../../atl/reference/cw2wex-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
