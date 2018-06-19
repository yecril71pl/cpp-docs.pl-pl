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
ms.openlocfilehash: 62fd48a34b82e0671d417a882e040a87a7691c01
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32364001"
---
# <a name="cw2aex-class"></a>Klasa CW2AEX
Ta klasa jest używana przez makra konwersji ciągu `CT2AEX`, `CW2TEX`, `CW2CTEX`, i `CT2CAEX`i typedef **CW2A**.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template<int t_nBufferLength = 128>  
class CW2AEX
```  
  
#### <a name="parameters"></a>Parametry  
 `t_nBufferLength`  
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
|[CW2AEX::m_psz](#m_psz)|Element członkowski danych, która przechowuje ciąg źródłowy.|  
|[CW2AEX::m_szBuffer](#m_szbuffer)|Bufor statycznych, używany do przechowywania skonwertowany ciąg.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli wymagane jest dodatkowe funkcje, użyj `CT2AEX`, `CW2TEX`, `CW2CTEX`, `CT2CAEX`, lub **CW2A** w kodzie.  
  
 Ta klasa zawiera w buforze statycznych stałym rozmiarze, który jest używany do przechowywania wynik konwersji. Jeśli wynik jest za duży, aby mieścił się w buforze statycznych, klasa przydziela pamięć przy użyciu `malloc`, zwalnianie pamięci, gdy obiekt wykracza poza zakres. Dzięki temu, w przeciwieństwie do tekstu makra konwersji dostępne w poprzednich wersjach ATL, ta klasa jest bezpiecznie korzystać w pętli i że nie będzie przepełnienia stosu.  
  
 Jeśli klasa próbuje przydzielić pamięci na stercie i kończy się niepowodzeniem, zostanie wywołany `AtlThrow` z argumentem **E_OUTOFMEMORY**.  
  
 Domyślnie klasy konwersji ATL i makra do konwersji Użyj stronę kodową ANSI bieżącego wątku. Do zastąpienia tego zachowania dla określonej konwersji, należy określić strona kodowa jako drugiego parametru konstruktora dla klasy.  
  
 Następujące makra są oparte na tej klasy:  
  
- `CT2AEX`  
  
- `CW2TEX`  
  
- `CW2CTEX`  
  
- `CT2CAEX`  
  
 Następujący element typedef jest oparty na tej klasy:  
  
- **CW2A**  
  
 Aby uzyskać informacje dotyczące tych makr konwersji tekstu, zobacz [ATL i makr konwersji MFC ciąg](string-conversion-macros.md).  
  
## <a name="example"></a>Przykład  
 Zobacz [ATL i makr konwersji MFC ciąg](string-conversion-macros.md) przykład używanie makr konwersji te parametry.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlconv.h  
  
##  <a name="cw2aex"></a>  CW2AEX::CW2AEX  
 Konstruktor.  
  
```
CW2AEX(LPCWSTR psz, UINT nCodePage) throw(...);  
CW2AEX(LPCWSTR psz) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `psz`  
 Ciąg tekstowy, który ma zostać przekonwertowany.  
  
 `nCodePage`  
 Strona kodowa używane w celu wykonania konwersji. Zawiera omówienie kodu strony parametr dla funkcji Windows SDK [MultiByteToWideChar](http://msdn.microsoft.com/library/windows/desktop/dd319072) więcej szczegółów.  
  
### <a name="remarks"></a>Uwagi  
 Przydziela bufora używanego w procesie tłumaczenia.  
  
##  <a name="dtor"></a>  CW2AEX:: ~ CW2AEX  
 Destruktor.  
  
```
~CW2AEX() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Zwalnia przydzielonego buforu.  
  
##  <a name="m_psz"></a>  CW2AEX::m_psz  
 Element członkowski danych, która przechowuje ciąg źródłowy.  
  
```
LPSTR m_psz;
```  
  
##  <a name="m_szbuffer"></a>  CW2AEX::m_szBuffer  
 Bufor statycznych, używany do przechowywania skonwertowany ciąg.  
  
```
char m_szBuffer[t_nBufferLength];
```  
  
##  <a name="operator_lpstr"></a>  CW2AEX::operator LPSTR  
 Operator konwersji.  
  
```  
operator LPSTR() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca ciąg tekstowy jako typ **LPSTR.**  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CA2AEX](../../atl/reference/ca2aex-class.md)   
 [Klasa CA2CAEX](../../atl/reference/ca2caex-class.md)   
 [Klasa CA2WEX](../../atl/reference/ca2wex-class.md)   
 [Klasa CW2CWEX](../../atl/reference/cw2cwex-class.md)   
 [Klasa CW2WEX](../../atl/reference/cw2wex-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
