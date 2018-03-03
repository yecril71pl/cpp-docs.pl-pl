---
title: Klasa CW2WEX | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CW2WEX
- ATLCONV/ATL::CW2WEX
- ATLCONV/ATL::CW2WEX::CW2WEX
- ATLCONV/ATL::CW2WEX::m_psz
- ATLCONV/ATL::CW2WEX::m_szBuffer
dev_langs:
- C++
helpviewer_keywords:
- CW2WEX class
ms.assetid: 46262e56-e0d2-41fe-855b-0b67ecc8fcd7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c35439b1309e75359177cf45ade4c6be9459f623
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cw2wex-class"></a>Klasa CW2WEX
Ta klasa jest używana przez makra konwersji ciągu `CW2TEX` i `CT2WEX`i typedef `CW2W`.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template <int t_nBufferLength = 128>  
class CW2WEX
```  
  
#### <a name="parameters"></a>Parametry  
 `t_nBufferLength`  
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
|[CW2WEX::m_psz](#m_psz)|Element członkowski danych, która przechowuje ciąg źródłowy.|  
|[CW2WEX::m_szBuffer](#m_szbuffer)|Bufor statycznych, używany do przechowywania skonwertowany ciąg.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli wymagane jest dodatkowe funkcje, użyj `CW2TEX`, `CT2WEX`, lub `CW2W` w kodzie.  
  
 Ta klasa zawiera w buforze statycznych stałym rozmiarze, który jest używany do przechowywania wynik konwersji. Jeśli wynik jest za duży, aby mieścił się w buforze statycznych, klasa przydziela pamięć przy użyciu `malloc`, zwalnianie pamięci, gdy obiekt wykracza poza zakres. Dzięki temu, w przeciwieństwie do tekstu makra konwersji dostępne w poprzednich wersjach ATL, ta klasa jest bezpiecznie korzystać w pętli i że nie będzie przepełnienia stosu.  
  
 Jeśli klasa próbuje przydzielić pamięci na stercie i kończy się niepowodzeniem, zostanie wywołany `AtlThrow` z argumentem **E_OUTOFMEMORY**.  
  
 Domyślnie klasy konwersji ATL i makra do konwersji Użyj stronę kodową ANSI bieżącego wątku.  
  
 Następujące makra są oparte na tej klasy:  
  
- `CW2TEX`  
  
- `CT2WEX`  
  
 Następujący element typedef jest oparty na tej klasy:  
  
- `CW2W`  
  
 Aby uzyskać informacje dotyczące tych makr konwersji tekstu, zobacz [ATL i makr konwersji MFC ciąg](string-conversion-macros.md).  
  
## <a name="example"></a>Przykład  
 Zobacz [ATL i makr konwersji MFC ciąg](string-conversion-macros.md) przykład używanie makr konwersji te parametry.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlconv.h  
  
##  <a name="cw2wex"></a>CW2WEX::CW2WEX  
 Konstruktor.  
  
```
CW2WEX(LPCWSTR psz, UINT nCodePage) throw(...);
CW2WEX( LPCWSTR  psz) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `psz`  
 Ciąg tekstowy, który ma zostać przekonwertowany.  
  
 `nCodePage`  
 Strona kodowa. Nie jest używany w tej klasie.  
  
### <a name="remarks"></a>Uwagi  
 Tworzy wymagane do tłumaczenia buforu.  
  
##  <a name="dtor"></a>CW2WEX:: ~ CW2WEX  
 Destruktor.  
  
```
~CW2WEX() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Zwalnia przydzielonego buforu.  
  
##  <a name="m_psz"></a>CW2WEX::m_psz  
 Element członkowski danych, która przechowuje ciąg źródłowy.  
  
```
LPWSTR m_psz;
```  
  
##  <a name="m_szbuffer"></a>CW2WEX::m_szBuffer  
 Bufor statycznych, używany do przechowywania skonwertowany ciąg.  
  
```
wchar_t m_szBuffer[t_nBufferLength];
```  
  
##  <a name="operator_lpwstr"></a>CW2WEX::operator LPWSTR  
 Operator rzutowania.  
  
```  
operator LPWSTR() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca ciąg tekstowy jako typ `LPWSTR`.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CA2AEX](../../atl/reference/ca2aex-class.md)   
 [Klasa CA2CAEX](../../atl/reference/ca2caex-class.md)   
 [Klasa CA2WEX](../../atl/reference/ca2wex-class.md)   
 [Klasa CW2AEX](../../atl/reference/cw2aex-class.md)   
 [Klasa CW2CWEX](../../atl/reference/cw2cwex-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
