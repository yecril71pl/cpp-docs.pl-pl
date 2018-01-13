---
title: Klasa CW2CWEX | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CW2CWEX
- ATLCONV/ATL::CW2CWEX
- ATLCONV/ATL::CW2CWEX::CW2CWEX
- ATLCONV/ATL::CW2CWEX::m_psz
dev_langs: C++
helpviewer_keywords: CW2CWEX class
ms.assetid: d654b22b-05a6-410f-a0ec-9a2cbbb4cca7
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a83f0fefed5e2393c303038346e3b84ec1a3d570
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cw2cwex-class"></a>Klasa CW2CWEX
Ta klasa jest używana przez makra konwersji ciągu `CW2CTEX` i `CT2CWEX`i typedef `CW2W`.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template<int t_nBufferLength = 128>  
class CW2CWEX
```  
  
#### <a name="parameters"></a>Parametry  
 `t_nBufferLength`  
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
|[CW2CWEX::m_psz](#m_psz)|Element członkowski danych, która przechowuje ciąg źródłowy.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli wymagane jest dodatkowe funkcje, użyj `CW2CTEX`, `CT2CWEX`, lub `CW2W` w kodzie.  
  
 Ta klasa jest bezpiecznie korzystać w pętli i nie będzie przepełnienia stosu. Domyślnie klasy konwersji ATL i makra do konwersji Użyj stronę kodową ANSI bieżącego wątku.  
  
 Następujące makra są oparte na tej klasy:  
  
- `CW2CTEX`  
  
- `CT2CWEX`  
  
 Następujący element typedef jest oparty na tej klasy:  
  
- `CW2W`  
  
 Aby uzyskać informacje dotyczące tych makr konwersji tekstu, zobacz [ATL i makr konwersji MFC ciąg](string-conversion-macros.md).  
  
## <a name="example"></a>Przykład  
 Zobacz [ATL i makr konwersji MFC ciąg](string-conversion-macros.md) przykład używanie makr konwersji te parametry.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlconv.h  
  
##  <a name="cw2cwex"></a>CW2CWEX::CW2CWEX  
 Konstruktor.  
  
```
CW2CWEX(LPCWSTR psz, UINT nCodePage) throw(...);  
CW2CWEX(LPCWSTR psz) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `psz`  
 Ciąg tekstowy, który ma zostać przekonwertowany.  
  
 `nCodePage`  
 Strona kodowa. Nie jest używany w tej klasie.  
  
### <a name="remarks"></a>Uwagi  
 Przydziela bufora używanego w procesie tłumaczenia.  
  
##  <a name="dtor"></a>CW2CWEX:: ~ CW2CWEX  
 Destruktor.  
  
```
~CW2CWEX() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Zwalnia przydzielonego buforu.  
  
##  <a name="m_psz"></a>CW2CWEX::m_psz  
 Element członkowski danych, która przechowuje ciąg źródłowy.  
  
```
LPCWSTR m_psz;
```  
  
##  <a name="operator_lpcwstr"></a>CW2CWEX::operator LPCWSTR  
 Operator konwersji.  
  
```  
operator LPCWSTR() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca ciąg tekstowy jako typ **LPCWSTR.**  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CA2AEX](../../atl/reference/ca2aex-class.md)   
 [Klasa CA2CAEX](../../atl/reference/ca2caex-class.md)   
 [Klasa CA2WEX](../../atl/reference/ca2wex-class.md)   
 [Klasa CW2AEX](../../atl/reference/cw2aex-class.md)   
 [Klasa CW2WEX](../../atl/reference/cw2wex-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
