---
title: Klasa CA2CAEX | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CA2CAEX
- ATLCONV/ATL::CA2CAEX
- ATLCONV/ATL::CA2CAEX::CA2CAEX
- ATLCONV/ATL::CA2CAEX::m_psz
dev_langs:
- C++
helpviewer_keywords:
- CA2CAEX class
ms.assetid: 388e7c1d-a144-474c-a182-b15f69a74bd8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4abf96e3850f88b58e138745536ffc40aef11b68
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024544"
---
# <a name="ca2caex-class"></a>Klasa CA2CAEX

Ta klasa jest używana przez makra konwersji ciągów CA2CTEX i CT2CAEX i typedef CA2CA.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
template<int t_nBufferLength = 128>
class CA2CAEX
```

#### <a name="parameters"></a>Parametry

*t_nBufferLength*<br/>
Rozmiar buforu używany w procesie tłumaczenia. Domyślna długość to 128 bajtów.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CA2CAEX::CA2CAEX](#ca2caex)|Konstruktor.|
|[CA2CAEX:: ~ CA2CAEX](#dtor)|Destruktor.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CA2CAEX::operator LPCSTR](#operator_lpcstr)|Operator konwersji.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CA2CAEX::m_psz](#m_psz)|Element członkowski danych, który przechowuje ciąg źródłowy.|

## <a name="remarks"></a>Uwagi

O ile nie jest wymagane dodatkowe funkcje, należy użyć CA2CTEX, CT2CAEX lub CA2CA we własnym kodzie.

Ta klasa jest bezpiecznym rozwiązaniem jest użycie w pętli i nie będzie przepełnienia stosu. Domyślnie klasy konwersji ATL i makra użyje stronę kodową ANSI bieżący wątek dla konwersji.

Następujące makra są oparte na tej klasy:

- CA2CTEX

- CT2CAEX

Następujący element typedef opiera się na tej klasy:

- CA2CA

Omówienie tych makr konwersji tekstu, zobacz [ATL i makr konwersji ciągu MFC](string-conversion-macros.md).

## <a name="example"></a>Przykład

Zobacz [ATL i makr konwersji ciągu MFC](string-conversion-macros.md) na przykład używanie makr konwersji tych parametrów.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlconv.h

##  <a name="ca2caex"></a>  CA2CAEX::CA2CAEX

Konstruktor.

```
CA2CAEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2CAEX(LPCSTR psz) throw(...);
```

### <a name="parameters"></a>Parametry

*psz*<br/>
Ciąg tekstowy, który ma zostać przekonwertowany.

*nCodePage*<br/>
Nieużywane w tej klasie.

### <a name="remarks"></a>Uwagi

Tworzy buforu wymagane do tłumaczenia.

##  <a name="dtor"></a>  CA2CAEX:: ~ CA2CAEX

Destruktor.

```
~CA2CAEX() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia przydzielonego buforu.

##  <a name="m_psz"></a>  CA2CAEX::m_psz

Element członkowski danych, który przechowuje ciąg źródłowy.

```
LPCSTR m_psz;
```

##  <a name="operator_lpcstr"></a>  CA2CAEX::operator LPCSTR

Operator konwersji.

```
operator LPCSTR() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca ciąg tekstowy jako typu LPCSTR.

## <a name="see-also"></a>Zobacz też

[Klasa CA2AEX](../../atl/reference/ca2aex-class.md)<br/>
[Klasa CA2WEX](../../atl/reference/ca2wex-class.md)<br/>
[Klasa CW2AEX](../../atl/reference/cw2aex-class.md)<br/>
[Klasa CW2CWEX](../../atl/reference/cw2cwex-class.md)<br/>
[Klasa CW2WEX](../../atl/reference/cw2wex-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
