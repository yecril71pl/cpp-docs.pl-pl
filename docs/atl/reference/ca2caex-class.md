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
ms.openlocfilehash: 8aa16122a1cb3a5f8378397363a45cd28ddaef6d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32357805"
---
# <a name="ca2caex-class"></a>Klasa CA2CAEX
Ta klasa jest używana przez makra konwersji ciągu `CA2CTEX` i `CT2CAEX`i typedef **CA2CA**.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template<int t_nBufferLength = 128>  
class CA2CAEX
```  
  
#### <a name="parameters"></a>Parametry  
 `t_nBufferLength`  
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
|[CA2CAEX::m_psz](#m_psz)|Element członkowski danych, która przechowuje ciąg źródłowy.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli wymagane jest dodatkowe funkcje, użyj `CA2CTEX`, `CT2CAEX`, lub **CA2CA** w swoim własnym kodem.  
  
 Ta klasa jest bezpiecznie korzystać w pętli i nie będzie przepełnienia stosu. Domyślnie klasy konwersji ATL i makra użyje stronę kodową ANSI bieżącego wątku dla konwersji.  
  
 Następujące makra są oparte na tej klasy:  
  
- `CA2CTEX`  
  
- `CT2CAEX`  
  
 Następujący element typedef jest oparty na tej klasy:  
  
- **CA2CA**  
  
 Aby uzyskać informacje dotyczące tych makr konwersji tekstu, zobacz [ATL i makr konwersji MFC ciąg](string-conversion-macros.md).  
  
## <a name="example"></a>Przykład  
 Zobacz [ATL i makr konwersji MFC ciąg](string-conversion-macros.md) przykład używanie makr konwersji te parametry.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlconv.h  
  
##  <a name="ca2caex"></a>  CA2CAEX::CA2CAEX  
 Konstruktor.  
  
```
CA2CAEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2CAEX(LPCSTR psz) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `psz`  
 Ciąg tekstowy, który ma zostać przekonwertowany.  
  
 `nCodePage`  
 Nieużywane w tej klasie.  
  
### <a name="remarks"></a>Uwagi  
 Tworzy wymagane do tłumaczenia buforu.  
  
##  <a name="dtor"></a>  CA2CAEX:: ~ CA2CAEX  
 Destruktor.  
  
```
~CA2CAEX() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Zwalnia przydzielonego buforu.  
  
##  <a name="m_psz"></a>  CA2CAEX::m_psz  
 Element członkowski danych, która przechowuje ciąg źródłowy.  
  
```
LPCSTR m_psz;
```  
  
##  <a name="operator_lpcstr"></a>  CA2CAEX::operator LPCSTR  
 Operator konwersji.  
  
```  
operator LPCSTR() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca ciąg tekstowy jako typ `LPCSTR`.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CA2AEX](../../atl/reference/ca2aex-class.md)   
 [Klasa CA2WEX](../../atl/reference/ca2wex-class.md)   
 [Klasa CW2AEX](../../atl/reference/cw2aex-class.md)   
 [Klasa CW2CWEX](../../atl/reference/cw2cwex-class.md)   
 [Klasa CW2WEX](../../atl/reference/cw2wex-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
