---
title: Klasa CW2AEX | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CW2AEX
- ATLCONV/ATL::CW2AEX
- ATLCONV/ATL::CW2AEX::CW2AEX
- ATLCONV/ATL::CW2AEX::m_psz
- ATLCONV/ATL::CW2AEX::m_szBuffer
dev_langs:
- C++
helpviewer_keywords:
- CW2AEX class
ms.assetid: 44dc2cf5-dd30-440b-a9b9-b21b43f49843
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0e10650235298e7a5b2931e59c39cb21a5374d0b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46087594"
---
# <a name="cw2aex-class"></a>Klasa CW2AEX

Ta klasa jest używana przez makra konwersji ciągów CT2AEX, CW2TEX, CW2CTEX i CT2CAEX i typedef CW2A.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

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
|[CW2AEX:: ~ CW2AEX](#dtor)|Destruktor.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CW2AEX::operator LPSTR](#operator_lpstr)|Operator konwersji.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CW2AEX::m_psz](#m_psz)|Element członkowski danych, który przechowuje ciąg źródłowy.|
|[CW2AEX::m_szBuffer](#m_szbuffer)|Bufor statyczne, używane do przechowywania przekonwertowany ciąg.|

## <a name="remarks"></a>Uwagi

O ile nie jest wymagane dodatkowe funkcje, należy użyć CT2AEX, CW2TEX, CW2CTEX, CT2CAEX lub CW2A w kodzie.

Ta klasa zawiera buforu statyczne stałym rozmiarze, który jest używany do przechowywania wynik konwersji. Jeśli wynik jest za duży, aby mieściły się w statycznych buforu, klasa przydziela pamięć przy użyciu **— funkcja malloc**, zwalniając pamięć, gdy obiekt wykracza poza zakres. Dzięki temu, w przeciwieństwie do tekstu makra konwersji dostępne w poprzednich wersjach biblioteki ATL, ta klasa bezpiecznym rozwiązaniem jest użycie w pętli i że nie będzie to przepełnienia stosu.

Jeśli klasa próbuje przydzielić pamięci na stosie i kończy się niepowodzeniem, wywoła `AtlThrow` z nieprawidłowym argumentem E_OUTOFMEMORY.

Domyślnie klasy konwersji ATL i makra stronę kodową ANSI bieżącego wątku na użytek konwersji. Aby zastąpić to zachowanie dla określonej konwersji z wersji, należy określić strony kodowej jako drugi parametr do konstruktora dla klasy.

Następujące makra są oparte na tej klasy:

- CT2AEX

- CW2TEX

- CW2CTEX

- CT2CAEX

Następujący element typedef opiera się na tej klasy:

- CW2A

Omówienie tych makr konwersji tekstu, zobacz [ATL i makr konwersji ciągu MFC](string-conversion-macros.md).

## <a name="example"></a>Przykład

Zobacz [ATL i makr konwersji ciągu MFC](string-conversion-macros.md) na przykład używanie makr konwersji tych parametrów.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlconv.h

##  <a name="cw2aex"></a>  CW2AEX::CW2AEX

Konstruktor.

```
CW2AEX(LPCWSTR psz, UINT nCodePage) throw(...);
CW2AEX(LPCWSTR psz) throw(...);
```

### <a name="parameters"></a>Parametry

*psz*<br/>
Ciąg tekstowy, który ma zostać przekonwertowany.

*nCodePage*<br/>
Strona kodowa używany do wykonywania konwersji. Zobacz Omówienie kodu strony parametrów dla funkcji Windows SDK [MultiByteToWideChar](/windows/desktop/api/stringapiset/nf-stringapiset-multibytetowidechar) Aby uzyskać więcej informacji.

### <a name="remarks"></a>Uwagi

Przydziela bufor używany w procesie tłumaczenia.

##  <a name="dtor"></a>  CW2AEX:: ~ CW2AEX

Destruktor.

```
~CW2AEX() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia przydzielonego buforu.

##  <a name="m_psz"></a>  CW2AEX::m_psz

Element członkowski danych, który przechowuje ciąg źródłowy.

```
LPSTR m_psz;
```

##  <a name="m_szbuffer"></a>  CW2AEX::m_szBuffer

Bufor statyczne, używane do przechowywania przekonwertowany ciąg.

```
char m_szBuffer[t_nBufferLength];
```

##  <a name="operator_lpstr"></a>  CW2AEX::operator LPSTR

Operator konwersji.

```
operator LPSTR() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca ciąg tekstowy jako typu LPSTR.

## <a name="see-also"></a>Zobacz też

[Klasa CA2AEX](../../atl/reference/ca2aex-class.md)<br/>
[Klasa CA2CAEX](../../atl/reference/ca2caex-class.md)<br/>
[Klasa CA2WEX](../../atl/reference/ca2wex-class.md)<br/>
[Klasa CW2CWEX](../../atl/reference/cw2cwex-class.md)<br/>
[Klasa CW2WEX](../../atl/reference/cw2wex-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
