---
title: Klasa CA2AEX | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CA2AEX
- ATLCONV/ATL::CA2AEX
- ATLCONV/ATL::CA2AEX::CA2AEX
- ATLCONV/ATL::CA2AEX::m_psz
- ATLCONV/ATL::CA2AEX::m_szBuffer
dev_langs: C++
helpviewer_keywords: CA2AEX class
ms.assetid: 57dc65df-d9cf-4a84-99d3-6e031dde3664
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ec54e698723b801823d58a3bad2a53e6f1708369
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ca2aex-class"></a>Klasa CA2AEX
Ta klasa jest używana przez makra konwersji ciągu `CA2TEX` i `CT2AEX`i typedef **CA2A**.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template <int t_nBufferLength = 128>
class CA2AEX
```  
  
#### <a name="parameters"></a>Parametry  
 `t_nBufferLength`  
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
|[CA2AEX::operator LPSTR](#operator_lpstr)|Operator konwersji.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CA2AEX::m_psz](#m_psz)|Element członkowski danych, która przechowuje ciąg źródłowy.|  
|[CA2AEX::m_szBuffer](#m_szbuffer)|Bufor statycznych, używany do przechowywania skonwertowany ciąg.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli wymagane jest dodatkowe funkcje, użyj `CA2TEX`, `CT2AEX`, lub **CA2A** w swoim własnym kodem.  
  
 Ta klasa zawiera w buforze statycznych stałym rozmiarze, który jest używany do przechowywania wynik konwersji. Jeśli wynik jest za duży, aby mieścił się w buforze statycznych, klasa przydziela pamięć przy użyciu `malloc`, zwalnianie pamięci, gdy obiekt wykracza poza zakres. Dzięki temu, w przeciwieństwie do tekstu makra konwersji dostępne w poprzednich wersjach ATL, ta klasa jest bezpiecznie korzystać w pętli i że nie będzie przepełnienia stosu.  
  
 Jeśli klasa próbuje przydzielić pamięci na stercie i kończy się niepowodzeniem, zostanie wywołany `AtlThrow` z argumentem **E_OUTOFMEMORY**.  
  
 Domyślnie klasy konwersji ATL i makra do konwersji Użyj stronę kodową ANSI bieżącego wątku.  
  
 Następujące makra są oparte na tej klasy:  
  
- `CA2TEX`  
  
- `CT2AEX`  
  
 Następujący element typedef jest oparty na tej klasy:  
  
- **CA2A**  
  
 Aby uzyskać informacje dotyczące tych makr konwersji tekstu, zobacz [ATL i makr konwersji MFC ciąg](string-conversion-macros.md).  
  
## <a name="example"></a>Przykład  
 Zobacz [ATL i makr konwersji MFC ciąg](string-conversion-macros.md) przykład używanie makr konwersji te parametry.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlconv.h  
  
##  <a name="ca2aex"></a>CA2AEX::CA2AEX  
 Konstruktor.  
  
```
CA2AEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2AEX(LPCSTR psz) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `psz`  
 Ciąg tekstowy, który ma zostać przekonwertowany.  
  
 `nCodePage`  
 Nieużywane w tej klasie.  
  
### <a name="remarks"></a>Uwagi  
 Tworzy wymagane do tłumaczenia buforu.  
  
##  <a name="dtor"></a>CA2AEX:: ~ CA2AEX  
 Destruktor.  
  
```
~CA2AEX() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Zwalnia przydzielonego buforu.  
  
##  <a name="m_psz"></a>CA2AEX::m_psz  
 Element członkowski danych, która przechowuje ciąg źródłowy.  
  
```
LPSTR m_psz;
```  
  
##  <a name="m_szbuffer"></a>CA2AEX::m_szBuffer  
 Bufor statycznych, używany do przechowywania skonwertowany ciąg.  
  
```
char m_szBuffer[ t_nBufferLength];
```  
  
##  <a name="operator_lpstr"></a>CA2AEX::operator LPSTR  
 Operator konwersji.  
  
```
operator LPSTR() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca ciąg tekstowy jako typ **LPSTR**.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CA2CAEX](../../atl/reference/ca2caex-class.md)   
 [Klasa CA2WEX](../../atl/reference/ca2wex-class.md)   
 [Klasa CW2AEX](../../atl/reference/cw2aex-class.md)   
 [Klasa CW2CWEX](../../atl/reference/cw2cwex-class.md)   
 [Klasa CW2WEX](../../atl/reference/cw2wex-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)