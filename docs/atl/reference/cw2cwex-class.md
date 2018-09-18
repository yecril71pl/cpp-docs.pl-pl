---
title: Klasa CW2CWEX | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CW2CWEX
- ATLCONV/ATL::CW2CWEX
- ATLCONV/ATL::CW2CWEX::CW2CWEX
- ATLCONV/ATL::CW2CWEX::m_psz
dev_langs:
- C++
helpviewer_keywords:
- CW2CWEX class
ms.assetid: d654b22b-05a6-410f-a0ec-9a2cbbb4cca7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3b45945a0f91570d78d8c1e365fd70240c2385b3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46116805"
---
# <a name="cw2cwex-class"></a>Klasa CW2CWEX

Ta klasa jest używana przez makra konwersji ciągów CW2CTEX i CT2CWEX i typedef CW2W.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
template<int t_nBufferLength = 128>
class CW2CWEX
```

#### <a name="parameters"></a>Parametry

*t_nBufferLength*<br/>
Rozmiar buforu używany w procesie tłumaczenia. Domyślna długość to 128 bajtów.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CW2CWEX::CW2CWEX](#cw2cwex)|Konstruktor.|
|[CW2CWEX:: ~ CW2CWEX](#dtor)|Destruktor.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CW2CWEX::operator LPCWSTR](#operator_lpcwstr)|Operator konwersji.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CW2CWEX::m_psz](#m_psz)|Element członkowski danych, który przechowuje ciąg źródłowy.|

## <a name="remarks"></a>Uwagi

O ile nie jest wymagane dodatkowe funkcje, należy użyć CW2CTEX, CT2CWEX lub CW2W w kodzie.

Ta klasa jest bezpiecznym rozwiązaniem jest użycie w pętli i nie będzie przepełnienia stosu. Domyślnie klasy konwersji ATL i makra stronę kodową ANSI bieżącego wątku na użytek konwersji.

Następujące makra są oparte na tej klasy:

- CW2CTEX

- CT2CWEX

Następujący element typedef opiera się na tej klasy:

- CW2W

Omówienie tych makr konwersji tekstu, zobacz [ATL i makr konwersji ciągu MFC](string-conversion-macros.md).

## <a name="example"></a>Przykład

Zobacz [ATL i makr konwersji ciągu MFC](string-conversion-macros.md) na przykład używanie makr konwersji tych parametrów.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlconv.h

##  <a name="cw2cwex"></a>  CW2CWEX::CW2CWEX

Konstruktor.

```
CW2CWEX(LPCWSTR psz, UINT nCodePage) throw(...);
CW2CWEX(LPCWSTR psz) throw(...);
```

### <a name="parameters"></a>Parametry

*psz*<br/>
Ciąg tekstowy, który ma zostać przekonwertowany.

*nCodePage*<br/>
Strona kodowa. Nie jest używany w tej klasie.

### <a name="remarks"></a>Uwagi

Przydziela bufor używany w procesie tłumaczenia.

##  <a name="dtor"></a>  CW2CWEX:: ~ CW2CWEX

Destruktor.

```
~CW2CWEX() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia przydzielonego buforu.

##  <a name="m_psz"></a>  CW2CWEX::m_psz

Element członkowski danych, który przechowuje ciąg źródłowy.

```
LPCWSTR m_psz;
```

##  <a name="operator_lpcwstr"></a>  CW2CWEX::operator LPCWSTR

Operator konwersji.

```
operator LPCWSTR() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca ciąg tekstowy jako typu LPCWSTR.

## <a name="see-also"></a>Zobacz też

[Klasa CA2AEX](../../atl/reference/ca2aex-class.md)<br/>
[Klasa CA2CAEX](../../atl/reference/ca2caex-class.md)<br/>
[Klasa CA2WEX](../../atl/reference/ca2wex-class.md)<br/>
[Klasa CW2AEX](../../atl/reference/cw2aex-class.md)<br/>
[Klasa CW2WEX](../../atl/reference/cw2wex-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
