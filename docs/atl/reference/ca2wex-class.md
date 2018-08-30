---
title: Klasa CA2WEX | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CA2WEX
- ATLCONV/ATL::CA2WEX
- ATLCONV/ATL::CA2WEX::CA2WEX
- ATLCONV/ATL::CA2WEX::m_psz
- ATLCONV/ATL::CA2WEX::m_szBuffer
dev_langs:
- C++
helpviewer_keywords:
- CA2WEX class
ms.assetid: 317d9ffb-e84f-47e8-beda-57e28fb19124
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 095d0d74fe5ff6eb30866b619e201a029b754d38
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43202179"
---
# <a name="ca2wex-class"></a>Klasa CA2WEX
Ta klasa jest używana przez makra konwersji ciągów CA2TEX, CA2CTEX, CT2WEX i CT2CWEX i typedef CA2W.  
  
> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template <int t_nBufferLength = 128>
class CA2WEX
```  
  
#### <a name="parameters"></a>Parametry  
 *t_nBufferLength*  
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
|[CA2WEX::m_psz](#m_psz)|Element członkowski danych, który przechowuje ciąg źródłowy.|  
|[CA2WEX::m_szBuffer](#m_szbuffer)|Bufor statyczne, używane do przechowywania przekonwertowany ciąg.|  
  
## <a name="remarks"></a>Uwagi  
 O ile nie jest wymagane dodatkowe funkcje, należy użyć CA2TEX, CA2CTEX, CT2WEX, CT2CWEX lub CA2W w kodzie.  
  
 Ta klasa zawiera buforu statyczne stałym rozmiarze, który jest używany do przechowywania wynik konwersji. Jeśli wynik jest za duży, aby mieściły się w statycznych buforu, klasa przydziela pamięć przy użyciu **— funkcja malloc**, zwalniając pamięć, gdy obiekt wykracza poza zakres. Dzięki temu, w przeciwieństwie do tekstu makra konwersji dostępne w poprzednich wersjach biblioteki ATL, ta klasa bezpiecznym rozwiązaniem jest użycie w pętli i że nie będzie to przepełnienia stosu.  
  
 Jeśli klasa próbuje przydzielić pamięci na stosie i kończy się niepowodzeniem, wywoła `AtlThrow` z nieprawidłowym argumentem E_OUTOFMEMORY.  
  
 Domyślnie klasy konwersji ATL i makra stronę kodową ANSI bieżącego wątku na użytek konwersji. Aby zastąpić to zachowanie dla określonej konwersji z wersji, należy określić strony kodowej jako drugi parametr do konstruktora dla klasy.  
  
 Następujące makra są oparte na tej klasy:  
  
- CA2TEX  
  
- CA2CTEX  
  
- CT2WEX  
  
- CT2CWEX  
  
 Następujący element typedef opiera się na tej klasy:  
  
- CA2W  
  
 Omówienie tych makr konwersji tekstu, zobacz [ATL i makr konwersji ciągu MFC](string-conversion-macros.md).  
  
## <a name="example"></a>Przykład  
 Zobacz [ATL i makr konwersji ciągu MFC](string-conversion-macros.md) na przykład używanie makr konwersji tych parametrów.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlconv.h  
  
##  <a name="ca2wex"></a>  CA2WEX::CA2WEX  
 Konstruktor.  
  
```
CA2WEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2WEX(LPCSTR psz) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 *psz*  
 Ciąg tekstowy, który ma zostać przekonwertowany.  
  
 *nCodePage*  
 Strona kodowa używany do wykonywania konwersji. Zobacz Omówienie kodu strony parametrów dla funkcji Windows SDK [MultiByteToWideChar](/windows/desktop/api/stringapiset/nf-stringapiset-multibytetowidechar) Aby uzyskać więcej informacji.  
  
### <a name="remarks"></a>Uwagi  
 Przydziela bufor używany w procesie tłumaczenia.  
  
##  <a name="dtor"></a>  CA2WEX:: ~ CA2WEX  
 Destruktor.  
  
```
~CA2WEX() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Zwalnia przydzielonego buforu.  
  
##  <a name="m_psz"></a>  CA2WEX::m_psz  
 Element członkowski danych, który przechowuje ciąg źródłowy.  
  
```
LPWSTR m_psz;
```  
  
##  <a name="m_szbuffer"></a>  CA2WEX::m_szBuffer  
 Bufor statyczne, używane do przechowywania przekonwertowany ciąg.  
  
```
wchar_t m_szBuffer[t_nBufferLength];
```  
  
##  <a name="operator_lpwstr"></a>  CA2WEX::operator LPWSTR  
 Operator konwersji.  
  
```  
operator LPWSTR() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca ciąg tekstowy, ponieważ typ LPWSTR.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CA2AEX](../../atl/reference/ca2aex-class.md)   
 [Klasa CA2CAEX](../../atl/reference/ca2caex-class.md)   
 [Klasa CW2AEX](../../atl/reference/cw2aex-class.md)   
 [Klasa CW2CWEX](../../atl/reference/cw2cwex-class.md)   
 [Klasa CW2WEX](../../atl/reference/cw2wex-class.md)   
 [Klasa — Przegląd](../../atl/atl-class-overview.md)
