---
title: Klasa CA2WEX | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CA2WEX
- ATLCONV/ATL::CA2WEX
- ATLCONV/ATL::CA2WEX::CA2WEX
- ATLCONV/ATL::CA2WEX::m_psz
- ATLCONV/ATL::CA2WEX::m_szBuffer
dev_langs: C++
helpviewer_keywords: CA2WEX class
ms.assetid: 317d9ffb-e84f-47e8-beda-57e28fb19124
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0114d2ce60eba1d92b4cfd52d003532bd9ced097
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ca2wex-class"></a>Klasa CA2WEX
Ta klasa jest używana przez makra konwersji ciągu `CA2TEX`, `CA2CTEX`, `CT2WEX`, i `CT2CWEX`i typedef **CA2W**.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template <int t_nBufferLength = 128>
class CA2WEX
```  
  
#### <a name="parameters"></a>Parametry  
 `t_nBufferLength`  
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
|[CA2WEX::operator LPWSTR](#operator_lpwstr)|Operator konwersji.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CA2WEX::m_psz](#m_psz)|Element członkowski danych, która przechowuje ciąg źródłowy.|  
|[CA2WEX::m_szBuffer](#m_szbuffer)|Bufor statycznych, używany do przechowywania skonwertowany ciąg.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli wymagane jest dodatkowe funkcje, użyj `CA2TEX`, `CA2CTEX`, `CT2WEX`, `CT2CWEX`, lub **CA2W** w kodzie.  
  
 Ta klasa zawiera w buforze statycznych stałym rozmiarze, który jest używany do przechowywania wynik konwersji. Jeśli wynik jest za duży, aby mieścił się w buforze statycznych, klasa przydziela pamięć przy użyciu `malloc`, zwalnianie pamięci, gdy obiekt wykracza poza zakres. Dzięki temu, w przeciwieństwie do tekstu makra konwersji dostępne w poprzednich wersjach ATL, ta klasa jest bezpiecznie korzystać w pętli i że nie będzie przepełnienia stosu.  
  
 Jeśli klasa próbuje przydzielić pamięci na stercie i kończy się niepowodzeniem, zostanie wywołany `AtlThrow` z argumentem **E_OUTOFMEMORY**.  
  
 Domyślnie klasy konwersji ATL i makra do konwersji Użyj stronę kodową ANSI bieżącego wątku. Do zastąpienia tego zachowania dla określonej konwersji, należy określić strona kodowa jako drugiego parametru konstruktora dla klasy.  
  
 Następujące makra są oparte na tej klasy:  
  
- `CA2TEX`  
  
- `CA2CTEX`  
  
- `CT2WEX`  
  
- `CT2CWEX`  
  
 Następujący element typedef jest oparty na tej klasy:  
  
- **CA2W**  
  
 Aby uzyskać informacje dotyczące tych makr konwersji tekstu, zobacz [ATL i makr konwersji MFC ciąg](string-conversion-macros.md).  
  
## <a name="example"></a>Przykład  
 Zobacz [ATL i makr konwersji MFC ciąg](string-conversion-macros.md) przykład używanie makr konwersji te parametry.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlconv.h  
  
##  <a name="ca2wex"></a>CA2WEX::CA2WEX  
 Konstruktor.  
  
```
CA2WEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2WEX(LPCSTR psz) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `psz`  
 Ciąg tekstowy, który ma zostać przekonwertowany.  
  
 `nCodePage`  
 Strona kodowa używane w celu wykonania konwersji. Zawiera omówienie kodu strony parametr dla funkcji Windows SDK [MultiByteToWideChar](http://msdn.microsoft.com/library/windows/desktop/dd319072) więcej szczegółów.  
  
### <a name="remarks"></a>Uwagi  
 Przydziela bufora używanego w procesie tłumaczenia.  
  
##  <a name="dtor"></a>CA2WEX:: ~ CA2WEX  
 Destruktor.  
  
```
~CA2WEX() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Zwalnia przydzielonego buforu.  
  
##  <a name="m_psz"></a>CA2WEX::m_psz  
 Element członkowski danych, która przechowuje ciąg źródłowy.  
  
```
LPWSTR m_psz;
```  
  
##  <a name="m_szbuffer"></a>CA2WEX::m_szBuffer  
 Bufor statycznych, używany do przechowywania skonwertowany ciąg.  
  
```
wchar_t m_szBuffer[t_nBufferLength];
```  
  
##  <a name="operator_lpwstr"></a>CA2WEX::operator LPWSTR  
 Operator konwersji.  
  
```  
operator LPWSTR() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca ciąg tekstowy jako typ **LPWSTR.**  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CA2AEX](../../atl/reference/ca2aex-class.md)   
 [Klasa CA2CAEX](../../atl/reference/ca2caex-class.md)   
 [Klasa CW2AEX](../../atl/reference/cw2aex-class.md)   
 [Klasa CW2CWEX](../../atl/reference/cw2cwex-class.md)   
 [Klasa CW2WEX](../../atl/reference/cw2wex-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
